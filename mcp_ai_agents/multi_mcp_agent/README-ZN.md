# 🚀 多MCP智能助手

多MCP智能助手是一个强大的生产力工具，它集成了多个模型上下文协议（MCP）服务器，通过自然语言交互为您提供对GitHub、Perplexity、日历和Gmail服务的无缝访问。这个先进的AI助手由Agno的AI代理框架驱动，旨在成为您数字工作空间中的生产力倍增器。

## 功能特性

- **多代理系统**
    - **GitHub集成**：完整的仓库管理、问题跟踪和代码分析
    - **Perplexity研究**：实时网络搜索和信息收集
    - **日历管理**：事件安排和会议协调
    - **Gmail集成**：邮件管理和通信工作流

- **核心功能**：
  - 仓库管理（创建、克隆、分叉、搜索）
  - 问题和PR工作流（创建、更新、审查、合并、评论）
  - 实时网络搜索和研究
  - 事件安排和可用性管理
  - 邮件组织和自动回复
  - 跨平台工作流自动化

- **高级功能**：
  - 带有流式响应的交互式CLI
  - 对话记忆和上下文保留
  - 复杂工作流的工具链
  - 会话特定的用户和会话ID
  - Markdown格式的响应
  - 主动式工作流建议

- **生产力焦点**：
  - 跨平台自动化（GitHub问题 → 日历事件）
  - 研究驱动的开发工作流
  - 项目管理集成
  - 文档和知识共享

## 运行方法

按照以下步骤设置和运行应用程序：

1. **克隆仓库**：
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd awesome-llm-apps/mcp_ai_agents/multi_mcp_agent
   ```

2. **安装依赖项**：
    ```bash
    pip install -r requirements.txt
    ```

3. **验证Node.js安装**（MCP服务器所需）：
    ```bash
    node --version
    npm --version
    npx --version
    ```
    如果未安装Node.js，请从[nodejs.org](https://nodejs.org/)下载

4. **设置您的API密钥**：
    在项目目录中创建一个`.env`文件，包含以下变量：
    ```env
    OPENAI_API_KEY=your-openai-api-key
    GITHUB_PERSONAL_ACCESS_TOKEN=your-github-token
    PERPLEXITY_API_KEY=your-perplexity-api-key
    ```

    - 从以下网址获取OpenAI API密钥：https://platform.openai.com/api-keys
    - 从以下网址获取GitHub个人访问令牌：https://github.com/settings/tokens（具有`repo`、`user`和`admin:org`范围）
    - 从以下网址获取Perplexity API密钥：https://www.perplexity.ai/
    - 根据您的设置要求配置OpenAI MCP标头

5. **运行多MCP代理**：
    ```bash
    python multi_mcp_agent.py
    ```

6. **开始交互**：
    - 助手将验证您的环境变量
    - 生成唯一的用户和会话ID
    - 初始化与所有MCP服务器的连接
    - 启动交互式CLI界面

## 使用方法

1. **环境验证**：助手会自动检查所有必需的API密钥和环境变量
2. **会话管理**：每个会话都会获得唯一的用户和会话ID用于跟踪和上下文
3. **交互式命令**：使用自然语言与集成服务交互：

### 示例命令

**GitHub操作**：
- "显示我最近的GitHub仓库"
- "在我的项目仓库中创建一个新问题"
- "在我的仓库中搜索Python代码"
- "审查最新的拉取请求"

**研究与信息**：
- "搜索最新的AI发展"
- "机器学习中的热门话题是什么？"
- "查找FastAPI的文档"
- "研究微服务的最佳实践"

**日历管理**：
- "为下周安排一个会议"
- "显示我即将到来的预约"
- "找到2小时会议的可用时间槽"

**跨平台工作流**：
- "创建一个GitHub问题并安排后续会议"
- "研究一个主题并创建摘要文档"
- "查找热门仓库并将其添加到我的关注列表"

4. **会话控制**：输入'exit'、'quit'或'bye'结束会话

## 架构

多MCP代理利用：
- **Agno框架**：用于代理编排和工具管理
- **OpenAI GPT-4o**：作为核心语言模型
- **MCP服务器**：用于外部服务集成
- **异步架构**：用于高效的并发操作
- **内存系统**：用于上下文保留和对话历史

## 注意事项

助手使用Node.js包连接到多个MCP服务器。请确保您有稳定的互联网连接和所有服务的有效API密钥。工具链功能允许跨多个平台的复杂工作流，使其成为开发人员和专业人士的强大生产力倍增器。