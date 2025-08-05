# 🐋 Qwen 3 本地RAG推理代理

这个RAG应用程序演示了如何使用通过Ollama本地运行的Qwen 3和Gemma 3模型构建强大的检索增强生成（RAG）系统。它结合了文档处理、向量搜索和网络搜索功能，为用户提供准确、符合上下文的响应。

## 功能特性

- **🧠 多种本地LLM选项**：

  - Qwen3 (1.7b, 8b) - 阿里巴巴最新的语言模型
  - Gemma3 (1b, 4b) - 谷歌的高效语言模型，具有多模态功能
  - DeepSeek (1.5b) - 替代模型选项
- **📚 全面的RAG系统**：

  - 上传和处理PDF文档
  - 从网页URL提取内容
  - 智能分块和嵌入
  - 带可调阈值的相似性搜索
- **🌐 网络搜索集成**：

  - 当文档知识不足时回退到网络搜索
  - 可配置的域过滤
  - 响应中的来源归属
- **🔄 灵活的操作模式**：

  - 在RAG和直接LLM交互之间切换
  - 在需要时强制网络搜索
  - 调整文档检索的相似性阈值
- **💾 向量数据库集成**：

  - 用于高效相似性搜索的Qdrant向量数据库
  - 文档嵌入的持久化存储

## 如何开始

### 先决条件

- 本地安装[Ollama](https://ollama.ai/)
- Python 3.8+
- Qdrant账户（提供免费层）用于向量存储
- Exa API密钥（可选，用于网络搜索功能）

### 安装步骤

1. 克隆GitHub仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd rag_tutorials/qwen_local_rag
```

2. 安装所需依赖：

```bash
pip install -r requirements.txt
```

3. 使用Ollama拉取所需模型：

```bash
ollama pull qwen3:1.7b # 或任何您想使用的其他模型
ollama pull snowflake-arctic-embed # 或任何您想使用的其他模型
```
4. 通过docker本地运行Qdrant
```bash
docker pull qdrant/qdrant

docker run -p 6333:6333 -p 6334:6334 \
    -v "$(pwd)/qdrant_storage:/qdrant/storage:z" \
    qdrant/qdrant
```

4. 获取您的API密钥：

   - Exa API密钥（可选，用于网络搜索）
   
5. 运行应用程序：

```bash
streamlit run qwen_local_rag_agent.py
```

## 工作原理

1. **文档处理**：

   - 使用PyPDFLoader处理PDF文件
   - 使用WebBaseLoader提取网页内容
   - 使用RecursiveCharacterTextSplitter将文档分割成块
2. **向量数据库**：

   - 使用Ollama的嵌入模型对文档块进行嵌入
   - 将嵌入存储在Qdrant向量数据库中
   - 相似性搜索根据查询检索相关文档
3. **查询处理**：

   - 分析用户查询以确定最佳信息源
   - 使用相似性阈值检查文档相关性
   - 如果未找到相关文档则回退到网络搜索
4. **响应生成**：

   - 本地LLM（Qwen/Gemma）基于检索到的上下文生成响应
   - 引用并显示给用户的来源
   - 清楚地标示使用时的网络搜索结果

## 配置选项

- **模型选择**：在不同的Qwen、Gemma和DeepSeek模型之间选择
- **RAG模式**：在启用RAG和直接LLM交互之间切换
- **搜索调整**：调整文档检索的相似性阈值
- **网络搜索**：启用/禁用网络搜索回退并配置域过滤

## 使用场景

- **文档问答**：就您上传的文档提问
- **研究助手**：结合文档知识和网络搜索
- **本地隐私**：处理敏感文档而无需将数据发送到外部API
- **离线操作**：在有限或无互联网访问的情况下运行高级AI功能

## 要求

有关完整的依赖列表，请参见`requirements.txt`。