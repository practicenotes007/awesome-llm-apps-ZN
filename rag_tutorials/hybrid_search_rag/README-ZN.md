# 👀 带混合搜索的RAG应用

一个强大的文档问答应用程序，利用混合搜索（RAG）和Claude的高级语言功能提供全面的答案。使用RAGLite进行强大的文档处理和检索，使用Streamlit构建直观的聊天界面，该系统无缝结合文档特定知识和Claude的通用智能，以提供准确和符合上下文的响应。

## 功能特性

- **混合搜索问答**
    - 基于RAG的文档特定查询答案
    - 回退到Claude处理通用知识问题

- **文档处理**：
  - PDF文档上传和处理
  - 自动文本分块和嵌入
  - 结合语义和关键词匹配的混合搜索
  - 重排序以获得更好的上下文选择

- **多模型集成**：
  - Claude用于文本生成 - 使用Claude 3 Opus测试
  - OpenAI用于嵌入 - 使用text-embedding-3-large测试
  - Cohere用于重排序 - 使用Cohere 3.5 reranker测试

## 先决条件

您需要以下API密钥和数据库设置：

1. **数据库**：在[Neon](https://neon.tech)创建免费的PostgreSQL数据库：
   - 在Neon注册/登录
   - 创建新项目
   - 复制连接字符串（格式如：`postgresql://user:pass@ep-xyz.region.aws.neon.tech/dbname`）

2. **API密钥**：
   - [OpenAI API密钥](https://platform.openai.com/api-keys)用于嵌入
   - [Anthropic API密钥](https://console.anthropic.com/settings/keys)用于Claude
   - [Cohere API密钥](https://dashboard.cohere.com/api-keys)用于重排序

## 如何开始？

1. **克隆仓库**：
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd awesome-llm-apps/rag_tutorials/hybrid_search_rag
   ```

2. **安装依赖**：
   ```bash
   pip install -r requirements.txt
   ```

3. **安装spaCy模型**：
   ```bash
   pip install https://github.com/explosion/spacy-models/releases/download/xx_sent_ud_sm-3.7.0/xx_sent_ud_sm-3.7.0-py3-none-any.whl
   ```

4. **运行应用程序**：
   ```bash
   streamlit run main.py
   ```

## 使用方法

1. 启动应用程序
2. 在侧边栏输入您的API密钥：
   - OpenAI API密钥
   - Anthropic API密钥
   - Cohere API密钥
   - 数据库URL（可选，默认为SQLite）
3. 点击"Save Configuration"
4. 上传PDF文档
5. 开始提问！
   - 文档特定问题将使用RAG
   - 通用问题将直接使用Claude

## 数据库选项

该应用程序支持多种数据库后端：

- **PostgreSQL**（推荐）：
  - 在[Neon](https://neon.tech)创建免费的无服务器PostgreSQL数据库
  - 获得即时配置和零扩展能力
  - 连接字符串格式：`postgresql://user:pass@ep-xyz.region.aws.neon.tech/dbname`

- **MySQL**：
  ```
  mysql://user:pass@host:port/db
  ```
- **SQLite**（本地开发）：
  ```
  sqlite:///path/to/db.sqlite
  ```

## 贡献

欢迎贡献！请随时提交拉取请求。