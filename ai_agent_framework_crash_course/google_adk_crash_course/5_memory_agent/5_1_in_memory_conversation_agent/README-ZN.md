# 🧠 教程5.1：内存中对话代理

欢迎进入会话管理的第一步！本教程教您如何使用`InMemorySessionService`创建一个能够在单个会话中记住对话的AI代理。

## 🎯 您将学到什么

- **InMemorySessionService**：用于临时对话的基本会话管理
- **会话创建**：如何创建和管理对话会话
- **状态管理**：存储和检索对话上下文
- **事件跟踪**：记录对话历史
- **多轮对话**：构建能记住上下文的代理

## 🧠 核心概念：内存中会话

**InMemorySessionService**将会话数据存储在您计算机的RAM（内存）中。这意味着：
- ✅ **快速访问** - 无需数据库查询
- ✅ **简单设置** - 无需外部依赖
- ❌ **临时存储** - 程序停止时数据丢失
- ❌ **无持久性** - 无法在程序重启后记住

适用于：
- 开发和测试
- 临时对话
- 原型记忆功能
- 单会话应用程序

## 🔧 关键组件

### 1. **InMemorySessionService**
```python
from google.adk.sessions import InMemorySessionService
```

### 2. **会话生命周期**
```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   创建      │───▶│   使用      │───▶│   关闭      │
│  会话       │    │  会话       │    │  会话       │
└─────────────┘    └─────────────┘    └─────────────┘
```

### 3. **会话数据结构**
```python
{
    "session_id": "unique_session_id",
    "user_id": "user_identifier", 
    "state": {
        "conversation_history": [...],
        "user_preferences": {...},
        "current_context": "..."
    },
    "events": [
        {"type": "user_input", "content": "...", "timestamp": "..."},
        {"type": "agent_response", "content": "...", "timestamp": "..."}
    ]
}
```

## 🚀 教程概述

在本教程中，我们将创建一个**个人助理代理**，它可以：
- 记住您的姓名和偏好
- 跟踪对话历史
- 提供个性化响应
- 演示基本会话管理

## 📁 项目结构

```
5_1_in_memory_conversation/
├── README.md              # 本文件 - 概念解释
├── requirements.txt       # 依赖项
├── agent.py              # 带会话管理的主代理
└── app.py                # Streamlit Web界面
```

## 🎯 学习目标

完成本教程后，您将理解：
- ✅ 如何创建和管理会话
- ✅ 如何存储和检索对话状态
- ✅ 如何跟踪对话事件
- ✅ 如何构建多轮对话
- ✅ 基本会话生命周期管理

## 🚀 开始使用

1. **安装依赖项**：
   ```bash
   pip install -r requirements.txt
   ```

2. **设置环境**：
   ```bash
   # 使用您的Google AI API密钥创建.env文件
   echo "GOOGLE_API_KEY=your_api_key_here" > .env
   ```

3. **运行代理**：
   ```bash
   # 启动Streamlit应用
   streamlit run app.py
   ```

4. **测试记忆功能**：
   - 告诉代理您的姓名："我的名字是约翰"
   - 询问您的偏好："你知道我什么？"
   - 进行对话，看它如何记住上下文

## 🔍 代码演练

### 关键会话管理代码：

```python
# 1. 创建会话服务
session_service = InMemorySessionService()

# 2. 创建新会话
session = await session_service.create_session(
    app_name="personal_assistant",
    user_id="user123"
)

# 3. 更新会话状态
await session_service.update_session_state(
    session_id=session.session_id,
    state={"user_name": "John", "preferences": ["travel", "music"]}
)

# 4. 添加事件以跟踪对话
await session_service.add_event(
    session_id=session.session_id,
    event_type="user_input",
    content="My name is John"
)
```

## 🎯 测试您的代理

尝试这些对话流程来测试记忆功能：

### 流程1：个人信息
```
用户: "我的名字是爱丽丝"
代理: "很高兴认识你，爱丽丝！今天我能帮你什么？"

用户: "我的名字是什么？"
代理: "你的名字是爱丽丝！我记得你告诉过我。"
```

### 流程2：偏好
```
用户: "我喜欢披萨和徒步旅行"
代理: "太好了！我会记住你喜欢披萨和徒步旅行。"

用户: "我的兴趣是什么？"
代理: "根据我们的对话，你喜欢披萨和徒步旅行！"
```

### 流程3：上下文连续性
```
用户: "我正在计划一次旅行"
代理: "听起来很令人兴奋！既然你提到了徒步旅行，你想要徒步目的地的推荐吗？"

用户: "是的，我应该去哪里？"
代理: "鉴于你喜欢徒步旅行，我推荐..."
```

## 🔗 下一步

完成本教程后，您可以继续：
- **[教程5.2：持久化对话](../5_2_persistent_conversation/README.md)** - 学习基于数据库的会话存储
- **[教程5.3：云记忆](../5_3_cloud_memory/README.md)** - 探索基于云的记忆解决方案

## 💡 专业提示

- **测试多轮对话**：进行扩展对话以查看记忆功能的实际效果
- **监控会话状态**：使用Web界面检查代理记住了什么
- **尝试状态**：尝试在会话状态中存储不同类型的数据
- **理解限制**：记住内存中会话是临时的

## 🚨 重要说明

- **数据丢失**：内存中会话在您重启应用程序时会丢失
- **单进程**：会话仅在同一个Python进程中工作
- **内存使用**：大的对话历史将消耗RAM
- **仅限开发**：将内存中会话用于开发，而不是生产环境