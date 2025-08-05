# 6.1 代理生命周期回调

本教程演示如何使用`before_agent_callback`和`after_agent_callback`来监控代理执行生命周期。

## 🎯 学习目标

- 理解代理生命周期回调
- 学习如何监控代理执行时间
- 了解如何在回调之间共享状态
- 练习实现性能监控

## 📁 项目结构

```
6_1_agent_lifecycle_callbacks/
├── agent.py          # 带生命周期回调的代理
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

## 🧠 核心概念：代理生命周期监控

代理生命周期回调允许您监控代理执行的开始和结束，提供代理何时开始和完成任务的可见性。

### **代理生命周期流程**

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   用户输入      │───▶│  代理开始       │───▶│  代理结束       │
│                 │    │   回调          │    │   回调          │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                              │                       │
                              ▼                       ▼
                       ┌─────────────────┐    ┌─────────────────┐
                       │  代理逻辑       │    │  性能           │
                       │  执行           │    │  指标           │
                       └─────────────────┘    └─────────────────┘
```

### **回调执行时间线**

```
时间线: ──────────────────────────────────────────────────────────▶

用户消息
    │
    ▼
┌─────────────────┐
│ before_agent    │ ← 记录开始时间，代理信息
│ _callback       │
└─────────────────┘
    │
    ▼
┌─────────────────┐
│ 代理逻辑        │ ← 核心代理处理
│ 执行            │
└─────────────────┘
    │
    ▼
┌─────────────────┐
│ after_agent     │ ← 计算持续时间，记录完成
│ _callback       │
└─────────────────┘
    │
    ▼
响应用户
```

## 📖 代码演练

### **1. 回调函数**

回调成对工作以监控完整的代理生命周期：

**前置回调 (`before_agent_callback`)：**
- 记录执行开始时间戳
- 在会话状态中存储开始时间供后置回调使用
- 记录代理执行开始日志（代理名称、时间）
- 返回`None`以允许正常执行

**后置回调 (`after_agent_callback`)：**
- 从会话状态中检索开始时间
- 计算总执行持续时间
- 记录完成日志和性能指标
- 返回`None`以使用原始结果

### **2. 回调之间的状态管理**

```
会话状态流:
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│ before_callback │───▶│  会话状态       │───▶│ after_callback  │
│ 存储:           │    │                 │    │ 检索:           │
│ - start_time    │    │ - request_start │    │ - start_time    │
│                 │    │   _time         │    │                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

### **3. 代理设置**

代理配置了两个生命周期回调：
- `before_agent_callback`：监控代理执行开始
- `after_agent_callback`：监控代理执行完成
- 使用`InMemoryRunner`以正确触发回调

## 🧪 测试示例

### **示例输出格式**

```
🚀 代理LifecycleDemoAgent于19:15:30开始
⏰ 开始时间: 2024-01-15 19:15:30

✅ 代理LifecycleDemoAgent完成
⏱️ 持续时间: 1.23s
⏰ 结束时间: 2024-01-15 19:15:31
📊 性能: 1.23s | LifecycleDemoAgent

```

### **每个指标的含义**

- **🚀 开始时间**：代理开始处理的时间
- **✅ 完成时间**：代理完成处理的时间
- **⏱️ 持续时间**：总执行时间（秒）
- **📊 性能**：格式化的性能摘要

## 🔍 关键概念

### **代理生命周期监控**
- **执行开始**：跟踪代理何时开始处理
- **执行结束**：跟踪代理何时完成任务
- **性能计时**：计算总执行持续时间
- **状态共享**：在回调之间传递计时数据

### **CallbackContext**
- **agent_name**：正在执行的代理名称
- **invocation_id**：此执行的唯一标识符
- **state**：在回调之间持久化的会话状态

### **状态管理**
- 使用`callback_context.state.to_dict()`获取当前状态
- 使用`callback_context.state.update()`修改状态
- 状态在前置和后置回调之间共享

## 🎯 使用场景

- **性能监控**：跟踪执行时间
- **日志记录**：记录代理活动
- **分析**：收集使用统计信息
- **调试**：监控代理行为
- **自定义逻辑**：添加前置/后置处理

## 🚨 常见错误

1. **忘记等待会话创建：**
   ```python
   # ❌ 错误
   session_service.create_session(...)
   
   # ✅ 正确
   await session_service.create_session(...)
   ```

2. **使用错误的回调签名：**
   ```python
   # ❌ 错误
   def after_agent_callback(context, result):
   
   # ✅ 正确
   def after_agent_callback(callback_context: CallbackContext):
   ```

3. **不使用InMemoryRunner：**
   ```python
   # ❌ 错误 - 回调不会触发
   agent.run(message)
   
   # ✅ 正确
   runner.run_async(...)
   ```

## ⚠️ 关键实现说明

**事件循环完成**：如果您在收到`is_final_response()`后立即中断事件循环，`after_agent_callback`将不会触发。

**正确模式**：让事件循环自然完成：
```python
# ❌ 错误 - 过早中断循环，after_agent_callback不会运行
if event.is_final_response() and event.content:
    response_text = event.content.parts[0].text.strip()
    break  # 这会阻止after_agent_callback运行

# ✅ 正确 - 让循环自然完成
if event.is_final_response() and event.content:
    response_text = event.content.parts[0].text.strip()
    # 不要中断 - 让循环完成以确保回调运行
```

这是ADK的一个已知行为，过早中断循环会阻止清理回调执行。

## 🔗 下一步

- 尝试教程6.2：LLM交互回调
- 在回调之间尝试状态管理
- 添加自定义日志或分析
- 为慢响应实现性能警报