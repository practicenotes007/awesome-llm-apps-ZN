# 带Cohere ⌘R 的RAG代理

一个使用Cohere的新模型Command-r7b-12-2024、Qdrant进行向量存储、Langchain进行RAG以及LangGraph进行编排构建的RAG代理系统。该应用程序允许用户上传文档、就文档提问，并在需要时回退到网络搜索以获得AI驱动的响应。

## 功能特性

- **文档处理**
  - PDF文档上传和处理
  - 自动文本分块和嵌入
  - Qdrant云中的向量存储

- **智能查询**
  - 基于RAG的文档检索
  - 带阈值过滤的相似性搜索
  - 当未找到相关文档时自动回退到网络搜索
  - 答案的来源归属

- **高级功能**
  - DuckDuckGo网络搜索集成
  - 用于网络研究的LangGraph代理
  - 上下文感知的响应生成
  - 长答案摘要

- **模型特定功能**
  - 用于聊天和RAG的Command-r7b-12-2024模型
  - 用于嵌入的cohere embed-english-v3.0模型
  - 来自langgraph的create_react_agent函数
  - 用于网络搜索的DuckDuckGoSearchRun工具

## 先决条件

### 1. Cohere API密钥
1. 访问[Cohere平台](https://dashboard.cohere.ai/api-keys)
2. 注册或登录您的账户
3. 导航到API密钥部分
4. 创建新的API密钥

### 2. Qdrant云设置
1. 访问[Qdrant云](https://cloud.qdrant.io/)
2. 创建账户或登录
3. 创建新集群
4. 获取您的凭证：
   - Qdrant API密钥：在API密钥部分找到
   - Qdrant URL：您的集群URL（格式：`https://xxx-xxx.aws.cloud.qdrant.io`）

## 如何运行

1. 克隆仓库：
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd rag_tutorials/rag_agent_cohere
```

2. 安装依赖：
```bash
pip install -r requirements.txt
```

```bash
streamlit run rag_agent_cohere.py
```