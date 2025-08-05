# 带Cohere Embed-4的视觉RAG 🖼️

一个强大的视觉检索增强生成（RAG）系统，利用Cohere最先进的Embed-4模型进行多模态嵌入，使用Google高效的Gemini 2.5 Flash模型回答关于图像和PDF页面的问题。

## 功能特性

- **多模态搜索**：利用Cohere Embed-4查找与给定文本问题在语义上最相关的图像（或PDF页面图像）。
- **视觉问答**：使用Google Gemini 2.5 Flash分析检索到的图像/页面内容并生成准确、符合上下文的答案。
- **灵活的内容来源**：
    - 使用预加载的示例财务图表和信息图。
    - 上传您自己的自定义图像（PNG、JPG、JPEG）。
    - **上传PDF文档**：自动将页面提取为图像进行分析。
- **无需OCR**：直接处理复杂图像和PDF页面中的视觉元素，无需单独的文本提取步骤。
- **交互式用户界面**：使用Streamlit构建，便于交互，包括内容加载、问题输入和结果显示。
- **会话管理**：在会话中记住已加载/上传的内容（图像和处理的PDF页面）。

## 要求

- Python 3.8+
- Cohere API密钥
- Google Gemini API密钥

## 如何运行

按照以下步骤设置和运行应用程序：

1.  **克隆并导航到目录**：
    ```bash
    git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
    cd awesome-llm-apps/rag_tutorials/vision_rag
    ```

2.  **安装依赖**：
    ```bash
    pip install -r requirements.txt
    ```
    *（确保您已安装最新的`PyMuPDF`以及其他要求）*

3.  **设置您的API密钥**：
    - 从以下位置获取Cohere API密钥：[https://dashboard.cohere.com/api-keys](https://dashboard.cohere.com/api-keys)
    - 从以下位置获取Google API密钥：[https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)

4.  **运行Streamlit应用**：
    ```bash
    streamlit run vision_rag.py
    ```

5.  **访问Web界面**：
    - Streamlit将在终端中提供本地URL（通常是`http://localhost:8501`）。
    - 在Web浏览器中打开此URL。

## 工作原理

应用程序遵循两阶段RAG过程：

1.  **检索**：
    - 当您加载示例图像或上传自己的图像/PDF时：
        - 常规图像被转换为base64字符串。
        - **PDF按页面处理**：每个页面被渲染为图像，临时保存并转换为base64字符串。
    - 使用Cohere的`embed-v4.0`模型（带有`input_type="search_document"`）为每个图像或PDF页面图像生成密集向量嵌入。
    - 当您提出问题时，使用相同的`embed-v4.0`模型（带有`input_type="search_query"`）对文本查询进行嵌入。
    - 计算问题嵌入与所有图像嵌入之间的余弦相似度。
    - 检索具有最高相似度分数的图像（可能是常规图像或特定PDF页面图像）作为最相关的上下文。

2.  **生成**：
    - 原始文本问题和检索到的图像/页面图像作为输入传递给Google `gemini-2.5-flash-preview-04-17`模型。
    - Gemini在问题的上下文中分析图像内容并生成文本答案。

## 使用方法

1.  在侧边栏输入您的Cohere和Google API密钥。
2.  加载内容：
    - 点击**"Load Sample Images"**下载并处理内置示例。
    - *或/和*使用**"Upload Your Images or PDFs"**部分上传您自己的图像或PDF文件。
3.  一旦内容加载并处理完成（生成嵌入），**"Ask a Question"**部分将被启用。
4.  （可选）展开**"View Loaded Images"**查看当前会话中所有图像和处理的PDF页面的缩略图。
5.  在文本输入字段中输入关于已加载内容的问题。
6.  点击**"Run Vision RAG"**。
7.  查看结果：
    - 被认为与您的问题最相关的**检索到的图像/页面**（标题指示源PDF和页码，如果适用）。
    - 基于图像和问题的Gemini**生成答案**。

## 使用场景

- 分析财务图表并提取关键数据或趋势。
- 回答关于图像或PDF中图表、流程图或信息图的具体问题。
- 从屏幕截图或PDF页面中提取表格或文本中的信息，而无需显式OCR。
- 使用自然语言构建和查询视觉知识库（来自图像和PDF）。
- 理解各种复杂视觉文档的内容，包括多页报告。

## 注意事项

- 图像和PDF处理（页面渲染+嵌入）可能需要时间，特别是对于许多项目或大文件。示例图像在首次加载后会被缓存；PDF处理目前在会话中每次上传时都会进行。
- 确保您的API密钥具有使用Cohere和Gemini模型所需的权限和配额。
- 答案的质量取决于检索到的图像的相关性和Gemini模型基于问题解释图像的能力。