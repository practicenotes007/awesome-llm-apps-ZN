# 企业级MCP AI代理团队

一个使用Google ADK构建的生产级多代理系统，通过MCP（模型上下文协议）在本地文件和SaaS平台之间编排知识管理。

## 概述

该系统结合了：
- **本地文件系统MCP服务器** - 用于访问和分析本地文档
- **Notion MCP服务器** - 用于管理Notion工作区和内容
- **Composio MCP服务器** - 用于GitHub和Figma集成
- **智能路由器/编排器** - 具有状态管理的上下文感知任务委派
- **4个专业AI代理** - 每个处理特定平台功能

## 架构

```
┌─────────────────────────────────────────────────────────────┐
│                企业级MCP AI代理团队                          │
│              (协调器/调度器模式)                             │
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────────┐  ┌─────────────────┐  ┌──────────────┐ │
│  │ 文件分析        │  │ Notion代理      │  │ GitHub代理   │ │
│  │ AI代理          │  │ (可选)          │  │ (可选)       │ │
│  └─────────────────┘  └─────────────────┘  └──────────────┘ │
│           │                     │                    │      │
│  ┌─────────────────┐  ┌─────────────────┐  ┌──────────────┐ │
│  │ 文件系统MCP     │  │ Notion MCP      │  │ Composio MCP │ │
│  │ 服务器          │  │ 服务器          │  │ 服务器       │ │
│  └─────────────────┘  └─────────────────┘  └──────────────┘ │
│           │                     │                    │      │
│  ┌─────────────────┐  ┌─────────────────┐  ┌──────────────┐ │
│  │ 本地文档        │  │ Notion页面与    │  │ GitHub仓库   │ │
│  │ (PDF, DOC, XLS) │  │ 数据库          │  │ 和问题       │ │
│  └─────────────────┘  └─────────────────┘  └──────────────┘ │
│                                                             │
│  ┌─────────────────┐  ┌─────────────────┐                   │
│  │ Figma代理       │  │ Composio MCP    │                   │
│  │ (可选)          │  │ 服务器          │                   │
│  └─────────────────┘  └─────────────────┘                   │
│           │                     │                           │
│  ┌─────────────────┐  ┌─────────────────┐                   │
│  │ Figma文件与     │  │ Figma设计与     │                   │
│  │ 设计            │  │ 资源            │                   │
│  └─────────────────┘  └─────────────────┘                   │
└─────────────────────────────────────────────────────────────┘
```

### **路由模式：**

1. **协调器/调度器模式**：基于查询分析的智能路由
2. **LLM驱动委派**：使用`transfer_to_agent()`自动代理选择
3. **显式调用**：使用`AgentTool`直接代理调用
4. **优雅降级**：系统在任何可用代理组合下都能工作

## 功能特性

### 🔍 文件分析代理
- 分析本地文档（PDF、Word文档、电子表格）
- 提取关键主题、摘要和行动项
- 按类型和内容对文档进行分类
- 识别用于知识库同步的信息

### 📝 Notion代理
- 读取、写入和更新Notion页面和数据库
- 在Notion工作区中搜索内容
- 创建结构化知识库和文档
- 将内容从其他来源同步到Notion

### 🐙 GitHub代理
- 创建和管理GitHub问题和拉取请求
- 搜索仓库和代码
- 管理仓库内容和文档
- 设置自动化工作流和操作

### 🎨 Figma代理
- 读取和分析Figma文件和设计
- 导出设计资源和组件
- 搜索设计元素和样式
- 管理设计系统组件

### 🎯 企业级MCP AI代理团队（路由器/编排器）
- 分析用户请求并确定哪个AI代理应该处理它们
- 根据能力将任务路由到适当的专门AI代理
- 协调需要多个AI代理的多步骤工作流
- 通过会话状态在AI代理之间共享上下文和结果
- 提供全面的结果和建议

### 🛡️ 错误处理和优雅降级
- **MCP服务器故障**：服务器不可用时的优雅回退
- **缺少环境变量**：系统仅使用可用API工作
- **代理创建失败**：继续使用可用代理
- **验证**：确保操作前至少有一个代理可用
- **全面日志记录**：详细的故障排除日志

## 先决条件

1. **Python 3.9+** 和 **Node.js**（用于MCP服务器）
2. **Google ADK** 已安装和配置
3. **Notion API密钥** 用于Notion集成
4. **环境变量中的必需API密钥**

## 设置

### 1. 环境变量

在项目根目录中创建一个`.env`文件：

```bash
# 必需：Google Gemini API
GOOGLE_API_KEY=your_gemini_api_key_here

# 必需：MCP工具的API密钥
NOTION_API_KEY=your_notion_api_key_here
GITHUB_API_KEY=your_github_api_key_here
FIGMA_API_KEY=your_figma_api_key_here

# 可选：自定义文件系统路径（默认为~/Documents）
MCP_FILESYSTEM_PATH=/Users/madhushantan/Downloads

```

### 2. Notion设置

#### 创建Notion集成
1. 访问[Notion集成](https://www.notion.so/my-integrations)
2. 点击"New integration"
3. 命名您的集成（例如，"Enterprise Knowledge Orchestrator"）
4. 选择所需功能（读取和写入内容）
5. 提交并复制您的"Internal Integration Token"

#### 与集成共享您的Notion页面
1. 打开您的Notion页面
2. 点击右上角的三个点（⋮）
3. 从下拉菜单中选择"Add connections"
4. 搜索您的集成名称
5. 点击您的集成以将其添加到页面
6. 点击"Confirm"确认

#### 查找您的Notion页面ID
1. 在浏览器中打开您的Notion页面
2. 复制URL：`https://www.notion.so/workspace/Your-Page-1f5b8a8ba283...`
3. ID是最后一个破折号后的部分：`1f5b8a8ba283`

### 3. Notion实现

系统使用SSE（Composio）进行Notion集成：

```python
# Notion MCP服务器（SSE - Composio）
url="https://mcp.composio.dev/composio/server/61e41019-d05f-44d0-973e-2aef7777063a/sse?useComposioHelperActions=true"
```

**功能：**
- **SSE连接**：使用服务器发送事件进行实时通信
- **Composio管理**：无需本地依赖
- **完整工具访问**：可访问所有可用的Notion工具
- **身份验证**：由Composio服务处理

**注意**：Notion集成需要有效的`NOTION_API_KEY`和`NOTION_PAGE_ID`才能正常工作。

### 4. GitHub和Figma实现

系统使用单独的SSE（Composio）服务器进行GitHub和Figma：

```python
# GitHub MCP服务器（SSE - Composio）
url="https://mcp.composio.dev/composio/server/11fbff47-fa12-432f-8c3a-18ed4e9f66f8/sse?useComposioHelperActions=true"

# Figma MCP服务器（SSE - Composio）  
url="https://mcp.composio.dev/composio/server/f05e7129-7997-4c17-a654-f935278c0dfe/sse?useComposioHelperActions=true"
```

**功能：**
- **独立服务器**：每个服务都有其专用的Composio服务器
- **完整工具访问**：可访问所有可用的GitHub和Figma工具
- **无本地依赖**：由Composio服务管理

### 2. 安装依赖

```bash
pip install -r requirements.txt
```

### 3. 验证MCP服务器安装

```bash
# 验证npx是否可用
which npx

# 测试文件系统MCP服务器
npx -y @modelcontextprotocol/server-filesystem --help

# 测试Notion MCP服务器
npx -y @notionhq/notion-mcp-server --help
```

## 使用方法

### 基本使用

```python
import asyncio
from agent import EnterpriseKnowledgeOrchestrator

async def main():
    # 创建编排器
    orchestrator = EnterpriseKnowledgeOrchestrator()
    
    try:
        # 处理知识请求
        results = await orchestrator.process_knowledge_request(
            "分析我文档文件夹中的所有PDF文档并为行动项创建GitHub问题"
        )
        
        # 访问结果
        print(f"分析的文件: {len(results['file_analysis'])}")
        print(f"Notion操作: {len(results['notion_operations'])}")
        print(f"GitHub操作: {len(results['github_operations'])}")
        print(f"Figma操作: {len(results['figma_operations'])}")
        
    finally:
        await orchestrator.close()

if __name__ == "__main__":
    asyncio.run(main())
```

### 示例请求

```python
# 文档分析
"分析我文档文件夹中的所有PDF文档并创建摘要"

# 多平台操作
"在我的Figma文件中搜索设计组件并为设计系统创建GitHub仓库"

# Notion和GitHub集成
"阅读我的Notion项目页面并为所有行动项创建GitHub问题"

# Figma资源管理
"从Figma导出设计资源并在结构化文件夹中组织它们"

# 复杂工作流
"分析季度报告，提取关键指标，创建Notion仪表板，并为后续行动设置GitHub问题"
```

## 代理路由逻辑

路由器/编排器代理基于查询分析智能路由任务：

- **文件相关任务** → FileAnalysisAgent
- **Notion相关任务** → NotionAgent  
- **GitHub相关任务** → GitHubAgent
- **Figma相关任务** → FigmaAgent
- **多平台任务** → 在相关代理之间协调

## 配置

### MCP服务器URL

系统使用这些MCP服务器：

```python
# 文件系统MCP服务器（本地）
command='npx'
args=["-y", "@modelcontextprotocol/server-filesystem", "~/Documents"]

# Notion MCP服务器（SSE - Composio）
url="https://mcp.composio.dev/composio/server/61e41019-d05f-44d0-973e-2aef7777063a/sse?useComposioHelperActions=true"

# GitHub MCP服务器（SSE - Composio）
url="https://mcp.composio.dev/composio/server/11fbff47-fa12-432f-8c3a-18ed4e9f66f8/sse?useComposioHelperActions=true"

# Figma MCP服务器（SSE - Composio）
url="https://mcp.composio.dev/composio/server/f05e7129-7997-4c17-a654-f935278c0dfe/sse?useComposioHelperActions=true"
# 无工具过滤 - 所有可用工具均可访问
```

### 自定义文件系统路径

系统现在支持通过环境变量配置文件系统路径：

```bash
# 在.env文件中设置或在终端中导出
export MCP_FILESYSTEM_PATH="/path/to/your/folder"

# 示例：
export MCP_FILESYSTEM_PATH="/Users/username/Projects"
export MCP_FILESYSTEM_PATH="/home/user/documents"
export MCP_FILESYSTEM_PATH="~/Desktop/Work"
```

**功能：**
- **灵活路径**：使用绝对或相对路径
- **自动扩展**：主目录的波浪号（~）扩展
- **自动创建**：目录不存在时自动创建
- **回退**：未指定时默认为`~/Documents`

## 输出模式

系统使用结构化Pydantic模型以确保一致的输出：

### FileAnalysis
```python
{
    "file_name": "quarterly_report.pdf",
    "file_type": "PDF",
    "summary": "Q3财务绩效分析...",
    "key_topics": ["收入", "支出", "增长"],
    "action_items": ["审查预算分配", "更新预测"]
}
```

### NotionOperation
```python
{
    "operation_type": "read",
    "page_id": "1f5b8a8ba283...",
    "content_summary": "从Notion读取的项目文档",
    "status": "completed",
    "results": {"content": "...", "blocks": [...]}
}
```

### GitHubOperation
```python
{
    "operation_type": "create_issue",
    "repository": "my-project",
    "content_summary": "为设计系统文档创建问题",
    "status": "completed",
    "results": {"issue_id": 123, "url": "..."}
}
```

### FigmaOperation
```python
{
    "operation_type": "export",
    "file_id": "figma_file_id",
    "content_summary": "从Figma导出的设计资源",
    "status": "completed",
    "results": {"assets": [...], "urls": [...]}
}
```

## 上下文共享

系统实现代理之间的智能上下文共享：

```python
# 会话状态包括共享上下文
"shared_context": {
    "current_task": user_request,
    "agent_results": {},
    "dependencies": []
}

# 代理可以访问和更新共享上下文
updated_session.state["shared_context"]["agent_results"]["file_analysis"] = file_results
```

## 错误处理

系统包含全面的错误处理：

- **MCP连接失败**：服务器不可用时的优雅回退
- **API速率限制**：具有指数退避的自动重试逻辑
- **无效数据**：输入的验证和清理
- **会话管理**：资源的正确清理

## 监控和日志记录

```python
import logging

# 配置日志级别
logging.basicConfig(level=logging.INFO)

# 监控代理活动
logger.info("文件分析完成: 处理了5个文档")
logger.warning("未找到Notion API密钥，Notion集成已禁用")
logger.error("创建GitHub问题失败: 超出速率限制")
```

## 生产部署

### 环境设置
```bash
# 生产环境变量
export GOOGLE_API_KEY="your_production_key"
export NOTION_API_KEY="your_production_key"
export LOG_LEVEL="INFO"
```

### 资源管理
```python
# 生产中的正确清理
async with EnterpriseKnowledgeOrchestrator() as orchestrator:
    results = await orchestrator.process_knowledge_request(request)
```

### 扩展考虑
- 对MCP服务器使用连接池
- 为频繁访问的文档实现缓存
- 考虑对大型文档集进行异步处理
- 使用大型文件操作监控内存使用情况

## 故障排除

### 常见问题

1. **MCP服务器连接失败**
   ```bash
   # 验证Node.js和npx安装
   node --version
   npx --version
   
   # 手动测试文件系统MCP服务器
   npx -y @modelcontextprotocol/server-filesystem /path/to/documents
   
   # 手动测试Notion MCP服务器
   npx -y @notionhq/notion-mcp-server
   ```

2. **Notion集成不工作**
   ```bash
   # 验证环境变量
   echo $NOTION_API_KEY
   
   # 测试Notion连接
   curl -H "Authorization: Bearer $NOTION_API_KEY" \
        -H "Notion-Version: 2022-06-28" \
        https://api.notion.com/v1/users/me
   ```

3. **Composio MCP服务器问题**
   ```bash
   # 测试Composio MCP服务器连接
   curl "https://mcp.composio.dev/composio/server/f05e7129-7997-4c17-a654-f935278c0dfe/sse?useComposioHelperActions=true"
   ```

4. **文档权限被拒绝**
   ```bash
   # 检查文件权限
   ls -la ~/Documents
   
   # 如需要更新权限
   chmod 755 ~/Documents
   ```

### 调试模式

```python
# 启用调试日志
logging.basicConfig(level=logging.DEBUG)

# 向代理添加调试信息
orchestrator = EnterpriseKnowledgeOrchestrator()
print(f"可用平台: {orchestrator.session_service.get_session(...).state['platforms_available']}")
```

## 贡献

1. Fork仓库
2. 创建功能分支
3. 为新功能添加测试
4. 确保所有测试通过
5. 提交拉取请求

## 许可证

本项目根据MIT许可证授权 - 有关详细信息请参阅LICENSE文件。

## 参考资料

- [Google ADK文档](https://google.github.io/adk-docs/)
- [MCP工具指南](https://google.github.io/adk-docs/tools/mcp-tools/)
- [Notion MCP服务器](https://github.com/notionhq/notion-mcp-server)
- [Composio MCP服务器](https://mcp.composio.dev/)
- [模型上下文协议](https://modelcontextprotocol.io/)