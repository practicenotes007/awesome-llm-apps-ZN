# 🐋 Deepseek本地RAG推理代理

一个强大的推理代理，将本地Deepseek模型与RAG功能相结合。使用Deepseek（通过Ollama）、Snowflake进行嵌入、Qdrant进行向量存储以及Agno进行代理编排构建，该应用程序提供简单的本地聊天和高级RAG增强交互，具有全面的文档处理和网络搜索功能。

## 功能特性

- **双操作模式**
  - 本地聊天模式：直接与本地Deepseek交互
  - RAG模式：增强的推理能力，包含文档上下文和网络搜索集成 - llama3.2

- **文档处理**（RAG模式）
  - PDF文档上传和处理
  - 网页内容提取
  - 自动文本分块和嵌入
  - Qdrant云中的向量存储

- **智能查询**（RAG模式）
  - 基于RAG的文档检索
  - 相似性搜索与阈值过滤
  - 自动回退到网络搜索
  - 答案的来源归属

- **高级功能**
  - Exa AI网络搜索集成
  - 网络搜索的自定义域过滤
  - 上下文感知的响应生成
  - 聊天历史管理
  - 思考过程可视化

- **模型特定功能**
  - 灵活的模型选择：
    - Deepseek r1 1.5b（较轻量，适合大多数笔记本电脑）
    - Deepseek r1 7b（功能更强，需要更好的硬件）
  - Snowflake Arctic嵌入模型（SOTA）用于向量嵌入
  - Agno代理框架用于编排
  - 基于Streamlit的交互式界面

## 先决条件

### 1. Ollama设置
1. 安装[Ollama](https://ollama.ai)
2. 拉取Deepseek r1模型：
```bash
# 对于较轻量的模型
ollama pull deepseek-r1:1.5b

# 对于功能更强的模型（如果您的硬件支持）
ollama pull deepseek-r1:7b

ollama pull snowflake-arctic-embed
ollama pull llama3.2
```

### 2. Qdrant云设置（用于RAG模式）
1. 访问[Qdrant云](https://cloud.qdrant.io/)
2. 创建账户或登录
3. 创建新集群
4. 获取您的凭证：
   - Qdrant API密钥：在API密钥部分找到
   - Qdrant URL：您的集群URL（格式：`https://xxx-xxx.cloud.qdrant.io`）

### 3. Exa AI API密钥（可选）
1. 访问[Exa AI](https://exa.ai)
2. 注册账户
3. 生成API密钥以获得网络搜索功能

## 如何运行

1. 克隆仓库：
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd rag_tutorials/deepseek_local_rag_agent
```

2. 安装依赖：
```bash
pip install -r requirements.txt
```

3. 运行应用程序：
```bash
streamlit run deepseek_rag_agent.py
```