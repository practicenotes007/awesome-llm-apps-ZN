## 🎬 AI 电影制作代理
这个Streamlit应用程序是一个由AI驱动的电影制作助手，使用Claude 3.5 Sonnet模型帮助实现您的电影创意。它自动化了剧本写作和选角的过程，让您能够轻松创建引人入胜的电影概念。

### 功能特性
- 根据您的电影创意、类型和目标受众生成剧本大纲
- 为主角推荐合适的演员，考虑他们过去的表演和当前的可用性
- 提供简洁的电影概念概述

### 如何开始？

1. 克隆GitHub仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd advanced_ai_agents/single_agent_apps/ai_movie_production_agent
```
2. 安装所需依赖：

```bash
pip install -r requirements.txt
```
3. 获取您的Anthropic API密钥

- 注册[Anthropic账户](https://console.anthropic.com)（或您选择的LLM提供商）并获取您的API密钥。

4. 获取您的SerpAPI密钥

- 注册[SerpAPI账户](https://serpapi.com/)并获取您的API密钥。

5. 运行Streamlit应用程序
```bash
streamlit run movie_production_agent.py
```

### 工作原理？

AI电影制作代理利用三个主要组件：
- **剧本作家**：根据给定的电影创意和类型，开发引人入胜的剧本大纲，包含角色描述和关键情节点。
- **选角导演**：为主角推荐合适的演员，考虑他们过去的表演和当前的可用性。
- **电影制片人**：监督整个过程，协调剧本作家和选角导演之间的工作，并提供简洁的电影概念概述。