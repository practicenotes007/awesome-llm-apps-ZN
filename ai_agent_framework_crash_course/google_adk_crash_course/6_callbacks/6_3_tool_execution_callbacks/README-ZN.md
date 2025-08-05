# 🎯 教程6.3：工具执行回调

## 🎯 您将学到什么
- **前置工具回调**：监控工具何时开始执行
- **后置工具回调**：跟踪工具完成和结果
- **工具上下文**：理解如何监控工具执行

## 🧠 核心概念：工具执行监控

工具执行回调允许您监控代理何时使用工具、跟踪其执行生命周期并分析结果。这提供了代理如何与外部系统和API交互的可见性。

### **工具执行流程**
```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   工具调用      │───▶│  前置工具       │───▶│  工具执行       │
│   (代理)        │    │   回调          │    │   (外部)        │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                              │                       │
                              ▼                       ▼
                       ┌─────────────────┐    ┌─────────────────┐
                       │  后置工具       │    │  工具结果       │
                       │   回调          │    │   (代理)        │
                       └─────────────────┘    └─────────────────┘
```

### **回调执行时间线**
```
时间 → 0ms    5ms    10ms   15ms   20ms   25ms
       │      │      │      │      │      │
       ▼      ▼      ▼      ▼      ▼      ▼
    [工具] [前置] [执行] [后置] [结果]
    调用   回调   开始   回调   返回
```

### **使用场景**
- **执行监控**：跟踪工具何时开始和完成
- **参数验证**：在执行前检查工具输入
- **结果记录**：记录工具输出和错误
- **调试**：理解工具执行模式
- **分析**：监控哪些工具使用最多

## 🚀 教程概述

在本教程中，我们将创建一个带有工具执行回调的代理，它可以：
- 使用简单的计算器工具
- 监控工具执行的开始和结束
- 跟踪工具参数和结果
- 提供详细的工具使用可见性

## 📁 项目结构

```
6_3_tool_execution_callbacks/
├── README.md              # 本文件
├── requirements.txt       # 依赖项
├── agent.py              # 带工具回调的代理
└── app.py                # Streamlit界面
```

## 🎯 学习目标

完成本教程后，您将理解：

- ✅ **前置工具回调**：如何监控工具执行开始
- ✅ **后置工具回调**：如何跟踪工具完成
- ✅ **工具上下文**：如何访问工具和代理信息
- ✅ **FunctionTool**：如何正确注册带回调的工具
- ✅ **回调集成**：如何将回调与代理集成

## 🚀 开始使用

### **设置**
1. **安装依赖项**：`pip install -r requirements.txt`
2. **设置环境**：创建包含`GOOGLE_API_KEY=your_key`的`.env`文件
3. **运行应用**：`streamlit run app.py`

### **测试代理**
```bash
# 运行Streamlit应用
streamlit run app.py

# 尝试这些测试消息：
- "计算15 + 27"
- "100除以4等于多少？"
- "8乘以12"
```

## 🔧 关键概念

### **1. 前置工具回调**
- **触发**：工具执行开始时
- **参数**：`tool`、`args`、`tool_context`
- **使用场景**：记录工具使用、验证参数、记录开始

### **2. 后置工具回调**
- **触发**：工具执行完成时
- **参数**：`tool`、`args`、`tool_context`、`tool_response`
- **使用场景**：记录结果、处理错误、提供反馈

### **3. 工具上下文**
- **代理信息**：访问`tool_context.agent_name`
- **代理信息**：访问`tool_context.agent_name`
- **状态管理**：使用`tool_context.state`进行数据共享
- **工具详情**：通过`tool.name`访问工具信息

## 🔍 测试示例

### **基本工具使用**
```
用户: "计算15 + 27"

🔧 工具calculator_tool开始
📝 参数: {'operation': 'add', 'a': 15.0, 'b': 27.0}
📋 代理: tool_execution_demo_agent

✅ 工具calculator_tool完成
⏱️ 持续时间: 0.0012s
📄 结果: 15 + 27 = 42
```

### **错误处理**
```
用户: "10除以0等于多少？"

🔧 工具calculator_tool开始
📝 参数: {'operation': 'divide', 'a': 10.0, 'b': 0.0}
📋 代理: tool_execution_demo_agent

✅ 工具calculator_tool完成
⏱️ 持续时间: 0.0008s
📄 结果: 错误: 除零错误
```

## 🎯 每个指标的含义

### **前置工具回调输出**
- **🔧 工具名称**：正在执行的工具
- **📝 参数**：传递给工具的输入参数
- **📋 代理**：使用工具的代理

### **后置工具回调输出**
- **✅ 完成状态**：工具执行成功完成
- **⏱️ 持续时间**：工具执行所需时间
- **📄 结果**：工具的输出或结果

## 🎯 关键实现说明

### **FunctionTool要求**
工具必须用`FunctionTool`包装才能使回调工作：

```python
# ✅ 正确 - 使用FunctionTool
calculator_function_tool = FunctionTool(func=calculator_tool)
agent = LlmAgent(tools=[calculator_function_tool], ...)

# ❌ 错误 - 原始函数不会触发回调
agent = LlmAgent(tools=[calculator_tool], ...)
```

### **回调签名**
使用正确的参数顺序进行工具回调：

```python
# ✅ 正确签名
def before_tool_callback(tool: BaseTool, args: dict, tool_context: ToolContext):
    pass

def after_tool_callback(tool: BaseTool, args: dict, tool_context: ToolContext, tool_response: any):
    pass
```

### **事件循环完成**
不要在`is_final_response()`后立即中断事件循环：

```python
# ✅ 这样做 - 允许回调完成
if event.is_final_response() and event.content:
    response_text = event.content.parts[0].text.strip()
    # 不要中断 - 让循环自然完成
```

## 🎯 高级模式

### **多个工具**
使用相同回调注册多个工具：

```python
def weather_tool(city: str) -> str:
    return f"{city}的天气: 晴天, 25°C"

def calculator_tool(operation: str, a: float, b: float) -> str:
    # ... 实现

# 注册多个工具
weather_function_tool = FunctionTool(func=weather_tool)
calculator_function_tool = FunctionTool(func=calculator_tool)

agent = LlmAgent(
    name="multi_tool_agent",
    model="gemini-2.5-flash",
    tools=[calculator_function_tool, weather_function_tool],
    before_tool_callback=before_tool_callback,
    after_tool_callback=after_tool_callback
)
```

### **参数验证**
在before_tool_callback中实现验证：

```python
def before_tool_callback(tool: BaseTool, args: dict, tool_context: ToolContext):
    tool_name = tool.name
    
    # 验证计算器工具参数
    if tool_name == "calculator_tool":
        if "operation" not in args:
            print("⚠️ 警告: 缺少操作参数")
        if "a" not in args or "b" not in args:
            print("⚠️ 警告: 缺少数值参数")
    
    print(f"🔧 工具 {tool_name} 开始")
    print(f"📝 参数: {args}")
    return None
```

### **结果修改**
在after_tool_callback中修改工具结果：

```python
def after_tool_callback(tool: BaseTool, args: dict, tool_context: ToolContext, tool_response: any):
    tool_name = tool.name
    
    # 为计算器结果添加上下文
    if tool_name == "calculator_tool" and "result" in tool_response:
        operation = args.get("operation", "unknown")
        tool_response["context"] = f"执行了 {operation} 操作"
    
    print(f"✅ 工具 {tool_name} 完成")
    print(f"📄 结果: {tool_response}")
    return tool_response  # 返回修改后的响应
```

## 🔗 下一步

完成本教程后，您可以继续：

- **[高级工具模式](../advanced_tool_patterns/README.md)** - 复杂工具架构
- **[自定义工具开发](../custom_tools/README.md)** - 构建自定义工具
- **[工具集成](../tool_integration/README.md)** - 集成外部API

## 📚 附加资源

- [Google ADK工具回调](https://google.github.io/adk-docs/callbacks/types-of-callbacks/#tool-execution-callbacks)
- [工具开发指南](https://google.github.io/adk-docs/tools/)
- [FunctionTool文档](https://google.github.io/adk-docs/tools/function-tools/)