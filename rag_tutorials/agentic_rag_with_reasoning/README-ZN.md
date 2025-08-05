# 🧐 带推理的代理RAG
一个复杂的RAG系统，使用Agno、Claude和OpenAI演示AI代理的逐步推理过程。该实现允许用户上传文档、添加网络资源、提出问题，并实时观察代理的思考过程。

## 功能特性

1. 交互式知识库管理
- 上传文档以扩展知识库
- 动态添加URL以获取网络内容
- 使用LanceDB进行持久化向量数据库存储

2. 透明的推理过程
- 实时显示代理的思考步骤
- 推理和最终答案的并排视图
- 清晰可见RAG过程

3. 高级RAG功能
- 使用OpenAI嵌入进行向量搜索以实现语义匹配
- 带引用的来源归属

## 代理配置

- Claude 3.5 Sonnet用于语言处理
- OpenAI嵌入模型用于向量搜索
- ReasoningTools用于逐步分析
- 可自定义的代理指令

## 先决条件

您需要以下API密钥：

1. Anthropic API密钥

- 在console.anthropic.com注册
- 导航到API密钥部分
- 创建新的API密钥

2. OpenAI API密钥

- 在platform.openai.com注册
- 导航到API密钥部分
- 生成新的API密钥

## 如何运行

1. **克隆仓库**：
    ```bash
    git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
    cd rag_tutorials/agentic_rag_with_reasoning
    ```

2. **安装依赖**：
    ```bash
    pip install -r requirements.txt
    ```

3. **运行应用程序：**
    ```bash
    streamlit run rag_reasoning_agent.py
    ```

4. **配置API密钥：**

- 在第一个字段中输入您的Anthropic API密钥
- 在第二个字段中输入您的OpenAI API密钥
- 应用程序正常运行需要两个密钥

5. **使用应用程序：**

- 添加知识源：使用侧边栏向知识库添加URL
- 提出问题：在主输入字段中输入查询
- 查看推理：实时观察代理的思考过程
- 获取答案：接收带来源引用的综合响应

## 工作原理

该应用程序使用复杂的RAG流水线：

### 知识库设置
- 使用WebBaseLoader从URL加载文档
- 使用OpenAI的嵌入模型对文本进行分块和嵌入
- 向量存储在LanceDB中以实现高效检索
- 向量搜索实现语义匹配以获取相关信息

### 代理处理
- 用户查询触发代理的推理过程
- ReasoningTools帮助代理逐步思考
- 代理在知识库中搜索相关信息
- Claude 4 Sonnet生成带引用的综合答案

### 用户界面流程
- 输入API密钥 → 添加知识源 → 提出问题
- 推理过程和答案生成并排显示
- 为透明度和验证引用来源