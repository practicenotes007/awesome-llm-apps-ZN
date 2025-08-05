# 🎮 代理 X 对代理 O：井字棋游戏

一个交互式井字棋游戏，其中两个由不同语言模型驱动的 AI 代理相互竞争，基于 Agno Agent 框架和 Streamlit 作为用户界面构建。

此示例展示了如何构建一个 AI 代理相互竞争的交互式井字棋游戏。该应用程序展示了如何：
- 在回合制游戏中协调多个 AI 代理
- 为不同玩家使用不同的语言模型
- 使用 Streamlit 创建交互式 Web 界面
- 处理游戏状态和移动验证
- 显示实时游戏进度和移动历史

## 功能特性
- 多 AI 模型支持（GPT-4、Claude、Gemini 等）
- 实时游戏可视化
- 带棋盘状态的移动历史跟踪
- 交互式玩家选择
- 游戏状态管理
- 移动验证和协调

## 如何运行？

1. **环境设置**
   ```bash
   # 克隆仓库
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd advanced_ai_agents/autonomous_game_playing_agent_apps/ai_tic_tac_toe_agent

   # 安装依赖
   pip install -r requirements.txt
   ```

### 2. 安装依赖

```shell
pip install -r requirements.txt
```

### 3. 设置 API 密钥

游戏支持多个 AI 模型。在此目录中创建一个 `.env` 文件并添加您的 API 密钥：

1. **创建一个 `.env` 文件：**
   ```bash
   # 在 ai_tic_tac_toe_agent 目录中
   touch .env
   ```

2. **将您的 API 密钥添加到 `.env` 文件中：**
   ```env
   # OpenAI 模型 (gpt-4o, o3-mini) 所需
   OPENAI_API_KEY=your_actual_openai_api_key_here

   # 可选 - 用于其他模型
   ANTHROPIC_API_KEY=your_actual_anthropic_api_key_here  # 用于 Claude 模型
   GOOGLE_API_KEY=your_actual_google_api_key_here        # 用于 Gemini 模型
   GROQ_API_KEY=your_actual_groq_api_key_here           # 用于 Groq 模型
   ```

   > **注意：** 请将占位符值替换为您的实际 API 密钥。如果缺少必需的密钥，应用程序将显示有用的错误消息。

### 4. 运行游戏

```shell
streamlit run app.py
```

- 打开 [localhost:8501](http://localhost:8501) 查看游戏界面

## 工作原理

游戏由三个代理组成：

1. **主代理（裁判）**
   - 协调游戏
   - 验证移动
   - 维护游戏状态
   - 确定游戏结果

2. **两个玩家代理**
   - 制定策略性移动
   - 分析棋盘状态
   - 遵守游戏规则
   - 响应对手移动

## 可用模型

游戏支持各种 AI 模型：
- GPT-4o (OpenAI)
- GPT-o3-mini (OpenAI)
- Gemini (Google)
- Llama 3 (Groq)
- Claude (Anthropic)

## 游戏功能

1. **交互式棋盘**
   - 实时更新
   - 视觉移动跟踪
   - 清晰的游戏状态显示

2. **移动历史**
   - 详细移动跟踪
   - 棋盘状态可视化
   - 玩家行动时间线

3. **游戏控制**
   - 开始/暂停游戏
   - 重置棋盘
   - 选择 AI 模型
   - 查看游戏历史

4. **性能分析**
   - 移动计时
   - 策略跟踪
   - 游戏统计数据