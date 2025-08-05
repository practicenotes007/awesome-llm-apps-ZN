# 📋 教程6：回调函数

## 🎯 您将学到什么
- **代理生命周期回调**：监控代理创建、初始化和清理
- **LLM交互回调**：跟踪模型请求、响应和令牌使用
- **工具执行回调**：监控工具调用、参数和结果

## 💡 核心概念：回调函数

回调函数是在代理执行过程中特定点执行的函数，允许您在不修改核心逻辑的情况下监控、记录和控制代理的行为。

### **回调流程图**
```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   代理开始      │───▶│  LLM请求        │───▶│  工具执行       │
│   回调          │    │   回调          │    │   回调          │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  代理结束       │    │  LLM响应        │    │  工具结果       │
│  回调           │    │   回调          │    │   回调          │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

### **为什么使用回调？**
- **监控**：跟踪代理性能和行为
- **日志记录**：记录交互以进行调试和分析
- **控制**：根据特定事件修改行为
- **集成**：将代理连接到外部系统
- **调试**：了解代理内部发生的情况

## 📖 教程概述

本教程涵盖了Google ADK中的三种基本回调模式：

1. **代理生命周期回调**：监控代理创建、初始化和清理事件
2. **LLM交互回调**：跟踪模型请求、响应和令牌使用
3. **工具执行回调**：监控工具调用、参数和执行结果

每个子教程都提供了简单、集中的示例，演示特定的回调模式。

## 📁 项目结构

```
6_callbacks/
├── README.md                           # 本文件 - 概念解释
├── 6_1_agent_lifecycle_callbacks/      # 代理生命周期监控
│   ├── README.md                       # 生命周期回调模式
│   ├── agent.py                        # 带生命周期回调的代理
│   ├── app.py                          # Streamlit界面
│   └── requirements.txt                # 依赖项
├── 6_2_llm_interaction_callbacks/      # LLM请求/响应跟踪
│   ├── README.md                       # LLM回调模式
│   ├── agent.py                        # 带LLM回调的代理
│   ├── app.py                          # Streamlit界面
│   └── requirements.txt                # 依赖项
└── 6_3_tool_execution_callbacks/       # 工具执行监控
    ├── README.md                       # 工具回调模式
    ├── agent.py                        # 带工具回调的代理
    ├── app.py                          # Streamlit界面
    └── requirements.txt                # 依赖项
```

## 🎯 学习目标

完成本教程后，您将理解：

- ✅ **回调基础**：回调在Google ADK中如何工作
- ✅ **生命周期监控**：跟踪代理创建、初始化和清理
- ✅ **LLM跟踪**：监控模型请求、响应和性能
- ✅ **工具监控**：跟踪工具执行和结果
- ✅ **实际应用**：回调的实际用例
- ✅ **调试技术**：使用回调进行故障排除

## 🚀 开始使用

### **先决条件**
- Python 3.11+
- Google AI Studio API密钥
- Google ADK基础知识（教程1-5）

### **设置**
1. **获取API密钥**：访问[Google AI Studio](https://aistudio.google.com/)
2. **创建.env文件**：添加`GOOGLE_API_KEY=your_key_here`
3. **安装依赖项**：`pip install -r requirements.txt`

### **运行教程**
```bash
# 代理生命周期回调
cd 6_1_agent_lifecycle_callbacks
streamlit run app.py

# LLM交互回调  
cd ../6_2_llm_interaction_callbacks
streamlit run app.py

# 工具执行回调
cd ../6_3_tool_execution_callbacks
streamlit run app.py
```

## ⚙️ 回调模式

### **1. 代理生命周期回调**
```python
def on_agent_start(agent_name: str):
    print(f"▶️ 代理 {agent_name} 已启动")

def on_agent_end(agent_name: str, result: str):
    print(f"✅ 代理 {agent_name} 已完成: {result}")

# 注册回调
agent = LlmAgent(
    name="my_agent",
    model="gemini-2.5-flash",
    on_start=on_agent_start,
    on_end=on_agent_end
)
```

### **2. LLM交互回调**
```python
def on_llm_request(model: str, prompt: str):
    print(f"📤 LLM请求到 {model}: {prompt[:50]}...")

def on_llm_response(model: str, response: str, tokens: int):
    print(f"📥 LLM响应来自 {model}: {tokens} 个令牌")

# 注册回调
agent = LlmAgent(
    name="my_agent",
    model="gemini-2.5-flash",
    on_llm_request=on_llm_request,
    on_llm_response=on_llm_response
)
```

### **3. 工具执行回调**
```python
def on_tool_start(tool_name: str, params: dict):
    print(f"🔧 工具 {tool_name} 已启动，参数: {params}")

def on_tool_end(tool_name: str, result: str):
    print(f"✅ 工具 {tool_name} 已完成: {result}")

# 注册回调
agent = LlmAgent(
    name="my_agent",
    model="gemini-2.5-flash",
    tools=[my_tool],
    on_tool_start=on_tool_start,
    on_tool_end=on_tool_end
)
```

## 📊 使用场景

### **监控和分析**
- 跟踪代理性能指标
- 监控令牌使用和成本
- 分析工具使用模式
- 调试代理行为

### **日志记录和调试**
- 记录所有代理交互
- 调试工具执行问题
- 监控LLM响应质量
- 跟踪错误模式

### **集成和控制**
- 连接到外部监控系统
- 实现自定义错误处理
- 添加身份验证和验证
- 动态控制代理行为

## 🔗 下一步

完成本教程后，您可以继续：

- **[高级代理模式](../advanced_patterns/README.md)** - 复杂代理架构
- **[生产部署](../deployment/README.md)** - 将代理部署到生产环境
- **[自定义工具](../custom_tools/README.md)** - 构建自定义工具和集成

## 📚 附加资源

- [Google ADK文档](https://google.github.io/adk-docs/)
- [回调API参考](https://google.github.io/adk-docs/api-reference/python/)
- [最佳实践指南](https://google.github.io/adk-docs/best-practices/)