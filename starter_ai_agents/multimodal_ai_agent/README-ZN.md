## 🧬 多模态AI代理

一个Streamlit应用程序，结合了Google Gemini 2.0模型的视频分析和网络搜索功能。该代理可以分析上传的视频，并通过结合视觉理解和网络搜索来回答问题。

### 功能特性

- 使用Gemini 2.0 Flash进行视频分析
- 通过DuckDuckGo集成网络研究
- 支持多种视频格式（MP4、MOV、AVI）
- 实时视频处理
- 结合视觉和文本分析

### 如何开始？

1. 克隆GitHub仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd ai_agent_tutorials/multimodal_ai_agent
```
2. 安装所需依赖项：

```bash
pip install -r requirements.txt
```
3. 获取您的Google Gemini API密钥

- 注册[Google AI Studio账户](https://aistudio.google.com/apikey)并获取您的API密钥。

4. 将您的Gemini API密钥设置为环境变量

```bash
GOOGLE_API_KEY=your_api_key_here
```

5. 运行Streamlit应用
```bash
streamlit run multimodal_agent.py
```