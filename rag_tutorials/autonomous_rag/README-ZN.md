# 🤖 AutoRAG：基于GPT-4o和向量数据库的自主RAG
这个Streamlit应用程序实现了一个使用OpenAI的GPT-4o模型和PgVector数据库的自主检索增强生成（RAG）系统。它允许用户上传PDF文档，将其添加到知识库中，并使用来自知识库和网络搜索的上下文查询AI助手。

### 功能特性
- 用于与AI助手交互的聊天界面
- PDF文档上传和处理
- 使用PostgreSQL和Pgvector的知识库集成
- 使用DuckDuckGo的网络搜索功能
- 助手数据和对话的持久化存储

### 如何开始？

1. 克隆GitHub仓库
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/rag_tutorials/autonomous_rag
```

2. 安装所需依赖：

```bash
pip install -r requirements.txt
```

3. 确保PgVector数据库正在运行：
应用程序期望PgVector在[localhost:5532](http://localhost:5532/)上运行。如果您的设置不同，请在代码中调整配置。

```bash
docker run -d \
  -e POSTGRES_DB=ai \
  -e POSTGRES_USER=ai \
  -e POSTGRES_PASSWORD=ai \
  -e PGDATA=/var/lib/postgresql/data/pgdata \
  -v pgvolume:/var/lib/postgresql/data \
  -p 5532:5432 \
  --name pgvector \
  phidata/pgvector:16
```

4. 运行Streamlit应用
```bash
streamlit run autorag.py
```