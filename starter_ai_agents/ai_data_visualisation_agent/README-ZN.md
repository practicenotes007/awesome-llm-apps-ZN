# 📊 AI数据可视化代理
一个Streamlit应用程序，作为您的个人数据可视化专家，由LLM驱动。只需上传您的数据集并用自然语言提问 - AI代理将分析您的数据，生成适当的可视化图表，并通过图表、统计数据和解释的组合提供见解。

## 功能特性
#### 自然语言数据分析
- 用简单的英语询问关于您的数据的问题
- 获得即时的可视化和统计分析
- 接收发现和见解的解释
- 交互式后续提问

#### 智能可视化选择
- 自动选择适当的图表类型
- 动态可视化生成
- 统计可视化支持
- 自定义图表格式和样式

#### 多模型AI支持
- Meta-Llama 3.1 405B用于复杂分析
- DeepSeek V3用于详细见解
- Qwen 2.5 7B用于快速分析
- Meta-Llama 3.3 70B用于高级查询

## 运行方法

请按照以下步骤设置和运行应用程序：
- 首先，请在此处获取免费的Together AI API密钥：https://api.together.ai/signin
- 在此处获取免费的E2B API密钥：https://e2b.dev/ ； https://e2b.dev/docs/legacy/getting-started/api-key

1. **克隆仓库**
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd ai_agent_tutorials/ai_data_visualisation_agent
   ```
2. **安装依赖项**
    ```bash
    pip install -r requirements.txt
    ```
3. **运行Streamlit应用**
    ```bash
    streamlit run ai_data_visualisation_agent.py
    ```