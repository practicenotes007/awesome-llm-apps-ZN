# AI健康与健身规划代理 🏋️‍♂️

**AI健康与健身规划器**是一个由Agno AI代理框架驱动的个性化健康和健身代理。该应用根据用户输入的年龄、体重、身高、活动水平、饮食偏好和健身目标生成量身定制的饮食和健身计划。

## 功能特性

- **健康代理和健身代理**
    - 应用有两个phidata代理，分别是饮食建议和健身/锻炼建议方面的专家。

- **个性化饮食计划**：
  - 生成详细的膳食计划（早餐、午餐、晚餐和零食）。
  - 包括 hydration、电解质和纤维摄入等重要考虑因素。
  - 支持各种饮食偏好，如生酮、素食、低碳水化合物等。

- **个性化健身计划**：
  - 根据健身目标提供定制的锻炼计划。
  - 涵盖热身、主要锻炼和放松运动。
  - 包括可操作的健身提示和进度跟踪建议。

- **交互式问答**：允许用户就他们的计划提出后续问题。

## 要求

该应用程序需要以下Python库：

- `agno`
- `google-generativeai`
- `streamlit`

确保通过`requirements.txt`文件根据指定版本安装这些依赖项

## 如何运行

按照以下步骤设置和运行应用程序：
在开始之前，请在此处获取Google AI提供的免费Gemini API密钥：https://aistudio.google.com/apikey

1. **克隆仓库**：
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd advanced_ai_agents/single_agent_apps/ai_health_fitness_agent
   ```

2. **安装依赖**
    ```bash
    pip install -r requirements.txt
    ```
3. **运行Streamlit应用**
    ```bash
    streamlit run health_agent.py
    ```