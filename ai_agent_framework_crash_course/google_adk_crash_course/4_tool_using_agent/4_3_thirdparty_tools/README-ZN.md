# 🔗 第三方工具

第三方工具允许您集成来自LangChain、CrewAI等框架的**现有工具生态系统**。这通过利用更广泛的AI社区中经过实战检验的工具，极大地扩展了代理的功能。

## 🎯 您将学到什么

- **LangChain集成**：使用LangChain的广泛工具库
- **CrewAI工具**：利用CrewAI的专业代理工具
- **工具适配器**：ADK如何包装外部工具
- **生态系统优势**：使用成熟工具库的优势
- **最佳实践**：何时以及如何使用第三方工具

## 🧠 核心概念：第三方工具

第三方工具是**为ADK包装的外部库**：
- **LangChain工具**：网页抓取、文档加载器、API
- **CrewAI工具**：网页抓取、文件操作、专业函数
- **自定义集成**：任何外部服务或库
- **包装类**：ADK提供适配器以实现无缝集成

### 主要优势
- ✅ **丰富的生态系统**：访问数百个预构建工具
- ✅ **经过实战检验**：数千名开发人员使用的成熟工具
- ✅ **社区支持**：活跃的社区和文档
- ✅ **快速开发**：无需重新发明轮子

## 🔧 可用的第三方集成

### 1. **LangChain工具**
- **用途**：全面的工具生态系统
- **示例**：网页抓取、文件操作、API
- **优势**：成熟、文档齐全的工具

### 2. **CrewAI工具**
- **用途**：专业代理工具
- **示例**：网页抓取、文件操作、内容处理
- **优势**：为代理工作流优化

### 3. **自定义集成**
- **用途**：任何外部服务或库
- **示例**：数据库连接器、API客户端
- **优势**：无限的可扩展性

## 🚀 教程示例

此子示例包含两个实际实现：

### 📍 **LangChain代理**
**位置**：`./langchain_agent/`
- **网络搜索**：DuckDuckGo搜索集成用于实时信息
- **维基百科集成**：访问百科全书知识和文章
- **研究能力**：结合多个来源的综合研究
- **内容分析**：信息综合和来源引用

### 📍 **CrewAI代理**
**位置**：`./crewai_agent/`
- **网站操作**：网站内容搜索和抓取功能
- **文件系统工具**：目录搜索和文件读取操作
- **内容提取**：高级网页抓取和数据提取
- **文档处理**：本地文件分析和内容处理

## 📁 项目结构

```
4_3_thirdparty_tools/
├── README.md                    # 本文件 - 第三方工具指南
├── requirements.txt             # 第三方工具的依赖项
├── ../env.example              # 环境变量模板（共享）
├── langchain_agent/            # LangChain集成
│   ├── __init__.py
│   └── agent.py               # 带LangChain工具的代理
└── crewai_agent/               # CrewAI集成
    ├── __init__.py
    └── agent.py               # 带CrewAI工具的代理
```

## 🎯 学习目标

完成此子示例后，您将理解：
- ✅ 如何将LangChain工具与ADK集成
- ✅ 如何在ADK代理中使用CrewAI工具
- ✅ 第三方工具集成的最佳实践
- ✅ 何时选择第三方工具与自定义工具
- ✅ 如何处理工具兼容性问题

## 🔗 开始使用

1. **设置环境**：
   ```bash
   cd 4_3_thirdparty_tools
   
   # 复制环境模板
   cp ../env.example .env
   
   # 编辑.env并添加您的Google AI API密钥
   # 从以下网址获取API密钥：https://aistudio.google.com/
   ```

2. **安装依赖项**：安装所需包
   ```bash
   pip install -r requirements.txt
   ```

3. **运行代理**：
   ```bash
   # 启动ADK Web界面
   adk web
   
   # 在Web界面中，选择：
   # - langchain_agent: 用于网络搜索和维基百科研究
   # - crewai_agent: 用于网站抓取和文件操作
   ```

4. **尝试代理**：
   - **LangChain代理**："搜索最新AI新闻"，"告诉我关于机器学习的信息"
   - **CrewAI代理**："从example.com抓取内容"，"在当前目录中搜索Python文件"

5. **比较方法**：查看每种工具生态系统差异和优势

## 💡 专业提示

- **选择成熟工具**：使用维护良好的库
- **阅读文档**：了解工具限制和要求
- **处理依赖项**：仔细管理外部库版本
- **测试集成**：验证工具与ADK的兼容性
- **监控性能**：某些工具可能比自定义实现慢

## 🔧 集成模式

### 1. **LangChain工具包装器**
```python
from google.adk.tools.langchain_tool import LangchainTool
from langchain_community.tools import DuckDuckGoSearchRun

# 为ADK包装LangChain工具
search_tool = LangchainTool(DuckDuckGoSearchRun())
```

### 2. **CrewAI工具包装器**
```python
from google.adk.tools.crewai_tool import CrewaiTool
from crewai_tools import ScrapeWebsiteTool, DirectorySearchTool, FileReadTool

# 基本工具 - 最小配置
scrape_tool = CrewaiTool(
    name="scrape_website",
    description="抓取和提取网站内容",
    tool=ScrapeWebsiteTool(
        config=dict(
            llm=dict(
                provider="google",  # 使用Google而不是默认的OpenAI
                config=dict(model="gemini-2.5-flash"),
            ),
        )
    )
)

# 搜索工具 - 需要嵌入进行语义搜索
search_tool = CrewaiTool(
    name="website_search",
    description="在网站内搜索内容",
    tool=WebsiteSearchTool(
        config=dict(
            llm=dict(
                provider="google",
                config=dict(model="gemini-2.5-flash"),
            ),
            embedder=dict(
                provider="google",
                config=dict(
                    model="gemini-embedding-001",
                    task_type="retrieval_document",
                ),
            ),
        )
    )
)
```

### 3. **自定义集成模式**
```python
from google.adk.tools import FunctionTool
import external_library

def custom_integration(query: str) -> dict:
    """与外部库集成。"""
    result = external_library.process(query)
    return {"result": result, "status": "success"}

# 作为函数工具使用
tool = FunctionTool(custom_integration)
```

## 🔧 常见第三方工具

### LangChain工具
- **DuckDuckGoSearchRun**：网络搜索
- **WebBaseLoader**：网页抓取
- **WikipediaQueryRun**：维基百科搜索
- **PythonREPLTool**：Python代码执行
- **ShellTool**：Shell命令执行

### CrewAI工具
- **ScrapeWebsiteTool**：网页抓取和内容提取
- **DirectorySearchTool**：文件系统搜索和探索
- **FileReadTool**：文件读取和内容分析

### 自定义集成
- **数据库连接器**：SQLAlchemy、MongoDB
- **API客户端**：REST、GraphQL
- **文件处理器**：PDF、Excel、CSV
- **云服务**：AWS、GCP、Azure

## 🚨 重要注意事项

- **依赖项**：第三方工具添加外部依赖项
- **兼容性**：确保工具版本与ADK兼容
- **性能**：某些工具可能比自定义实现慢
- **维护**：外部工具可能会更改或被弃用
- **安全性**：验证外部工具的安全性和权限

### 🔧 **CrewAI模型配置**
⚠️ **重要**：CrewAI工具默认使用OpenAI模型。使用Google ADK时，配置它们使用Google模型以保持一致性：

```python
# ❌ 默认 - 使用OpenAI模型
tool = WebsiteSearchTool()

# ✅ 正确配置 - 所有工具都需要LLM和嵌入
tool = ScrapeWebsiteTool(
    config=dict(
        llm=dict(
            provider="google",
            config=dict(model="gemini-2.5-flash"),
        ),
        embedder=dict(
            provider="google",
            config=dict(
                model="gemini-embedding-001",
                task_type="retrieval_document",
            ),
        ),
    )
)

# ✅ 所有工具的相同配置模式
tool = DirectorySearchTool(
    config=dict(
        llm=dict(
            provider="google",
            config=dict(model="gemini-2.5-flash"),
        ),
        embedder=dict(
            provider="google",
            config=dict(
                model="gemini-embedding-001",
                task_type="retrieval_document",
            ),
        ),
    )
)
```

**关键点：**
- **LLM配置**：始终设置`provider="google"`以避免OpenAI默认值
- **嵌入**：所有CrewAI工具都需要以防止OpenAI回退
- **可用提供商**：`google`、`openai`、`anthropic`、`ollama`、`llama2`等

## 🔧 常见用例

### 网络和研究
- 网页抓取和内容提取
- 网站内容分析
- 文档处理
- 内容研究和分析

### 文件操作
- 文件系统搜索和探索
- 文件读取和内容分析
- 目录导航
- 本地文件处理

### 开发工具
- 代码执行
- 文档搜索
- 版本控制操作
- 测试工具

### 云和服务
- 云存储操作
- 电子邮件和消息
- 身份验证服务
- 监控和日志

## 📊 比较：第三方 vs 自定义 vs 内置

| 方面 | 第三方 | 自定义 | 内置 |
|------|--------|--------|------|
| **开发时间** | 快 | 慢 | 即时 |
| **灵活性** | 中等 | 高 | 低 |
| **性能** | 可变 | 高 | 最高 |
| **维护** | 外部 | 内部 | 无 |
| **功能** | 丰富 | 定制 | 基本 |
| **依赖项** | 多 | 少 | 无 |