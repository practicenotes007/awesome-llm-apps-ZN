# AI演讲训练代理

## 概述
AI演讲训练师是一个由AI驱动的多代理、多模态公共演讲教练，它倾听您如何说话，观察您如何表达，并评估您说什么——帮助您成为自信的演讲者。

无论您是在准备TED演讲、面试还是学校展示，AI演讲训练师都会为您提供个性化反馈，帮助您提高公共演讲技能——突出您的优势和劣势，并为您提供宝贵的建议，让您说得更好、更清晰、更自信。

这个项目是作为**全球代理黑客马拉松（2025年5月）**的一部分构建的。它利用多代理协作、实时反馈和多模态分析的力量，帮助任何人成为自信而有效的演讲者。

## 功能特性
### 核心功能
- **面部表情分析**：情绪识别和眼神接触估算
- **音频分析**：节奏、音调、清晰度和填充词
- **内容评估**：基于GPT的结构、语调和清晰度反馈
- **个性化反馈**：平均分、整体评估、优势、劣势和改进建议

### 代理
- **面部代理**：分析表情、参与度和眼神接触
- **声音代理**：检测语音问题（速度、填充词、音调）
- **内容代理**：使用LLM评估和改进内容清晰度
- **反馈代理**：使用其他代理的响应根据评分标准评估演讲者
- **协调代理**：代理团队 - 协调所有分析和反馈生成

## 工作原理
### **用户流程**：
1. 用户打开Streamlit应用并上传自己练习演讲或展示的视频。

2. 多个代理开始行动：

- 面部代理分析表情和眼神接触。
- 声音代理转录演讲并检测声音属性。
- 内容代理评估语法、结构和连贯性。
- 反馈代理提供关于演讲整体效果的反馈。
- 协调代理汇总所有代理的见解。

AI演讲训练师呈现详细的反馈报告，包括基于评分标准的分数和反馈摘要。

### **核心功能**：
- 使用OpenCV、DeepFace和Mediapipe地标进行面部情绪识别。
- 语音转录和分析。
- 使用基于GPT的反馈进行内容分析。
- 聚合评估分数和反馈摘要。

### **多模态元素**：
- **音频**：语音输入和音质分析。
- **视频**：面部表情跟踪和反馈。
- **文本**：基于GPT的结构、清晰度和语调反馈。

## 技术栈
### AI/ML工具
- **Agno**：用于构建多代理协作和协调。
- **面部表情工具**：面部情绪分析 - 新的定制工具。
- **声音分析工具**：语音转录和分析 - 新的定制工具。
- **Together API (Llama-3.3-70B-Instruct-Turbo-Free)**：LLM - 内容分析和反馈生成。

### 应用框架
- **Streamlit**：用户界面前端。
- **FastAPI**：后端API端点。

### 语言和包
- **Python**：后端逻辑和代理实现的核心语言。
- **OpenCV + DeepFace + Mediapipe**：用于面部表情分析
- **Moviepy + Faster-Whisper + Librosa**：用于声音分析

## UI方法
使用Streamlit构建，UI包括：

- 带有视频上传部分、按钮和显示转录文本空间的主页。
- 反馈页面显示评估分数、详细反馈、优势、劣势、改进建议和性能图表。

## 视觉效果
### 高级架构
<img src="visuals/ai_speech_trainer.drawio.png">

### 主页
<img src="visuals/home.png">

### 反馈页面
<img src="visuals/feedback.png">

## 设置说明
### 1. 克隆仓库
```sh
git clone https://github.com/aminajavaid30/ai_speech_trainer.git
cd ai_speech_trainer
```

### 2. 安装依赖
```sh
pip install -r requirements.txt
```

### 3. **添加您的API密钥** - 创建一个.env文件包含：
```sh
TOGETHER_API_KEY=...
```

### 4. 初始化后端
导航到**backend**文件夹并运行以下命令：
```sh
uvicorn main:app --reload
```

### 5. 运行应用
导航到**frontend**文件夹并运行以下命令：
```sh
streamlit run Home.py
```

## 团队信息
- **团队负责人**：https://github.com/aminajavaid30 - 代理系统设计师和开发者
- **团队成员**：https://github.com/aminajavaid30 - 个人项目
- **背景/经验**：具有软件工程和Web开发背景的数据科学家。在构建AI产品和代理工作流程方面有经验。

## 演示视频链接
https://youtu.be/Sb0JPUpJTGQ

## 文件夹结构
```sh
/backend
  /agents
    /tools
      - facial_expression_tool.py
      - voice_analysis_tool.py
    - content_analysis_agent.py
    - coordinator_agent.py
    - facial_expression_agent.py
    - feedback_agent.py
    - voice_analysis_agent.py
  main.py (FastAPI应用)
/frontend
  /pages
    - 1 - Feedback.py
  Home.py
  page_config.py
  sidebar.py
  style.css
.env
LICENSE
README.md
requirements.txt
```

## 附加说明
- 这个项目旨在利用**Agno**作为AI代理开发平台的功能。它展示了Agno作为一个协作代理团队无缝协作解决现实世界挑战的潜力——分析用户的演讲展示并为他们提供全面的评估和反馈，以提高他们的公共演讲技能。每个单独的代理都有明确的目标要遵循，它们作为一个团队协调解决复杂的多模态问题。

- 这个项目有很大的进一步增强潜力。它可以成为一个更全面和有用的代理系统的起点。一些提议的附加功能可能包括：
  1. 通过不同角色场景整合实时视频录制和对话功能。
  2. 通过AI头像回放用户演讲，帮助用户学习和理解最佳演讲实践。
  3. 保留用户会话记录。
  4. 包含性能仪表板以跟踪用户随时间的性能。

   这些附加功能中的每一项都可以通过在系统中实现特定目标导向的代理来添加。

## 限制
- 使用**meta-llama/Llama-3.3-70B-Instruct-Turbo-Free**作为LLM的**Together API**有小的令牌限制，因此它适用于小视频片段（15-30秒）。
- 对于较长的视频片段使用其他LLM选项。不要忘记在*.env*文件中添加它们的API密钥。

## 致谢
为**#GlobalAgentHackathonMay2025**使用Agno、Streamlit、Together API和FastAPI构建。