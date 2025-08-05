# 🚀 Google ADK 速成课程

一个全面的教程系列，从基础到高级概念学习 Google 的 Agent Development Kit (ADK)。这个速成课程旨在让您从零开始成为使用 Google ADK 构建 AI 代理的高手。

## 📚 什么是 Google ADK?

Google ADK (Agent Development Kit) 是一个用于**开发和部署 AI 代理**的灵活且模块化的框架。它针对 Gemini 和 Google 生态系统进行了优化，但**模型无关**且**部署无关**，使其与其他框架兼容。

### 主要特性：
- **灵活编排**：使用工作流代理或 LLM 驱动的动态路由定义工作流
- **多代理架构**：使用多个专业代理构建模块化应用程序
- **丰富的工具生态系统**：使用预构建工具、创建自定义函数或集成第三方库
- **部署就绪**：容器化并在任何地方部署代理
- **内置评估**：系统性地评估代理性能
- **安全性和保障**：为可信代理构建内置模式

## 🎯 学习路径

这个速成课程通过动手教程涵盖了 Google ADK 的基本概念：

### 📚 **教程**

1. **[1_starter_agent](./1_starter_agent/README.md)** - 您的第一个 ADK 代理
   - 基本代理创建
   - 理解 ADK 工作流
   - 简单文本处理

2. **[2_model_agnostic_agent](./2_model_agnostic_agent/README.md)** - 模型无关的代理开发
   - **[2.1 OpenAI Agent](./2_model_agnostic_agent/2_1_openai_adk_agent/README.md)** - OpenAI 集成
   - **[2.2 Anthropic Claude Agent](./2_model_agnostic_agent/2_2_anthropic_adk_agent/README.md)** - Claude 集成

3. **[3_structured_output_agent](./3_structured_output_agent/README.md)** - 类型安全的响应
   - **[3.1 Customer Support Ticket Agent](./3_structured_output_agent/3_1_customer_support_ticket_agent/README.md)** - Pydantic 模式
   - **[3.2 Email Agent](./3_structured_output_agent/3_2_email_agent/README.md)** - 结构化数据验证

4. **[4_tool_using_agent](./4_tool_using_agent/README.md)** - 带工具的代理
   - **[4.1 Built-in Tools](./4_tool_using_agent/4_1_builtin_tools/README.md)** - 搜索、代码执行
   - **[4.2 Function Tools](./4_tool_using_agent/4_2_function_tools/README.md)** - 自定义 Python 函数
   - **[4.3 Third-party Tools](./4_tool_using_agent/4_3_thirdparty_tools/README.md)** - LangChain、CrewAI
   - **[4.4 MCP Tools](./4_tool_using_agent/4_4_mcp_tools/README.md)** - MCP 工具集成

5. **[5_memory_agent](./5_memory_agent/README.md)** - 内存和会话管理
   - **[5.1 In-Memory Conversation](./5_memory_agent/5_1_in_memory_conversation/README.md)** - 基本会话管理
   - **[5.2 Persistent Conversation](./5_memory_agent/5_2_persistent_conversation/README.md)** - 使用 SQLite 的数据库存储

6. **[6_callbacks](./6_callbacks/README.md)** - 回调模式和监控
   - **[6.1 Agent Lifecycle Callbacks](./6_callbacks/6_1_agent_lifecycle_callbacks/README.md)** - 监控代理创建和清理
   - **[6.2 LLM Interaction Callbacks](./6_callbacks/6_2_llm_interaction_callbacks/README.md)** - 跟踪模型请求和响应
   - **[6.3 Tool Execution Callbacks](./6_callbacks/6_3_tool_execution_callbacks/README.md)** - 监控工具调用和结果

7. **更多教程即将推出！**

## 🛠️ 先决条件

在开始这个速成课程之前，请确保您具备：

- 安装了 **Python 3.11+**
- 来自 [Google AI Studio](https://aistudio.google.com/) 的 **Google AI API 密钥**
- 对 Python 和 API 的基本理解

## 📖 如何使用本课程

每个教程都遵循一致的结构：

- **README.md**：概念解释和学习目标
- **Python 文件**：包含代理实现和 Streamlit 应用
- **requirements.txt**：教程的依赖项

### 学习方法：
1. **阅读 README** 以理解概念
2. **检查代码** 以查看实现
3. **运行示例** 以查看实际效果
4. **实验** 通过修改代码
5. **准备好时进入下一个教程**

## 🎯 教程特性

每个教程包括：
- ✅ **清晰的概念解释**
- ✅ **最小的可工作代码示例**
- ✅ **真实世界的用例**
- ✅ **逐步指导**
- ✅ **最佳实践和技巧**

## 📚 附加资源

- [Google ADK 文档](https://google.github.io/adk-docs/)
- [Google AI Studio](https://aistudio.google.com/)
- [Gemini API 参考](https://ai.google.dev/docs)
- [Pydantic 文档](https://docs.pydantic.dev/)

## 🤝 贡献

欢迎贡献改进、错误修复或额外的教程。每个教程应该：
- 自包含且可运行
- 包含清晰的文档
- 遵循既定结构
- 使用最小且易于理解的代码