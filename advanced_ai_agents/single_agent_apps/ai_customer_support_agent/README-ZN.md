## 🛒 带记忆功能的AI客户支持代理
这个Streamlit应用实现了一个使用GPT-4o生成合成数据的AI驱动客户支持代理。该代理使用OpenAI的GPT-4o模型，并使用Mem0库和Qdrant作为向量存储来维护过去交互的记忆。

### 功能特性

- 用于与AI客户支持代理交互的聊天界面
- 客户交互和档案的持久化记忆
- 用于测试和演示的合成数据生成
- 利用OpenAI的GPT-4o模型提供智能响应

### 如何开始？

1. 克隆GitHub仓库
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd advanced_ai_agents/single_agent_apps/ai_customer_support_agent
```

2. 安装所需依赖：

```bash
pip install -r requirements.txt
```

3. 确保Qdrant正在运行：
应用程序期望Qdrant在localhost:6333上运行。如果您的设置不同，请在代码中调整配置。

```bash
docker pull qdrant/qdrant

docker run -p 6333:6333 -p 6334:6334 \
    -v "$(pwd)/qdrant_storage:/qdrant/storage:z" \
    qdrant/qdrant
```

4. 运行Streamlit应用
```bash
streamlit run customer_support_agent.py
```