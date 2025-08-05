# 6.2 LLM交互回调

本教程演示如何使用`before_model_callback`和`after_model_callback`来监控LLM请求和响应。

## 🎯 学习目标

- 理解LLM交互回调
- 学习如何监控LLM请求和响应
- 跟踪令牌使用和响应时间
- 估算API成本
- 监控LLM性能指标

## 📁 项目结构

```
6_2_llm_interaction_callbacks/
├── agent.py          # 带LLM交互回调的代理
├── app.py            # Streamlit Web界面
├── requirements.txt  # Python依赖项
└── README.md         # 本文件
```

## 🔧 设置

1. **安装依赖项：**
   ```bash
   pip install -r requirements.txt
   ```

2. **设置API密钥：**
   ```bash
   # 创建.env文件
   echo "GOOGLE_API_KEY=your_api_key_here" > .env
   ```

## 🚀 运行演示

### 命令行演示
```bash
python agent.py
```

### Web界面
```bash
streamlit run app.py
```

## 🧠 核心概念：LLM交互监控

LLM交互回调允许您监控代理与底层语言模型之间的通信，提供有关请求、响应和性能指标的洞察。

### **LLM交互流程**

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   用户输入      │───▶│  LLM请求        │───▶│  LLM响应        │
│                 │    │   回调          │    │   回调          │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                              │                       │
                              ▼                       ▼
                       ┌─────────────────┐    ┌─────────────────┐
                       │  模型API        │    │  令牌使用       │
                       │  (Gemini)       │    │  和性能         │
                       └─────────────────┘    └─────────────────┘
```

### **回调执行时间线**

```
时间线: ──────────────────────────────────────────────────────────▶

用户消息
    │
    ▼
┌─────────────────┐
│ before_model    │ ← 记录开始时间，模型信息
│ _callback       │
└─────────────────┘
    │
    ▼
┌─────────────────┐
│ LLM API调用     │ ← 实际请求到Gemini
│ (Gemini 2.5)    │
└─────────────────┘
    │
    ▼
┌─────────────────┐
│ after_model     │ ← 计算持续时间、令牌、成本
│ _callback       │
└─────────────────┘
    │
    ▼
响应用户
```

## 📖 代码演练

### **1. 回调函数**

回调成对工作以监控完整的LLM交互：

**前置回调 (`before_model_callback`)：**
- 从`llm_request`中提取模型信息
- 记录请求时间戳
- 在会话状态中存储数据供后置回调使用
- 记录请求详情（模型、时间、代理）

**后置回调 (`after_model_callback`)：**
- 从会话状态中检索存储的请求数据
- 计算响应持续时间
- 从`llm_response.usage_metadata`中提取令牌使用情况
- 基于令牌数量估算API成本
- 记录性能指标

### **2. 回调之间的状态管理**

```
会话状态流:
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│ before_callback │───▶│  会话状态       │───▶│ after_callback  │
│ 存储:           │    │                 │    │ 检索:           │
│ - start_time    │    │ - llm_request_  │    │ - start_time    │
│ - model         │    │   time          │    │ - model         │
│ - prompt_length │    │ - llm_model     │    │ - prompt_length │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

### **3. 代理设置**

代理配置了两个回调：
- `before_model_callback`：监控请求发起
- `after_model_callback`：监控响应完成
- 使用`InMemoryRunner`以正确触发回调

## 🧪 测试示例

### **示例输出格式**

```
🤖 LLM请求到gemini-2.5-flash
⏰ 请求时间: 19:15:30
📋 代理: llm_monitor_agent

📝 LLM响应来自gemini-2.5-flash
⏱️ 持续时间: 1.45s
🔢 令牌: 156
💰 估算成本: $0.0004

```

### **每个指标的含义**

- **⏰ 请求时间**：LLM请求发起的时间
- **⏱️ 持续时间**：从请求到响应的总时间
- **🔢 令牌**：消耗的总令牌数（输入+输出）
- **💰 估算成本**：基于令牌使用量的大致API成本

## 🔍 关键概念

### **LLM请求监控**
- **模型信息**：跟踪正在使用的模型
- **计时**：记录请求时间戳
- **状态管理**：存储请求数据以供响应分析

### **LLM响应监控**
- **响应时间**：计算从请求到响应的持续时间
- **令牌使用**：跟踪消耗的总令牌数
- **成本估算**：大致估算API成本

### **使用元数据**
- **令牌计数**：`llm_response.usage_metadata.total_token_count`
- **模型信息**：在请求和响应中可用
- **计时数据**：在回调之间存储在会话状态中

## 🎯 使用场景

- **性能监控**：跟踪LLM响应时间
- **成本管理**：监控API使用和成本
- **质量保证**：分析提示和响应模式
- **调试**：排查LLM交互问题
- **分析**：收集使用统计和指标

## 🚨 常见错误

1. **错误的回调签名：**
   ```python
   # ❌ 错误
   def before_model_callback(context, model, prompt):
   
   # ✅ 正确
   def before_model_callback(callback_context: CallbackContext, llm_request):
   ```

2. **错误的令牌提取：**
   ```python
   # ❌ 错误
   tokens = llm_response.usage_metadata.get('total_token_count')
   
   # ✅ 正确
   tokens = getattr(llm_response.usage_metadata, 'total_token_count', 0)
   ```

3. **不使用InMemoryRunner：**
   ```python
   # ❌ 错误 - 回调不会触发
   agent.run(message)
   
   # ✅ 正确
   runner.run_async(...)
   ```

## 🔗 下一步

- 尝试教程6.3：工具执行回调
- 尝试不同的成本估算模型
- 添加响应质量指标
- 实现速率限制和配额管理
- 创建自定义分析仪表板