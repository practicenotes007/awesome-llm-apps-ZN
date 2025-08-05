## 📽️ 与YouTube视频聊天

使用RAG技术与YouTube视频进行聊天的LLM应用，采用OpenAI的gpt-4o、mem0/embedchain作为记忆功能以及youtube-transcript-api。该应用使用检索增强生成（RAG）技术，基于上传视频的内容提供准确的答案。

### 功能特性

- 输入YouTube视频URL
- 就视频内容提出问题
- 使用RAG和所选LLM获得准确答案

### 如何开始？

1. 克隆GitHub仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/chat_with_X_tutorials/chat_with_youtube_videos
```
2. 安装所需依赖：

```bash
pip install -r requirements.txt
```
3. 获取您的OpenAI API密钥

- 注册[OpenAI账户](https://platform.openai.com/)（或您选择的LLM提供商）并获取您的API密钥。

4. 运行Streamlit应用
```bash
streamlit run chat_youtube.py
```