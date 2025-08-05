# 基于LangGraph的代理RAG：AI博客搜索

## 概述
AI博客搜索是一个代理RAG应用程序，旨在增强从AI相关博客文章中检索信息的能力。该系统利用LangChain、LangGraph和Google的Gemini模型来获取、处理和分析博客内容，为用户提供准确且符合上下文的相关答案。

## LangGraph工作流程
![LangGraph-Workflow](https://github.com/user-attachments/assets/07d8a6b5-f1ef-4b7e-b47a-4f14a192bd8a)

## 演示
https://github.com/user-attachments/assets/cee07380-d3dc-45f4-ad26-7d944ba9c32b

## 功能特性
- **文档检索：** 使用Qdrant作为向量数据库，基于嵌入存储和检索博客内容。
- **代理查询处理：** 使用AI驱动的代理来确定查询是否应重写、回答或需要更多检索。
- **相关性评估：** 使用Google的Gemini模型实现自动相关性分级系统。
- **查询优化：** 增强结构不良的查询以获得更好的检索结果。
- **Streamlit UI：** 提供用户友好的界面，用于输入博客URL、查询并获取有见地的响应。
- **基于图的工作流程：** 使用LangGraph实现结构化状态图以进行高效决策。

## 使用的技术
- **编程语言**：[Python 3.10+](https://www.python.org/downloads/release/python-31011/)
- **框架**：[LangChain](https://www.langchain.com/) 和 [LangGraph](https://langchain-ai.github.io/langgraph/tutorials/introduction/)
- **数据库**：[Qdrant](https://qdrant.tech/)
- **模型**：
  - 嵌入：[Google Gemini API (embedding-001)](https://ai.google.dev/gemini-api/docs/embeddings)
  - 聊天：[Google Gemini API (gemini-2.0-flash)](https://ai.google.dev/gemini-api/docs/models/gemini#gemini-2.0-flash)
- **博客加载器**：[Langchain WebBaseLoader](https://python.langchain.com/docs/integrations/document_loaders/web_base/)
- **文档分割器**：[RecursiveCharacterTextSplitter](https://python.langchain.com/v0.1/docs/modules/data_connection/document_transformers/recursive_text_splitter/)
- **用户界面(UI)**：[Streamlit](https://docs.streamlit.io/)

## 要求
1. **安装依赖**：
   ```bash
   pip install -r requirements.txt
   ```

2. **运行应用程序**：
   ```bash
   streamlit run app.py
   ```

3. **使用应用程序**：
   - 在侧边栏粘贴您的Google API密钥。
   - 粘贴博客链接。
   - 输入您关于博客文章的查询。

## :mailbox: 与我联系
<img align="right" src="https://media.giphy.com/media/2HtWpp60NQ9CU/giphy.gif" alt="handshake gif" width="150">

<p align="left">
  <a href="https://linkedin.com/in/codewithcharan" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="codewithcharan" height="30" width="40" style="margin-right: 10px" /></a>
  <a href="https://instagram.com/joyboy._.ig" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/instagram.svg" alt="__mr.__.unique" height="30" width="40" /></a>
  <a href="https://twitter.com/Joyboy_x_" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/twitter.svg" alt="codewithcharan" height="30" width="40" style="margin-right: 10px" /></a>
</p>

<img src="https://readme-typing-svg.herokuapp.com/?font=Righteous&size=35&center=true&vCenter=true&width=500&height=70&duration=4000&lines=Thanks+for+visiting!+👋;+Message+me+on+Linkedin!;+I'm+always+down+to+collab+:)"/>