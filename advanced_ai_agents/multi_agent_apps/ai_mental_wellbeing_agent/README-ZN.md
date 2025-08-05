# AI心理健康代理团队 🧠

AI心理健康代理团队是一个由[AG2](https://github.com/ag2ai/ag2?tab=readme-ov-file)（前身为AutoGen）的AI代理框架驱动的支持性心理健康评估和指导系统。该应用通过协调专业AI代理提供个性化的心理健康支持，每个代理专注于心理健康护理的不同方面，基于用户输入的情绪状态、压力水平、睡眠模式和当前症状等信息。这是基于AG2的新swarm功能，通过initiate_swarm_chat()方法运行。

## 功能特性

- **专业心理健康支持团队**
    - 🧠 **评估代理**：以临床精确性和同理心分析情绪状态和心理需求
    - 🎯 **行动代理**：创建即时行动计划并将用户与适当资源联系起来
    - 🔄 **跟进代理**：设计长期支持策略和预防计划

- **全面的心理健康支持**：
  - 详细的心理评估
  - 即时应对策略
  - 资源推荐
  - 长期支持规划
  - 危机预防策略
  - 进展监控系统

- **可定制的输入参数**：
  - 当前情绪状态
  - 睡眠模式
  - 压力水平
  - 支持系统信息
  - 最近的生活变化
  - 当前症状

- **交互式结果**：
   - 实时评估摘要
   - 详细建议在可展开部分中显示
   - 明确的行动步骤和资源
   - 长期支持策略

## 如何运行

按照以下步骤设置和运行应用程序：

1. **克隆仓库**：
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd advanced_ai_agents/multi_agent_apps/ai_mental_wellbeing_agent
   ```

2. **安装依赖**：
   ```bash
   pip install -r requirements.txt
   ```

3. **创建环境文件**：
   在项目目录中创建一个`.env`文件：
   ```bash
   echo "AUTOGEN_USE_DOCKER=0" > .env
   ```
   这将禁用AutoGen中代码执行的Docker要求。

4. **设置OpenAI API密钥**：
   - 从[OpenAI平台](https://platform.openai.com)获取OpenAI API密钥
   - 运行时您将在应用的侧边栏输入此密钥

5. **运行Streamlit应用**：
   ```bash
   streamlit run ai_mental_wellbeing_agent.py
   ```

## ⚠️ 重要通知

此应用程序是一个支持工具，不能替代专业心理健康护理。如果您正在经历自残想法或严重危机：

- 拨打国家危机热线：988
- 拨打紧急服务电话：911
- 寻求即时专业帮助