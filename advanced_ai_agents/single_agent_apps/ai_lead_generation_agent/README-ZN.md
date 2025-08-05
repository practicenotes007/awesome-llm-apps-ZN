## 🎯 AI潜在客户生成代理 - 由Firecrawl的提取端点驱动

AI潜在客户生成代理自动化从Quora寻找和筛选潜在客户的过程。它使用Firecrawl的搜索和新的提取端点来识别相关的用户档案，提取有价值的信息，并将其组织成Google Sheets中的结构化格式。该代理帮助销售和营销团队高效地构建目标潜在客户列表，同时节省数小时的手动研究时间。

### 功能特性
- **目标搜索**：使用Firecrawl的搜索端点根据您的搜索条件查找相关的Quora URL
- **智能提取**：利用Firecrawl的新提取端点从Quora档案中提取用户信息
- **自动化处理**：将提取的用户信息格式化为干净、结构化的格式
- **Google Sheets集成**：自动创建Google Sheets并用潜在客户信息填充
- **可定制标准**：允许您定义特定的搜索参数，为您的利基市场找到理想潜在客户

### 如何开始
1. **克隆仓库**：
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd advanced_ai_agents/single_agent_apps/ai_lead_generation_agent
   ```
3. **安装所需包**：
   ```bash
   pip install -r requirements.txt
   ```
4. **在composio中的重要事项**：
    - 在终端中运行此命令：`composio add googlesheets`
    - 在您的composio仪表板中，创建一个新的Google Sheet集成，并确保它在活动集成/连接选项卡中处于活动状态

5. **设置您的API密钥**：
   - 从[Firecrawl网站](https://www.firecrawl.dev/app/api-keys)获取您的Firecrawl API密钥
   - 从[Composio网站](https://composio.ai)获取您的Composio API密钥
   - 从[OpenAI网站](https://platform.openai.com/api-keys)获取您的OpenAI API密钥

6. **运行应用程序**：
   ```bash
   streamlit run ai_lead_generation_agent.py
   ```