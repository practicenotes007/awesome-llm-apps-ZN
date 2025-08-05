# 🖥️ 带混合搜索的本地RAG应用

一个强大的文档问答应用程序，利用混合搜索（RAG）和本地LLM提供全面的答案。使用RAGLite进行强大的文档处理和检索，使用Streamlit构建直观的聊天界面，该系统结合文档特定知识和本地LLM功能，以提供准确和符合上下文的响应。

## 演示:


https://github.com/user-attachments/assets/375da089-1ab9-4bf4-b6f3-733f44e47403


## 快速开始

为了立即测试，请使用这些经过测试的模型配置：
```bash
# LLM模型
bartowski/Llama-3.2-3B-Instruct-GGUF/Llama-3.2-3B-Instruct-Q4_K_M.gguf@4096

# 嵌入器模型
lm-kit/bge-m3-gguf/bge-m3-Q4_K_M.gguf@1024
```
这些模型在性能和资源使用之间提供了良好的平衡，并且已经验证即使在配备8GB RAM的MacBook Air M2上也能良好运行。

## 功能特性

- **本地LLM集成**：
  - 使用llama-cpp-python模型进行本地推理
  - 支持各种量化格式（推荐Q4_K_M）
  - 可配置的上下文窗口大小

- **文档处理**：
  - PDF文档上传和处理
  - 自动文本分块和嵌入
  - 结合语义和关键词匹配的混合搜索
  - 重排序以获得更好的上下文选择

- **多模型集成**：
  - 本地LLM用于文本生成（例如，Llama-3.2-3B-Instruct）
  - 使用BGE模型进行本地嵌入
  - FlashRank用于本地重排序

## 先决条件

1. **安装spaCy模型**：
   ```bash
   pip install https://github.com/explosion/spacy-models/releases/download/xx_sent_ud_sm-3.7.0/xx_sent_ud_sm-3.7.0-py3-none-any.whl
   ```

2. **安装加速版llama-cpp-python**（可选但推荐）：
   ```bash
   # 配置安装变量
   LLAMA_CPP_PYTHON_VERSION=0.3.2
   PYTHON_VERSION=310 # 3.10, 3.11, 3.12
   ACCELERATOR=metal  # 适用于Mac
   # ACCELERATOR=cu121  # 适用于NVIDIA GPU
   PLATFORM=macosx_11_0_arm64  # 适用于Mac
   # PLATFORM=linux_x86_64  # 适用于Linux
   # PLATFORM=win_amd64  # 适用于Windows

   # 安装加速版本
   pip install "https://github.com/abetlen/llama-cpp-python/releases/download/v$LLAMA_CPP_PYTHON_VERSION-$ACCELERATOR/llama_cpp_python-$LLAMA_CPP_PYTHON_VERSION-cp$PYTHON_VERSION-cp$PYTHON_VERSION-$PLATFORM.whl"
   ```

3. **安装依赖**：
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd awesome-llm-apps/rag_tutorials/local_hybrid_search_rag
   pip install -r requirements.txt
   ```

## 模型设置

RAGLite通过llama-cpp-python扩展了LiteLLM对llama.cpp模型的支持。要选择llama.cpp模型（例如，来自bartowski集合），请使用格式为"llama-cpp-python/<hugging_face_repo_id>/<filename>@<n_ctx>"的模型标识符，其中n_ctx是可选参数，指定模型的上下文大小。

1. **LLM模型路径格式**：
   ```
   llama-cpp-python/<repo>/<model>/<filename>@<context_length>
   ```
   示例：
   ```
   bartowski/Llama-3.2-3B-Instruct-GGUF/Llama-3.2-3B-Instruct-Q4_K_M.gguf@4096
   ```

2. **嵌入器模型路径格式**：
   ```
   llama-cpp-python/<repo>/<model>/<filename>@<dimension>
   ```
   示例：
   ```
   lm-kit/bge-m3-gguf/bge-m3-Q4_K_M.gguf@1024
   ```

## 数据库设置

该应用程序支持多种数据库后端：

- **PostgreSQL**（推荐）：
  - 在[Neon](https://neon.tech)上创建免费的无服务器PostgreSQL数据库，只需几次点击
  - 获得即时配置和零扩展能力
  - 连接字符串格式：`postgresql://user:pass@ep-xyz.region.aws.neon.tech/dbname`

## 如何运行

1. **启动应用程序**：
   ```bash
   streamlit run local_main.py
   ```

2. **配置应用程序**：
   - 输入LLM模型路径
   - 输入嵌入器模型路径
   - 设置数据库URL
   - 点击"Save Configuration"

3. **上传文档**：
   - 通过界面上传PDF文件
   - 等待处理完成

4. **开始聊天**：
   - 就您的文档提出问题
   - 使用本地LLM获取响应
   - 在需要时回退到通用知识

## 注意事项

- 对于大多数用例，推荐4096的上下文窗口大小
- Q4_K_M量化在速度和质量之间提供了良好的平衡
- 带1024维度的BGE-M3嵌入器是最佳选择
- 本地模型需要足够的RAM和CPU/GPU资源
- Mac支持Metal加速，NVIDIA GPU支持CUDA

## 贡献

欢迎贡献！请随时提交拉取请求。