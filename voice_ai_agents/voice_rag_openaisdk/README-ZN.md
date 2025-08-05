## 🎙️ 使用OpenAI SDK的语音RAG

此脚本演示了如何使用OpenAI的SDK和Streamlit构建一个支持语音的检索增强生成（RAG）系统。该应用程序允许用户上传PDF文档、提出问题，并使用OpenAI的文本转语音功能接收文本和语音响应。

### 功能特性

- 使用OpenAI的SDK创建支持语音的RAG系统
- 支持PDF文档处理和分块
- 使用Qdrant作为向量数据库进行高效的相似性搜索
- 实现实时文本转语音，支持多种语音选项
- 提供用户友好的Streamlit界面
- 允许下载生成的音频响应
- 支持多文档上传和跟踪

### 如何开始？

1. 克隆GitHub仓库
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/rag_tutorials/voice_rag_openaisdk
```

2. 安装所需依赖项：
```bash
pip install -r requirements.txt
```

3. 设置您的API密钥：
- 从[OpenAI Platform](https://platform.openai.com/)获取您的[OpenAI API密钥](https://platform.openai.com/)
- 设置一个[Qdrant Cloud](https://cloud.qdrant.io/)账户并获取您的API密钥和URL
- 创建一个包含您凭据的`.env`文件：
```bash
OPENAI_API_KEY='your-openai-api-key'
QDRANT_URL='your-qdrant-url'
QDRANT_API_KEY='your-qdrant-api-key'
```

4. 运行语音RAG应用程序：
```bash
streamlit run rag_voice.py
```

5. 打开您的网络浏览器并导航到控制台输出中提供的URL以与语音RAG系统交互。

### 工作原理？

1. **文档处理：** 
   - 通过Streamlit界面上传PDF文档
   - 使用LangChain的RecursiveCharacterTextSplitter将文档分割成块
   - 每个块使用FastEmbed嵌入并存储在Qdrant中

2. **查询处理：**
   - 用户问题被转换为嵌入
   - 从Qdrant中检索相似文档
   - 处理代理生成清晰、适合口语的响应
   - TTS代理优化响应以进行语音合成

3. **语音生成：**
   - 使用OpenAI的TTS将文本响应转换为语音
   - 用户可以从多种语音选项中选择
   - 音频可以直接播放或下载为MP3

4. **功能特性：**
   - 实时音频流
   - 多种语音个性选项
   - 文档来源跟踪
   - 音频响应下载功能
   - 文档处理进度跟踪