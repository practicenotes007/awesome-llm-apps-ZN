## 🧠 使用Llama 3.1和个性化记忆的本地ChatGPT
这个Streamlit应用程序实现了一个完全本地化的ChatGPT式体验，使用Llama 3.1，并为每个用户提供个性化记忆存储。所有组件，包括语言模型、嵌入和向量存储，都在本地运行，无需外部API密钥。

### 功能特性
- 完全本地化实现，无外部API依赖
- 通过Ollama驱动的Llama 3.1
- 为每个用户提供个人记忆空间
- 使用Nomic Embed进行本地嵌入生成
- 使用Qdrant进行向量存储

### 如何开始？

1. 克隆GitHub仓库
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/llm_apps_with_memory_tutorials/local_chatgpt_with_memory
```

2. 安装所需依赖：

```bash
cd awesome-llm-apps/rag_tutorials/local_rag_agent
pip install -r requirements.txt
```

3. 在本地安装并启动[Qdrant](https://qdrant.tech/documentation/guides/installation/)向量数据库

```bash
docker pull qdrant/qdrant
docker run -p 6333:6333 qdrant/qdrant
```

4. 安装[Ollama](https://ollama.com/download)并拉取Llama 3.1
```bash
ollama pull llama3.1
```

5. 运行Streamlit应用
```bash
streamlit run local_chatgpt_memory.py
```