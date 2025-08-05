# 🧲 AI竞争对手情报代理团队

AI竞争对手情报代理团队是一个由Firecrawl和Agno的AI代理框架驱动的强大竞争对手分析工具。该应用通过从竞争对手网站提取结构化数据并使用AI生成可操作的见解，帮助企业管理竞争对手。

## 功能特性

- **多代理系统**
    - **Firecrawl代理**：专门用于爬取和总结竞争对手网站
    - **分析代理**：生成详细的竞争分析报告
    - **比较代理**：创建竞争对手之间的结构化比较

- **竞争对手发现**：
  - 使用Exa AI的URL匹配查找类似公司
  - 基于业务描述发现竞争对手
  - 自动提取相关竞争对手URL

- **全面分析**：
  - 提供结构化分析报告，包括：
    - 市场空白和机会
    - 竞争对手弱点
    - 推荐功能
    - 定价策略
    - 增长机会
    - 可操作的建议

- **交互式分析**：用户可以输入公司URL或描述进行分析

## 要求

该应用程序需要以下Python库：

- `agno`
- `exa-py`
- `streamlit`
- `pandas`
- `firecrawl-py`

您还需要以下API密钥：
- OpenAI
- Firecrawl
- Exa

## 如何运行

按照以下步骤设置和运行应用程序：

1. **克隆仓库**：
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd advanced_ai_agents/multi_agent_apps/agent_teams/ai_competitor_intelligence_agent_team
   ```

2. **安装依赖**：
    ```bash
    pip install -r requirements.txt
    ```

3. **设置您的API密钥**：
    - 从以下位置获取OpenAI API密钥：https://platform.openai.com/api-keys
    - 从以下位置获取Firecrawl API密钥：[Firecrawl网站](https://www.firecrawl.dev/app/api-keys)
    - 从以下位置获取Exa API密钥：[Exa网站](https://dashboard.exa.ai/api-keys)

4. **运行Streamlit应用**：
    ```bash
    streamlit run ai_competitor_analyser.py
    ```

## 使用方法

1. 在侧边栏输入您的API密钥
2. 输入以下任一项：
   - 您公司的网站URL
   - 您公司的描述
3. 点击"Analyze Competitors"生成：
   - 竞争对手比较表
   - 详细分析报告
   - 战略建议