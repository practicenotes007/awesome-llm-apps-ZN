# 🔥 Firecrawl代理 - 使用MCP的高级网页抓取

欢迎使用**Firecrawl MCP代理**！这个强大的代理演示了如何通过模型上下文协议（MCP）将Firecrawl的高级网页抓取功能与Google ADK集成。

## 🌟 您将学到什么

- **Firecrawl集成**：连接到Firecrawl的综合网页抓取平台
- **高级网页抓取**：单页抓取、批处理和完整网站爬取
- **AI驱动的提取**：使用LLM从网页内容中提取结构化数据
- **研究能力**：通过多源分析进行深度网络研究
- **实际应用**：数据提取和研究的实际示例

## 🚀 主要功能

### 🔧 综合工具集
- **单页抓取**：使用高级选项从单个URL提取内容
- **批处理**：高效地并行处理多个URL
- **网站映射**：发现网站上的所有URL以供探索
- **网络搜索**：搜索网络并从结果中提取内容
- **全站爬取**：执行具有深度控制的全面网站分析
- **结构化提取**：使用AI从页面中提取特定数据点
- **深度研究**：通过多源分析进行深入研究
- **LLMs.txt生成**：为域创建标准化的AI交互指南

### 🌍 高级功能
- **自动速率限制**：内置重试逻辑和退避策略
- **多种输出格式**：支持Markdown、HTML和JSON
- **内容过滤**：内容选择和排除的高级选项
- **移动/桌面渲染**：在不同渲染模式之间选择
- **身份验证支持**：处理需要登录凭据的站点
- **JavaScript渲染**：对动态内容的完全支持

## 📋 先决条件

### 所需依赖项
1. **Node.js**：Firecrawl MCP服务器所需
   ```bash
   # 如果尚未安装，请安装Node.js
   # 访问https://nodejs.org/获取安装说明
   ```

2. **Firecrawl API密钥**：从[Firecrawl.dev](https://firecrawl.dev)获取您的API密钥
   ```bash
   # 将您的API密钥设置为环境变量
   export FIRECRAWL_API_KEY=your_api_key_here
   ```

3. **Google ADK依赖项**：确保您拥有所需的包
   ```bash
   pip install -r ../requirements.txt
   ```

## 🛠️ 设置说明

### 1. 环境配置
```bash
# 设置您的Firecrawl API密钥
export FIRECRAWL_API_KEY=fc-your_api_key_here

# 可选：配置重试设置
export FIRECRAWL_RETRY_MAX_ATTEMPTS=5
export FIRECRAWL_RETRY_INITIAL_DELAY=2000
```

### 2. 安装依赖项
```bash
# 从教程根目录
pip install -r requirements.txt
```

### 3. 运行代理
```bash
# 从教程根目录
adk web
```

然后从下拉菜单中选择`firecrawl_mcp_agent`。

## 🎯 使用示例

### 基本网页抓取
```text
用户: "抓取https://example.com的主页"
代理: 使用firecrawl_scrape以Markdown格式提取干净内容
```

### 批量URL处理
```text
用户: "从这三篇文章中提取内容: [url1, url2, url3]"
代理: 使用firecrawl_batch_scrape进行高效的并行处理
```

### 网站发现
```text
用户: "在https://blog.example.com上找到所有博客文章URL"
代理: 使用firecrawl_map发现并列出所有可用URL
```

### 网络搜索和提取
```text
用户: "搜索过去4周内关于AI代理的研究论文并提取关键信息"
代理: 使用firecrawl_search查找相关论文并提取摘要
```

### 结构化数据提取
```text
用户: "从此电商页面提取产品详情（名称、价格、描述）"
代理: 使用带有自定义模式的firecrawl_extract进行结构化数据提取
```

### 深度研究
```text
用户: "对可持续能源技术进行全面研究"
代理: 使用firecrawl_deep_research进行多源分析和综合
```

### 网站爬取
```text
用户: "爬取https://docs.example.com的文档部分"
代理: 使用适当的深度和过滤器的firecrawl_crawl
```

## 🔧 可用工具

### 核心抓取工具
| 工具 | 用途 | 最佳场景 |
|------|------|----------|
| `firecrawl_scrape` | 单页提取 | 已知URL、特定页面 |
| `firecrawl_batch_scrape` | 多URL处理 | URL列表、并行提取 |
| `firecrawl_map` | URL发现 | 探索网站结构 |

### 高级工具
| 工具 | 用途 | 最佳场景 |
|------|------|----------|
| `firecrawl_search` | 网络搜索 | 查找相关内容 |
| `firecrawl_crawl` | 全站爬取 | 全面网站分析 |
| `firecrawl_extract` | 结构化数据提取 | 特定数据点 |
| `firecrawl_deep_research` | 多源研究 | 复杂研究任务 |

### 实用工具
| 工具 | 用途 | 最佳场景 |
|------|------|----------|
| `firecrawl_generate_llmstxt` | LLMs.txt生成 | AI交互指南 |
| `firecrawl_check_crawl_status` | 监控爬取进度 | 长时间运行的操作 |
| `firecrawl_check_batch_status` | 监控批处理进度 | 批处理操作跟踪 |

## 💡 最佳实践

### 工具选择指南
- **单个URL**：使用`firecrawl_scrape`
- **多个已知URL**：使用`firecrawl_batch_scrape`
- **发现URL**：首先使用`firecrawl_map`
- **网络搜索**：使用`firecrawl_search`
- **结构化数据**：使用`firecrawl_extract`
- **深度研究**：使用`firecrawl_deep_research`
- **全站分析**：使用`firecrawl_crawl`（带限制）

### 性能优化
- 对多个URL使用批处理操作而不是单独抓取
- 为爬取操作设置适当的限制以避免超时
- 使用状态检查工具监控长时间运行的操作
- 遵守速率限制并对目标网站保持尊重

### 内容质量
- 使用`onlyMainContent: true`提取干净内容
- 利用内容过滤选项以获得更好的结果
- 选择适当的输出格式（文本用Markdown，数据用JSON）
- 对特定数据需求使用结构化提取

## ⚙️ 配置选项

### 抓取参数
```python
# 抓取操作的示例配置
{
    "formats": ["markdown"],           # 输出格式
    "onlyMainContent": True,          # 仅提取主要内容
    "waitFor": 1000,                  # 页面加载等待时间
    "timeout": 30000,                 # 请求超时
    "mobile": False,                  # 使用移动渲染
    "includeTags": ["article", "main"], # 包含特定HTML标签
    "excludeTags": ["nav", "footer"]    # 排除特定HTML标签
}
```

### 批处理
```python
# 批处理配置示例
{
    "maxUrls": 50,                    # 要处理的最大URL数
    "parallelLimit": 5,               # 并行处理限制
    "options": {
        "formats": ["markdown"],
        "onlyMainContent": True
    }
}
```

### 爬取参数
```python
# 爬取配置示例
{
    "maxDepth": 2,                    # 爬取深度限制
    "limit": 100,                     # 要爬取的最大页面数
    "allowExternalLinks": False,      # 保持在域内
    "deduplicateSimilarURLs": True    # 删除重复内容
}
```

## 🚨 重要说明

### 速率限制
- Firecrawl包含自动速率限制和重试逻辑
- 批处理操作会被排队，可能需要时间完成
- 监控长时间运行任务的操作状态

### 资源管理
- 爬取操作可能资源密集
- 设置适当的限制以避免超时或过多的令牌使用
- 对大型操作使用批处理状态检查

### API使用
- 云操作需要有效的Firecrawl API密钥
- 考虑自托管部署以用于高容量使用
- 通过Firecrawl仪表板监控信用使用情况

## 🔍 故障排除

### 常见问题

**连接错误**
```bash
# 检查Node.js安装
node --version

# 测试Firecrawl MCP服务器
npx -y firecrawl-mcp
```

**API密钥问题**
```bash
# 验证API密钥是否设置
echo $FIRECRAWL_API_KEY

# 测试API密钥有效性
curl -H "Authorization: Bearer $FIRECRAWL_API_KEY" https://api.firecrawl.dev/v1/scrape
```

**找不到工具**
- 确保ADK MCP服务器配置正确
- 检查Node.js是否已安装且可访问
- 验证Firecrawl MCP包是否可以安装

### 调试命令
```bash
# 测试MCP服务器连接
npx @modelcontextprotocol/inspector

# 使用调试输出运行代理
adk web --debug
```

## 📚 附加资源

- **[Firecrawl文档](https://docs.firecrawl.dev)** - 完整的API参考
- **[Firecrawl MCP服务器](https://github.com/mendableai/firecrawl-mcp-server)** - 源代码和示例
- **[MCP规范](https://modelcontextprotocol.io/docs/spec)** - 协议详情
- **[ADK MCP文档](https://google.github.io/adk-docs/tools/mcp-tools/)** - 集成指南

## 🎯 实际应用

### 数据收集和研究
- 市场研究和竞争对手分析
- 学术研究和论文收集
- 新闻监控和趋势分析
- 产品目录提取
- 社交媒体内容分析

### 内容管理
- 网站迁移和内容审计
- SEO分析和优化
- 内容质量评估
- 文档提取
- 知识库创建

### 商业智能
- 潜在客户生成和联系信息提取
- 价格监控和比较
- 评论和情感分析
- 行业趋势跟踪
- 法规合规监控