# 👨‍⚖️ AI 法律代理团队

一个Streamlit应用程序，使用多个AI代理模拟全方位法律服务团队，分析法律文件并提供全面的法律见解。每个代理代表不同的法律专家角色，从研究和合同分析到战略规划，共同协作提供详尽的法律分析和建议。

## 功能特性

- **专业法律AI代理团队**
  - **法律研究员**：配备DuckDuckGo搜索工具，用于查找和引用相关法律案例和先例。提供详细的带来源的研究摘要，并引用上传文件中的特定章节。
  
  - **合同分析师**：专门从事彻底的合同审查，识别关键条款、义务和潜在问题。引用文件中的具体条款进行详细分析。
  
  - **法律战略师**：专注于制定全面的法律策略，提供可操作的建议，同时考虑风险和机遇。
  
  - **团队负责人**：协调团队成员之间的分析，确保全面的响应、正确来源的建议，并引用文件的特定部分。作为所有三个代理的代理团队协调员。

- **文件分析类型**
  - 合同审查 - 由合同分析师完成
  - 法律研究 - 由法律研究员完成
  - 风险评估 - 由法律战略师、合同分析师完成
  - 合规检查 - 由法律战略师、法律研究员、合同分析师完成
  - 自定义查询 - 由代理团队完成 - 法律研究员、法律战略师、合同分析师

## 如何运行

1. **环境设置**
   ```bash
   # 克隆仓库
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd advanced_ai_agents/multi_agent_apps/agent_teams/ai_legal_agent_team
   
   # 安装依赖
   pip install -r requirements.txt
   ```

2. **配置API密钥**
   - 从[OpenAI平台](https://platform.openai.com)获取OpenAI API密钥
   - 从[Qdrant云](https://cloud.qdrant.io)获取Qdrant API密钥和URL

3. **运行应用程序**
   ```bash
   streamlit run legal_agent_team.py
   ```
4. **使用界面**
   - 输入API凭证
   - 上传法律文件（PDF）
   - 选择分析类型
   - 如需要添加自定义查询
   - 查看分析结果

## 注意事项

- 仅支持PDF文件
- 使用GPT-4o进行分析
- 使用text-embedding-3-small进行嵌入
- 需要稳定的互联网连接
- 会产生API使用费用