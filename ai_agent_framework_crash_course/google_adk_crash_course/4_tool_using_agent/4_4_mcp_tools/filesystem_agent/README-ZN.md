# 📁 文件系统代理 - MCP集成

本示例演示了如何使用`MCPToolset`将ADK代理连接到**文件系统MCP服务器**。代理可以通过模型上下文协议执行文件操作，如读取、写入和列出文件。

## 🎯 本示例展示的内容

- **MCP服务器连接**：连接到`@modelcontextprotocol/server-filesystem`
- **文件操作**：读取、写入、列出文件和目录
- **Stdio通信**：使用标准输入/输出进行本地MCP服务器通信
- **自动工具发现**：让ADK发现和使用可用的文件系统工具

## 🔧 工作原理

### MCP服务器设置
代理连接到提供以下工具的文件系统MCP服务器：
- `list_directory`：列出文件和文件夹
- `read_file`：读取文件内容
- `write_file`：将内容写入文件
- `create_directory`：创建新目录

### 连接流程
```python
MCPToolset(
    connection_params=StdioServerParameters(
        command='npx',
        args=['-y', '@modelcontextprotocol/server-filesystem', '/path/to/folder']
    )
)
```

## 🚀 开始使用

### 先决条件
1. **Node.js和npm**：文件系统MCP服务器所需
2. **ADK环境**：使用您的Google AI API密钥设置
3. **依赖项**：从`requirements.txt`安装

### 运行代理

1. **导航到教程根目录**：
   ```bash
   cd ai_agent_framework_crash_course/google_adk_tutorials/
   ```

2. **启动ADK Web**：
   ```bash
   adk web
   ```

3. **选择代理**：从下拉菜单中选择`filesystem_mcp_agent`

4. **测试命令**：
   - "列出当前目录中的文件"
   - "读取sample.txt的内容"
   - "创建一个名为hello.txt的新文件，内容为Hello World!"
   - "显示目录中的所有文本文件"

## 📝 示例对话

### 文件列表
```
用户: 列出当前目录中的文件
代理: 我将为您列出当前目录中的文件。
[使用list_directory工具]
找到以下文件:
- sample.txt
- hello.txt
```

### 文件读取
```
用户: 读取sample.txt的内容
代理: 我将为您读取sample.txt的内容。
[使用read_file工具]
文件包含:
这是MCP文件系统代理演示的示例文件。
您可以使用MCP工具读取、写入和列出文件。
```

### 文件写入
```
用户: 创建一个名为notes.txt的新文件，内容为"今天的会议记录"
代理: 我将创建文件notes.txt并写入您指定的内容。
[使用write_file工具]
已成功创建notes.txt，内容为"今天的会议记录"。
```

## 🔧 代码结构

### 代理定义
```python
root_agent = LlmAgent(
    model='gemini-2.5-flash',
    name='filesystem_mcp_agent',
    instruction="""
    您是一个有用的文件系统助手，可以帮助用户管理他们的文件。
    您可以通过模型上下文协议（MCP）访问文件系统工具。
    """,
    tools=[
        MCPToolset(
            connection_params=StdioServerParameters(
                command='npx',
                args=['-y', '@modelcontextprotocol/server-filesystem', DEMO_FOLDER]
            )
        )
    ]
)
```

### 演示环境
代理使用代理文件的父目录进行演示：
- **位置**：filesystem_agent文件夹的父目录
- **示例文件**：包含演示内容的`sample.txt`
- **工作目录**：MCP服务器可访问以进行安全操作

## 🛠️ 可用工具

文件系统MCP服务器自动提供以下工具：

| 工具 | 描述 | 参数 |
|------|------|------|
| `list_directory` | 列出文件和文件夹 | `path`（可选） |
| `read_file` | 读取文件内容 | `path`（必需） |
| `write_file` | 将内容写入文件 | `path`, `content` |
| `create_directory` | 创建新目录 | `path` |

## 🔍 高级用法

### 工具过滤
```python
MCPToolset(
    connection_params=StdioServerParameters(
        command='npx',
        args=['-y', '@modelcontextprotocol/server-filesystem', DEMO_FOLDER]
    ),
    tool_filter=['list_directory', 'read_file']  # 仅暴露特定工具
)
```

## 🚨 重要说明

- **安全性**：MCP服务器只能访问指定目录
- **需要Node.js**：文件系统服务器通过`npx`运行
- **工作目录**：使用父目录以便轻松访问项目文件
- **错误处理**：代理优雅地处理文件未找到和权限错误

## 🔍 故障排除

### 常见问题

1. **未找到Node.js**：
   ```bash
   # 安装Node.js
   # macOS: brew install node
   # Ubuntu: sudo apt install nodejs npm
   ```

2. **权限错误**：
   - 确保目录可写
   - 检查文件权限

3. **MCP服务器无法启动**：
   - 验证Node.js安装
   - 检查端口是否可用
   - 查看控制台日志

### 调试命令
```bash
# 直接测试MCP服务器
npx @modelcontextprotocol/server-filesystem /path/to/folder

# 使用调试日志运行
adk web --debug
```

## 🔗 下一步

尝试此示例后：
1. **自定义目录**：将`DEMO_FOLDER`更改为您的首选位置
2. **添加更多工具**：探索其他MCP服务器
3. **尝试服务器代理**：学习创建自定义MCP服务器
4. **与工作流集成**：与其他ADK功能结合

## 📚 相关文档

- **[ADK MCP工具](https://google.github.io/adk-docs/tools/mcp-tools/)** - 官方文档
- **[MCP文件系统服务器](https://github.com/modelcontextprotocol/servers/tree/main/src/filesystem)** - 服务器详情
- **[模型上下文协议](https://modelcontextprotocol.io/)** - 协议规范