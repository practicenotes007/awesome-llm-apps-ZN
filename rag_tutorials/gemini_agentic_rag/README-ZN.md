# 🤔 基于Gemini Flash Thinking的代理RAG

一个使用新的Gemini 2.0 Flash Thinking模型和gemini-exp-1206、Qdrant进行向量存储以及Agno（前身为phidata）进行代理编排构建的RAG代理系统。该应用程序具有智能查询重写、文档处理和网络搜索回退功能，以提供全面的AI驱动响应。

## 功能特性

- **文档处理**
  - PDF文档上传和处理
  - 网页内容提取
  - 自动文本分块和嵌入
  - Qdrant云中的向量存储

- **智能查询**
  - 查询重写以获得更好的检索效果
  - 基于RAG的文档检索
  - 带阈值过滤的相似性搜索
  - 自动回退到网络搜索
  - 答案的来源归属

- **高级功能**
  - Exa AI网络搜索集成
  - 网络搜索的自定义域过滤
  - 上下文感知的响应生成
  - 聊天历史管理
  - 查询重构代理

- **模型特定功能**
  - 用于聊天和推理的Gemini Thinking 2.0 Flash
  - 用于向量嵌入的Gemini嵌入模型
  - 用于编排的Agno代理框架
  - 基于Streamlit的交互式界面

## 先决条件

### 1. Google API密钥
1. 访问[Google AI Studio](https://aistudio.google.com/apikey)
2. 注册或登录您的账户
3. 创建新的API密钥

### 2. Qdrant云设置
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
cd rag_tutorials/gemini_agentic_rag
```

2. 安装依赖：
```bash
pip install -r requirements.txt
```

3. 运行应用程序：
```bash
streamlit run agentic_rag_gemini.py
```

## 使用方法

1. 在侧边栏配置API密钥：
   - 输入您的Google API密钥
   - 添加Qdrant凭证
   - （可选）添加Exa AI密钥以进行网络搜索

2. 上传文档：
   - 使用文件上传器上传PDF
   - 输入URL以获取网页内容

3. 提出问题：
   - 在聊天界面输入您的查询
   - 查看重写的查询和来源
   - 在相关时查看网络搜索结果

4. 管理会话：
   - 根据需要清除聊天历史
   - 配置网络搜索域
   - 监控处理的文档