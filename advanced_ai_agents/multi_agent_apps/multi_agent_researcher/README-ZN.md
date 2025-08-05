## 📰 多代理AI研究员
这个Streamlit应用让您能够使用GPT-4o的AI助手团队研究HackerNews上的热门故事和用户。

### 功能特性
- 研究HackerNews上的热门故事和用户
- 利用专门从事故事和用户研究的AI助手团队
- 基于您的研究查询生成博客文章、报告和社交媒体内容

### 如何开始？

1. 克隆GitHub仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd advanced_ai_agents/multi_agent_apps/multi_agent_researcher
```
2. 安装所需依赖：

```bash
pip install -r requirements.txt
```
3. 获取您的OpenAI API密钥

- 注册[OpenAI账户](https://platform.openai.com/)（或您选择的LLM提供商）并获取您的API密钥。

4. 运行Streamlit应用
```bash
streamlit run research_agent.py
```

### 工作原理？

- 运行应用后，系统会提示您输入OpenAI API密钥。此密钥用于验证和访问OpenAI语言模型。
- 一旦您提供了有效的API密钥，将创建三个专业AI代理：
    - **HackerNews研究员**：专门使用HackerNews API获取热门故事。
    - **网络搜索员**：使用DuckDuckGo搜索主题的额外信息。
    - **文章阅读器**：使用newspaper4k工具读取和提取文章URL的内容。

- 这些代理在**HackerNews团队**的协调下作为一个协调团队工作，该团队编排研究过程。
- 在提供的文本输入字段中输入您的研究查询。这可以是与HackerNews故事或用户相关的主题、关键词或具体问题。
- HackerNews团队遵循结构化工作流程：
    1. 首先根据您的查询搜索HackerNews的相关故事
    2. 使用文章阅读器从故事URL中提取详细内容
    3. 利用网络搜索员收集额外的上下文和信息
    4. 最后提供一个深思熟虑且引人入胜的摘要，包含标题、摘要和参考链接
- 生成的内容结构为包含标题、摘要和参考链接的文章，便于查看和使用。