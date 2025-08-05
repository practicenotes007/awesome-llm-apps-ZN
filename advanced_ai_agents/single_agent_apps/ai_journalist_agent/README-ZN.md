## 🗞️ AI 记者代理
这个Streamlit应用程序是一个由AI驱动的记者代理，使用OpenAI GPT-4o生成高质量的文章。它自动化了研究、写作和编辑文章的过程，让您能够轻松地就任何主题创建引人入胜的内容。

### 功能特性
- 在网络上搜索给定主题的相关信息
- 编写结构良好、信息丰富且引人入胜的文章
- 编辑和优化生成的内容，以达到《纽约时报》的高标准

### 如何开始？

1. 克隆GitHub仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd advanced_ai_agents/single_agent_apps/ai_journalist_agent
```
2. 安装所需依赖：

```bash
pip install -r requirements.txt
```
3. 获取您的OpenAI API密钥

- 注册[OpenAI账户](https://platform.openai.com/)（或您选择的LLM提供商）并获取您的API密钥。

4. 获取您的SerpAPI密钥

- 注册[SerpAPI账户](https://serpapi.com/)并获取您的API密钥。

5. 运行Streamlit应用程序
```bash
streamlit run journalist_agent.py
```

### 工作原理？

AI记者代理利用三个主要组件：
- 搜索器：负责根据给定主题生成搜索词，并使用SerpAPI在网络上搜索相关URL。
- 作者：使用NewspaperToolkit从提供的URL中检索文本，并根据提取的信息编写高质量的文章。
- 编辑：协调搜索器和作者之间的工作流程，并对生成的文章进行最终编辑和优化。