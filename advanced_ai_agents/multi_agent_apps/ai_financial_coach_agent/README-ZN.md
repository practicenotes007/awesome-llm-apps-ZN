# 带Google ADK的AI财务教练代理 💰

**AI财务教练**是一个由Google ADK（代理开发工具包）框架驱动的个性化财务顾问。该应用基于用户输入的收入、支出、债务和财务目标提供全面的财务分析和建议。

## 功能特性

- **多代理财务分析系统**
    - 预算分析代理：分析支出模式并推荐优化方案
    - 储蓄策略代理：创建个性化储蓄计划和应急基金策略
    - 债务减少代理：使用雪崩法和雪球法开发优化的债务偿还策略

- **支出分析**：
  - 支持CSV上传和手动支出录入
  - CSV交易分析，包含日期、类别和金额跟踪
  - 按类别支出的可视化分解
  - 自动支出分类和模式检测

- **储蓄建议**：
  - 应急基金规模和构建策略
  - 针对不同目标的自定义储蓄分配
  - 持续储蓄的实用自动化技术
  - 进度跟踪和里程碑建议

- **债务管理**：
  - 多重债务处理和利率优化
  - 雪崩法和雪球法的比较
  - 债务偿还时间线和利息节省分析的可视化
  - 可操作的债务减少建议

- **交互式可视化**：
  - 支出分解的饼图
  - 收入与支出的柱状图
  - 债务比较图
  - 进度跟踪指标

## 如何运行

按照以下步骤设置和运行应用程序：

1. **获取API密钥**：
   - 从Google AI Studio获取免费的Gemini API密钥：https://aistudio.google.com/apikey
   - 在项目根目录创建一个`.env`文件并添加您的API密钥：
     ```
     GOOGLE_API_KEY=your_api_key_here
     ```

2. **克隆仓库**：
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd awesome-llm-apps/advanced_ai_agents/multi_agent_apps/ai_financial_coach_agent/
   ```

3. **安装依赖**：
   ```bash
   pip install -r requirements.txt
   ```

4. **运行Streamlit应用**：
   ```bash
   streamlit run ai_financial_coach_agent.py
   ```

## CSV文件格式

应用程序接受具有以下必需列的CSV文件：
- `Date`：交易日期，格式为YYYY-MM-DD
- `Category`：支出类别
- `Amount`：交易金额（支持货币符号和逗号格式）

示例：
```csv
Date,Category,Amount
2024-01-01,Housing,1200.00
2024-01-02,Food,150.50
2024-01-03,Transportation,45.00
```

可以从应用程序的侧边栏直接下载模板CSV文件。