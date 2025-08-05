## 🗃️ 带网络访问功能的 AI RAG 代理
此脚本演示了如何使用仅 15 行 Python 代码构建具有网络访问功能的检索增强生成（RAG）代理。该代理使用 PDF 知识库，并具备使用 DuckDuckGo 搜索网络的能力。

### 功能特性

- 使用 GPT-4o 创建 RAG 代理
- 整合基于 PDF 的知识库
- 使用 LanceDB 作为向量数据库进行高效相似性搜索
- 通过 DuckDuckGo 包含网络搜索功能
- 提供游乐场界面以便轻松交互

### 如何开始？

1. 克隆 GitHub 仓库
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/rag_tutorials/agentic_rag
```

2. 安装所需依赖：

```bash
pip install -r requirements.txt
```

3. 获取您的 OpenAI API 密钥

- 注册 [OpenAI 账户](https://platform.openai.com/)（或您选择的 LLM 提供商）并获取您的 API 密钥。
- 将您的 OpenAI API 密钥设置为环境变量：
```bash
export OPENAI_API_KEY='your-api-key-here'
```

4. 运行 AI RAG 代理
```bash
python3 rag_agent.py
```
5. 打开您的网络浏览器并导航到控制台输出中提供的 URL，通过游乐场界面与 RAG 代理进行交互。

### 工作原理？

1. **知识库创建：** 脚本从在线托管的 PDF 文件创建知识库。
2. **向量数据库设置：** 使用 LanceDB 作为向量数据库，在知识库内进行高效相似性搜索。
3. **代理配置：** 使用 GPT-4o 作为底层模型创建 AI 代理，并配备 PDF 知识库和 DuckDuckGo 搜索工具。
4. **游乐场设置：** 设置游乐场界面以便与 RAG 代理轻松交互。