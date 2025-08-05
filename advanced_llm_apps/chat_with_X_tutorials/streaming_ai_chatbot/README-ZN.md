# 流式AI聊天机器人

一个使用Motia框架演示**实时AI流式传输**和**对话状态管理**的最小示例。
![streaming-ai-chatbot](docs/images/streaming-ai-chatbot.gif)

## 🚀 功能特性

- **实时AI流式传输**：使用OpenAI流式API逐令牌生成响应
- **实时状态管理**：实时更新对话状态和消息历史
- **事件驱动架构**：清晰的API → 事件 → 流式响应流程
- **最小复杂性**：仅需3个核心文件即可实现最大影响

## 📁 架构

```
streaming-ai-chatbot/
├── steps/
│   ├── conversation.stream.ts    # 实时对话状态
│   ├── chat-api.step.ts         # 简单聊天API端点  
│   └── ai-response.step.ts      # 流式AI响应处理器
├── package.json                 # 依赖项
├── .env.example                 # 配置模板
└── README.md                    # 本文件
```

## 🛠️ 设置

### 安装与设置

```bash
# 克隆仓库
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd advanced_llm_apps/chat_with_X_tutorials/chat_with_llms

# 安装依赖项
npm install

# 启动开发服务器
npm run dev
```

### 配置OpenAI API
   ```bash
   cp .env.example .env
   # 编辑.env并添加您的OpenAI API密钥
   ```

**打开Motia工作台**：
   导航到`http://localhost:3000`与聊天机器人交互

## 🔧 使用方法

### 发送聊天消息

**POST** `/chat`

```json
{
  "message": "Hello, how are you?",
  "conversationId": "optional-conversation-id"  // 可选：如果未提供，将创建新对话
}
```

**响应：**
```json
{
  "conversationId": "uuid-v4",
  "message": "消息已接收，AI正在响应...",
  "status": "streaming"
}
```

当AI处理消息时，响应将更新，可能的状态值包括：
- `created`：初始消息状态
- `streaming`：AI正在生成响应
- `completed`：响应完成并包含完整消息

完成后，响应将包含实际的AI消息而不是处理消息。

### 实时状态更新

对话状态流在AI生成响应时提供实时更新：

- **用户消息**：立即存储，状态为`status: 'completed'`
- **AI响应**：以`status: 'streaming'`开始，实时更新，以`status: 'completed'`结束

## 🎯 展示的关键概念

### 1. **流式API集成**
```typescript
const stream = await openai.chat.completions.create({
  model: 'gpt-4o-mini',
  messages: [...],
  stream: true, // 启用流式传输
})

for await (const chunk of stream) {
  // 使用每个令牌更新状态
  await streams.conversation.set(conversationId, messageId, {
    message: fullResponse,
    status: 'streaming',
    // ...
  })
}
```

### 2. **实时状态管理**
```typescript
export const config: StateStreamConfig = {
  name: 'conversation',
  schema: z.object({
    message: z.string(),
    from: z.enum(['user', 'assistant']),
    status: z.enum(['created', 'streaming', 'completed']),
    timestamp: z.string(),
  }),
  baseConfig: { storageType: 'state' },
}
```

### 3. **事件驱动流程**
```typescript
// API发出事件
await emit({
  topic: 'chat-message',
  data: { message, conversationId, assistantMessageId },
})

// 事件处理器订阅并处理
export const config: EventConfig = {
  subscribes: ['chat-message'],
  // ...
}
```

## 🌟 为什么这个示例很重要

这个示例展示了Motia在仅**3个文件**中的强大功能：

- **轻松流式传输**：具有自动状态更新的实时AI响应
- **类型安全事件**：从API到事件处理器的端到端类型安全
- **内置状态管理**：无需外部状态库
- **可扩展架构**：随着需求增长的事件驱动设计

完美展示了Motia如何使复杂的实时应用程序变得简单且易于维护。

## 🔑 环境变量

- `OPENAI_API_KEY`：您的OpenAI API密钥（必需）