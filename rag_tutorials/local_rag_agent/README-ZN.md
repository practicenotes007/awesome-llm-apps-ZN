## 🦙 基于 Llama 3.2 的本地 RAG 代理
此应用程序通过 Ollama 实现了一个使用 Llama 3.2 的检索增强生成（RAG）系统，并使用 Qdrant 作为向量数据库。

### 功能特性
- 完全本地化的 RAG 实现
- 通过 Ollama 驱动的 Llama 3.2
- 使用 Qdrant 进行向量搜索
- 交互式游乐场界面
- 无外部 API 依赖

### 如何开始？

1. 克隆 GitHub 仓库
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
```

2. 安装所需依赖：

```bash
cd awesome-llm-apps/rag_tutorials/local_rag_agent
pip install -r requirements.txt
```

3. 在本地安装并启动 [Qdrant](https://qdrant.tech/) 向量数据库

```bash
docker pull qdrant/qdrant
docker run -p 6333:6333 qdrant/qdrant
```

4. 安装 [Ollama](https://ollama.com/download) 并拉取 Llama 3.2 作为 LLM，以及 OpenHermes 作为 OllamaEmbedder 的嵌入器
```bash
ollama pull llama3.2
ollama pull openhermes
```

4. 运行 AI RAG 代理
```bash
python local_rag_agent.py
```

5. 打开您的网络浏览器并导航到控制台输出中提供的 URL，通过游乐场界面与 RAG 代理进行交互。