# ♜ 白方代理 vs 黑方代理：国际象棋游戏

一个先进的国际象棋游戏系统，其中两个AI代理使用Autogen在streamlit应用中相互对弈。它具有强大的走子验证和游戏状态管理功能。

## 功能特性

### 多代理架构
- 白方玩家：由OpenAI驱动的战略决策制定者
- 黑方玩家：由OpenAI驱动的战术对手
- 棋盘代理：走子合法性和游戏状态的验证代理

### 安全与验证
- 强大的走子验证系统
- 非法走子预防
- 实时棋盘状态监控
- 安全的游戏进程控制

### 策略性游戏玩法
- AI驱动的位置评估
- 深度战术分析
- 动态策略适应
- 完整国际象棋规则集实现

### 如何开始？

1. 克隆GitHub仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd ai_agent_tutorials/ai_chess_game
```
2. 安装所需依赖：

```bash
pip install -r requirements.txt
```
3. 获取您的OpenAI API密钥

- 注册[OpenAI账户](https://platform.openai.com/)（或您选择的LLM提供商）并获取您的API密钥。

4. 运行Streamlit应用
```bash
streamlit run ai_chess_agent.py
```