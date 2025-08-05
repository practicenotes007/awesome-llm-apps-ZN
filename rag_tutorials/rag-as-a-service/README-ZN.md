## 🖇️ RAG即服务与Claude 3.5 Sonnet
使用Claude 3.5 Sonnet和Ragie.ai构建和部署生产就绪的检索增强生成（RAG）服务。此实现允许您创建一个文档查询系统，配备用户友好的Streamlit界面，仅需不到50行Python代码。

### 功能特性
- 生产就绪的RAG流水线
- 与Claude 3.5 Sonnet集成用于响应生成
- 从URL上传文档
- 实时文档查询
- 支持快速和准确的文档处理模式

### 如何开始？

1. 克隆GitHub仓库
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/rag_tutorials/rag-as-a-service
```

2. 安装所需依赖：

```bash
pip install -r requirements.txt
```

3. 获取您的Anthropic API和Ragie API密钥

- 注册[Anthropic账户](https://console.anthropic.com/)并获取您的API密钥
- 注册[Ragie账户](https://www.ragie.ai/)并获取您的API密钥

4. 运行Streamlit应用
```bash
streamlit run rag_app.py
```