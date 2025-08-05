## 📝 AI会议准备代理
这个Streamlit应用程序利用多个AI代理创建全面的会议准备材料。它使用OpenAI的GPT-4、Anthropic的Claude和Serper API进行网络搜索，生成上下文分析、行业见解、会议策略和高管简报。

### 功能特性

- 用于彻底会议准备的多代理AI系统
- 利用OpenAI的GPT-4和Anthropic的Claude模型
- 使用Serper API的网络搜索功能
- 生成详细的上下文分析、行业见解、会议策略和高管简报

### 如何开始？

1. 克隆GitHub仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd advanced_ai_agents/single_agent_apps/ai_meeting_agent
```
2. 安装所需依赖：

```bash
pip install -r requirements.txt
```
3. 获取您的Anthropic API密钥

- 注册[Anthropic账户](https://console.anthropic.com)（或您选择的LLM提供商）并获取您的API密钥。

4. 获取您的SerpAPI密钥

- 注册[Serper API账户](https://serper.dev/)并获取您的API密钥。

5. 获取您的OpenAI API密钥

- 注册[OpenAI账户](https://platform.openai.com/)（或您选择的LLM提供商）并获取您的API密钥。

6. 运行Streamlit应用
```bash
streamlit run meeting_agent.py
```