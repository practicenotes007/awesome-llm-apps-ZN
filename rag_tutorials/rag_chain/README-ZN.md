# PharmaQuery

## 概述
PharmaQuery是一个先进的制药洞察检索系统，旨在帮助用户从制药领域的研究论文和文档中获得有意义的见解。

## 演示
https://github.com/user-attachments/assets/c12ee305-86fe-4f71-9219-57c7f438f291

## 功能特性
- **自然语言查询**：就制药行业提出复杂问题，并获得简洁、准确的答案。
- **自定义数据库**：上传您自己的研究文档以增强检索系统的知识库。
- **相似性搜索**：使用AI嵌入检索与您的查询最相关的文档。
- **Streamlit界面**：用于查询和文档上传的用户友好界面。

## 使用的技术
- **编程语言**：[Python 3.10+](https://www.python.org/downloads/release/python-31011/)
- **框架**：[LangChain](https://www.langchain.com/)
- **数据库**：[ChromaDB](https://www.trychroma.com/)
- **模型**：
  - 嵌入：[Google Gemini API (embedding-001)](https://ai.google.dev/gemini-api/docs/embeddings)
  - 聊天：[Google Gemini API (gemini-1.5-pro)](https://ai.google.dev/gemini-api/docs/models/gemini#gemini-1.5-pro)
- **PDF处理**：[PyPDFLoader](https://python.langchain.com/docs/integrations/document_loaders/pypdfloader/)
- **文档分割器**：[SentenceTransformersTokenTextSplitter](https://python.langchain.com/api_reference/text_splitters/sentence_transformers/langchain_text_splitters.sentence_transformers.SentenceTransformersTokenTextSplitter.html)

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
   - 在主界面输入您的查询。
   - （可选）在侧边栏上传研究论文以增强数据库。

## :mailbox: 与我联系
<img align="right" src="https://media.giphy.com/media/2HtWpp60NQ9CU/giphy.gif" alt="handshake gif" width="150">

<p align="left">
  <a href="https://linkedin.com/in/codewithcharan" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="codewithcharan" height="30" width="40" style="margin-right: 10px" /></a>
  <a href="https://instagram.com/joyboy._.ig" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/instagram.svg" alt="__mr.__.unique" height="30" width="40" /></a>
  <a href="https://twitter.com/Joyboy_x_" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/twitter.svg" alt="codewithcharan" height="30" width="40" style="margin-right: 10px" /></a>
</p>