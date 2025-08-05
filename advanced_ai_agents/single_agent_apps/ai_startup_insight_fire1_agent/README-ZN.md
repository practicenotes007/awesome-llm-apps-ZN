# 🔥 使用Firecrawl FIRE-1代理的AI初创公司洞察

一个使用Firecrawl的FIRE-1代理+extract v1端点和Agno代理框架构建的高级网络提取和分析工具，可立即获取新初创公司的详细信息！该应用程序自动从初创公司网站提取结构化数据并提供AI驱动的业务分析，让您无需手动研究即可轻松收集公司见解。

## 功能特性

- 🌐 **智能网络提取**：
  - 从任何公司网站提取结构化数据
  - 自动识别公司信息、使命和产品特性
  - 按顺序处理多个网站

- 🔍 **高级网络导航**：
  - 与按钮、链接和动态元素交互
  - 处理分页和多步骤过程
  - 访问多个页面的信息

- 🧠 **AI业务分析**：
  - 生成提取公司数据的洞察摘要
  - 识别独特的价值主张和市场机会
  - 提供可操作的商业智能

- 📊 **结构化数据输出**：
  - 以一致的JSON模式组织信息
  - 提取公司名称、描述、使命和产品特性
  - 标准化输出以供进一步处理

- 🎯 **交互式用户界面**：
  - 用户友好的Streamlit界面
  - 并行处理多个URL
  - 清晰展示提取的数据和分析

## 如何运行

1. **设置环境**

   ```bash
   # 克隆仓库

   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd advanced_ai_agents/single_agent_apps/ai_startup_insight_fire1_agent
   ```

   # 安装依赖


   ```
   pip install -r requirements.txt

   ```

2. **配置API密钥**

   - 从[Firecrawl](https://firecrawl.dev)获取Firecrawl API密钥
   - 从[OpenAI平台](https://platform.openai.com)获取OpenAI API密钥

3. **运行应用程序**

   ```bash
   streamlit run ai_startup_insight_fire1_agent.py
   ```

## 使用方法

1. 使用上述命令启动应用程序
2. 在侧边栏提供您的Firecrawl和OpenAI API密钥
3. 在文本区域输入一个或多个公司网站URL（每行一个）
4. 点击"🚀 Start Analysis"开始提取和分析过程
5. 在标签式界面中查看每个网站的结构化数据和AI分析

## 可尝试的示例网站

- https://www.spurtest.com
- https://cluely.com
- https://www.harvey.ai

## 使用的技术

- **Firecrawl FIRE-1**：高级网络提取代理
- **Agno代理框架**：用于AI分析功能
- **OpenAI GPT模型**：用于业务洞察生成
- **Streamlit**：用于交互式Web界面

## 要求

- Python 3.8+
- Firecrawl API密钥
- OpenAI API密钥
- 用于网络提取的互联网连接