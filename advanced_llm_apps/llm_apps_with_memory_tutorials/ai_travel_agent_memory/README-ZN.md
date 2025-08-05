## 🧳 带记忆功能的 AI 旅行代理
此 Streamlit 应用实现了一个 AI 驱动的旅行助手，能够记住用户偏好和过去的交互历史。它利用 OpenAI 的 GPT-4o 生成响应，并使用 Mem0 和 Qdrant 维护对话历史。

### 功能特性
- 基于聊天的界面，用于与 AI 旅行助手交互
- 持久化存储用户偏好和过去对话的记忆
- 利用 OpenAI 的 GPT-4o 模型生成智能响应
- 使用 Mem0 和 Qdrant 实现记忆存储和检索
- 用户特定的对话历史和记忆查看功能

### 如何开始？

1. 克隆 GitHub 仓库
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/llm_apps_with_memory_tutorials/ai_travel_agent_memory
```

2. 安装所需依赖：

```bash
pip install -r requirements.txt
```

3. 确保 Qdrant 正在运行：
应用程序期望 Qdrant 在 localhost:6333 上运行。如果您的设置不同，请在代码中调整配置。

```bash
docker pull qdrant/qdrant

docker run -p 6333:6333 -p 6334:6334 \
    -v $(pwd)/qdrant_storage:/qdrant/storage:z \
    qdrant/qdrant
```

4. 运行 Streamlit 应用
```bash
streamlit run travel_agent_memory.py
```