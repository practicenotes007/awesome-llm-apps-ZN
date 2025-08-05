## ModelsLab音乐生成器

这是一个基于Streamlit的应用程序，允许用户使用ModelsLab API和OpenAI的GPT-4模型生成音乐。用户可以输入描述他们想要生成的音乐类型的提示，应用程序将根据给定的提示生成MP3格式的音乐轨道。

## 功能特性

- **生成音乐**：输入详细的音乐生成提示（流派、乐器、情绪等），应用将生成音乐轨道。
- **MP3输出**：生成的音乐将以MP3格式提供，可收听或下载。
- **用户友好界面**：简单清晰的Streamlit UI，易于使用。
- **API密钥集成**：需要OpenAI和ModelsLab API密钥才能运行。API密钥在侧边栏中输入进行身份验证。

## 设置

### 要求

1. **API密钥**：
   - **OpenAI API密钥**：在[OpenAI](https://platform.openai.com/api-keys)注册以获取您的API密钥。
   - **ModelsLab API密钥**：在[ModelsLab](https://modelslab.com/dashboard/api-keys)注册以获取您的API密钥。

2. **Python 3.8+**：确保您已安装Python 3.8或更高版本。

### 安装
1. 克隆此仓库：
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps
   cd ai_agent_tutorials/ai_models_lab_music_generator_agent
   ```

2. 安装所需的Python包：
   ```bash
   pip install -r requirements.txt
   ```
### 运行应用

1. 启动Streamlit应用：
   ```bash
   streamlit run models_lab_music_generator_agent.py
   ```

2. 在应用界面中：
   - 输入音乐生成提示
   - 点击"Generate Music"
   - 播放音乐并下载。