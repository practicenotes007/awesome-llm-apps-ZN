## 📈 AI投资代理
这个Streamlit应用是一个使用Agno的AI代理框架构建的AI驱动投资代理，可以比较两只股票的表现并生成详细报告。通过使用GPT-4o和雅虎财经数据，该应用提供有价值的见解，帮助您做出明智的投资决策。

### 功能特性
- 比较两只股票的表现
- 获取全面的公司信息
- 获取最新的公司新闻和分析师建议

### 如何开始？

1. 克隆GitHub仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd advanced_ai_agents/single_agent_apps/ai_investment_agent
```
2. 安装所需依赖：

```bash
pip install -r requirements.txt
```
3. 获取您的OpenAI API密钥

- 注册[OpenAI账户](https://platform.openai.com/)（或您选择的LLM提供商）并获取您的API密钥。

4. 运行Streamlit应用
```bash
streamlit run investment_agent.py
```

### 工作原理？

- 运行应用后，系统会提示您输入OpenAI API密钥。此密钥用于验证和访问OpenAI语言模型。
- 一旦您提供了有效的API密钥，将创建一个Assistant类的实例。该助手利用OpenAI的GPT-4o语言模型和YFinanceTools访问股票数据。
- 在提供的文本输入字段中输入您想要比较的两家公司的股票代码。
- 助手将执行以下步骤：
    - 使用YFinanceTools获取实时股价和历史数据
    - 获取最新的公司新闻和分析师建议
    - 收集全面的公司信息
    - 使用GPT-4语言模型生成详细的比较报告
- 生成的报告将在应用中显示，为您提供有价值的见解和分析，以指导您的投资决策。