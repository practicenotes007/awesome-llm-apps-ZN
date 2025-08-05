## 📚 带记忆功能的AI研究代理
这个Streamlit应用实现了一个由AI驱动的研究助手，帮助用户在arXiv上搜索学术论文，同时保持对用户兴趣和过去交互的记忆。它利用OpenAI的GPT-4o-mini模型处理搜索结果，使用MultiOn进行网页浏览，以及使用Mem0和Qdrant维护用户上下文。

### 功能特性

- 用于查询arXiv论文的搜索界面
- AI驱动的搜索结果处理以提高可读性
- 持久化存储用户兴趣和过去搜索的记忆
- 利用OpenAI的GPT-4o-mini模型进行智能处理
- 使用Mem0和Qdrant实现记忆存储和检索

### 如何开始？

1. 克隆GitHub仓库
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/llm_apps_with_memory_tutorials/ai_arxiv_agent_memory
```

2. 安装所需依赖：

```bash
pip install -r requirements.txt
```

3. 确保Qdrant正在运行：
应用程序期望Qdrant在localhost:6333上运行。如果您的设置不同，请在代码中调整配置。

```bash
docker pull qdrant/qdrant

docker run -p 6333:6333 -p 6334:6334 \
    -v $(pwd)/qdrant_storage:/qdrant/storage:z \
    qdrant/qdrant
```

4. 运行Streamlit应用
```bash
streamlit run ai_arxiv_agent_memory.py
```