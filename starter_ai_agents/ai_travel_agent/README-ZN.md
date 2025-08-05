## 🛫 AI 旅行代理
这个 Streamlit 应用是一个由 AI 驱动的旅行代理，使用 OpenAI GPT-4o 生成个性化的旅行行程。它自动化了研究、规划和组织您梦想假期的过程，让您能够轻松探索令人兴奋的目的地。

### 功能特性
- 研究和发现令人兴奋的旅行目的地、活动和住宿
- 根据您想要旅行的天数自定义您的行程
- 利用 GPT-4o 的强大功能生成智能和个性化的旅行计划
- 将您的行程下载为日历（.ics）文件，导入到 Google 日历、苹果日历或其他日历应用中

### 如何开始？

1. 克隆 GitHub 仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/ai_agent_tutorials/ai_travel_agent
```
2. 安装所需依赖：

```bash
pip install -r requirements.txt
```
3. 获取您的 OpenAI API 密钥

- 注册 [OpenAI 账户](https://platform.openai.com/)（或您选择的 LLM 提供商）并获取您的 API 密钥。

4. 获取您的 SerpAPI 密钥

- 注册 [SerpAPI 账户](https://serpapi.com/) 并获取您的 API 密钥。

5. 运行 Streamlit 应用
```bash
streamlit run travel_agent.py
```

对于本地 LLM 使用（通过 Ollama）：
```bash
streamlit run local_travel_agent.py
```

### 工作原理？

AI 旅行代理有两个主要组件：
- **研究员：** 负责根据用户的目 的地和旅行时长生成搜索词，并使用 SerpAPI 搜索相关的活动和住宿。
- **规划师：** 接收研究结果和用户偏好，生成包含建议活动、餐饮选项和住宿的个性化行程草案。

### 使用日历下载功能

生成您的旅行行程后：
1. 点击出现在"Generate Itinerary"按钮旁边的"Download Itinerary as Calendar (.ics)"按钮
2. 将 .ics 文件保存到您的计算机
3. 将文件导入到您喜欢的日历应用程序（Google 日历、苹果日历、Outlook 等）
4. 您行程的每一天将作为全天事件出现在您的日历中
5. 每天活动的完整详细信息都包含在事件描述中

此功能使您能够轻松跟踪您的旅行计划，并在所有设备上查看您的行程，即使在离线状态下也可以。

### 本地版本与云端版本

- **travel_agent.py**：使用 OpenAI 的 GPT-4o 生成高质量行程（需要 OpenAI API 密钥）
- **local_travel_agent.py**：使用 Ollama 进行本地 LLM 推理，无需将数据发送到外部 API（需要安装并运行 Ollama）