# 🌐 MCP工具集成

欢迎来到**模型上下文协议（MCP）**集成指南！本示例演示了如何通过标准化的MCP协议将您的ADK代理与外部数据源和工具连接。

## 🎯 您将学到什么

- **MCP基础**：理解模型上下文协议
- **ADK ↔ MCP集成**：使用`MCPToolset`连接到MCP服务器
- **外部工具访问**：利用来自MCP服务器的工具
- **服务器通信**：使用本地和远程MCP服务器
- **实际应用**：使用文件系统和维基百科的实际示例

## 🧠 核心概念：模型上下文协议

**模型上下文协议（MCP）**是一种开放标准，使AI代理能够：
- 一致地访问外部数据源
- 使用来自远程服务器的工具
- 与各种应用程序通信
- 在交互中保持上下文

### MCP如何与ADK协同工作

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│  ADK代理    │◄──►│ MCPToolset  │◄──►│ MCP服务器   │
│             │    │             │    │             │
│   Gemini    │    │   桥接      │    │   工具      │
└─────────────┘    └─────────────┘    └─────────────┘
```

**MCPToolset**充当桥梁，可以：
- 连接到MCP服务器（本地或远程）
- 自动发现可用工具
- 将MCP工具转换为ADK兼容格式
- 管理连接生命周期

## 🔧 集成模式

### 1. **使用外部MCP服务器**
连接到现有MCP服务器：
- **文件系统服务器**：文件操作
- **维基百科服务器**：知识检索
- **数据库服务器**：数据访问
- **API服务器**：外部服务集成

### 2. **通信协议**
- **服务器发送事件（SSE）**：远程服务器的实时通信
- **标准I/O**：本地进程通信的MCP服务器

## 🚀 本教程中的示例

### 📍 **示例1：文件系统代理**
**位置**：`./filesystem_agent/`
- 连接到文件系统MCP服务器
- 执行文件操作（读取、写入、列出）
- 处理本地文件系统交互
- 使用标准I/O通信

### 🔥 **示例2：Firecrawl代理**
**位置**：`./firecrawl_agent/`
- 连接到Firecrawl MCP服务器进行高级网页抓取
- 执行单页抓取、批处理和网站爬取
- 使用AI驱动的分析提取结构化数据
- 使用多源综合进行深度网络研究
- 使用与云API集成的标准I/O通信

## 📁 项目结构

```
4_4_mcp_tools/
├── README.md                    # 本文件 - MCP集成指南
├── requirements.txt             # MCP依赖项
├── filesystem_agent/            # 文件系统MCP集成
│   ├── __init__.py             # 包初始化
│   ├── agent.py                # 主代理实现
│   └── README.md               # 文件系统代理指南
├── firecrawl_agent/             # Firecrawl网页抓取集成
│   ├── __init__.py             # 包初始化
│   ├── agent.py                # 主代理实现
│   └── README.md               # Firecrawl代理指南
```

## 🎯 主要特性

- **无缝集成**：`MCPToolset`处理所有MCP协议细节
- **自动发现**：工具被自动发现并可用
- **多协议**：支持stdio和SSE通信
- **错误处理**：对网络和服务器问题的健壮错误管理
- **资源管理**：正确清理连接和资源

## 📋 先决条件

运行这些示例之前：

1. **安装依赖项**：
   ```bash
   pip install -r requirements.txt
   ```

2. **设置环境**：
   ```bash
   # 从根教程目录
   cp env.example .env
   # 编辑.env并添加您的Google AI API密钥
   ```

3. **Node.js用于MCP服务器**（用于社区服务器）：
   ```bash
   # 安装Node.js（如果尚未安装）
   # npm/npx基于的MCP服务器所需
   ```

## 🔄 工作原理

### 连接流程
1. 使用连接参数**初始化MCPToolset**
2. **建立连接**到MCP服务器
3. 通过MCP协议**发现工具**
4. **适配工具**为ADK格式
5. 在代理对话中**使用工具**
6. **清理**完成时的连接

### 代码示例
```python
from google.adk.agents import LlmAgent
from google.adk.tools.mcp_tool.mcp_toolset import MCPToolset, StdioServerParameters

# 为外部服务器创建MCP工具集
toolset = MCPToolset(
    connection_params=StdioServerParameters(
        command='npx',
        args=['-y', '@modelcontextprotocol/server-filesystem', '/path/to/folder']
    )
)

# 使用MCP工具创建代理
agent = LlmAgent(
    model='gemini-2.5-flash',
    name='mcp_agent',
    instruction='使用MCP工具帮助用户',
    tools=[toolset]
)
```

## 🚀 开始使用

### 快速开始
1. **选择一个示例**来探索：
   - **文件系统代理**：用于文件操作
   - **Firecrawl代理**：用于高级网页抓取和研究

2. **按照每个示例目录中的指南**操作

3. **使用ADK Web运行**：
   ```bash
   # 从根教程目录
   adk web
   ```

## 🔗 示例演练

### 文件系统代理示例
```python
# 连接到文件系统MCP服务器
toolset = MCPToolset(
    connection_params=StdioServerParameters(
        command='npx',
        args=['-y', '@modelcontextprotocol/server-filesystem', '/path/to/folder']
    )
)

# 要求代理使用文件系统工具
# "列出当前目录中的文件"
# "读取sample.txt的内容"
```

### Firecrawl代理示例
```python
# 连接到Firecrawl MCP服务器
toolset = MCPToolset(
    connection_params=StdioServerParameters(
        command='npx',
        args=['-y', 'firecrawl-mcp'],
        env={'FIRECRAWL_API_KEY': 'your_api_key'}
    )
)

# 要求代理使用网页抓取工具
# "抓取https://example.com的主页"
# "在https://blog.example.com上找到所有博客文章URL"
# "搜索最新的AI研究论文并提取摘要"
# "从此电商页面提取产品详情：[URL]"
```

## 💡 最佳实践

- **连接管理**：始终正确处理连接生命周期
- **错误处理**：为网络问题实现健壮的错误处理
- **资源清理**：为连接使用适当的清理模式
- **安全性**：适当验证输入和处理身份验证
- **性能**：考虑高吞吐量场景的连接池

## 🔍 故障排除

### 常见问题
- **连接错误**：检查服务器URL和网络连接
- **找不到工具**：验证服务器是否运行且工具已暴露
- **身份验证**：确保正确的API密钥和凭据
- **版本兼容性**：检查MCP协议版本兼容性

### 调试命令
```bash
# 测试MCP服务器连接
npx @modelcontextprotocol/inspector

# 检查ADK代理日志
adk web --debug
```

## 🔗 下一步

完成本教程后：
- **[教程4：记忆代理](../4_memory_agent/README.md)** - 添加记忆功能
- **[教程5：工作流代理](../5_workflow_agent/README.md)** - 多步骤流程
- **[教程6：多代理系统](../6_multi_agent_system/README.md)** - 代理协作

## 📚 附加资源

- **[MCP规范](https://modelcontextprotocol.io/docs/spec)** - 协议详情
- **[ADK MCP文档](https://google.github.io/adk-docs/tools/mcp-tools/)** - 集成指南
- **[社区MCP服务器](https://github.com/modelcontextprotocol/servers)** - 即用型服务器

## 🎯 实际应用

MCP工具支持：
- **知识检索**：访问维基百科、数据库、文档
- **文件操作**：读取、写入、管理文件和目录
- **API集成**：连接到外部服务和API
- **数据处理**：从各种来源转换和分析数据
- **自定义工具**：创建和共享跨代理的专用工具