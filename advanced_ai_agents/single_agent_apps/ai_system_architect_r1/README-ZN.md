# 🤖 基于R1的AI系统架构师顾问

一个Agno代理系统，使用结合DeepSeek R1推理和Claude的双模型方法提供专业的软件架构分析和建议。该系统为复杂的软件系统提供详细的技术分析、实施路线图和架构决策。

## 功能特性

- **双AI模型架构**
  - **DeepSeek推理器**：提供初始技术分析和关于架构模式、工具和实施策略的结构化推理
  - **Claude-3.5**：基于DeepSeek的分析生成详细解释、实施路线图和技术规范

- **全面分析组件**
  - 架构模式选择
  - 基础设施资源规划
  - 安全措施和合规性
  - 数据库架构
  - 性能要求
  - 成本估算
  - 风险评估

- **分析类型**
  - 实时事件处理系统
  - 医疗数据平台
  - 金融交易平台
  - 多租户SaaS解决方案
  - 数字内容分发网络
  - 供应链管理系统

## 如何运行

1. **环境设置**
   ```bash
   # 克隆仓库
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd advanced_ai_agents/single_agent_apps/ai_system_architect_r1
   
   # 安装依赖
   pip install -r requirements.txt
   ```

2. **配置API密钥**
   - 从DeepSeek平台获取DeepSeek API密钥
   - 从[Anthropic平台](https://www.anthropic.com)获取Anthropic API密钥

3. **运行应用程序**
   ```bash
   streamlit run ai_system_architect_r1.py
   ```

4. **使用界面**
   - 在侧边栏输入API凭证
   - 构造您的提示，包括：
     - 项目背景
     - 需求
     - 约束条件
     - 规模
     - 安全/合规需求
   - 查看详细分析结果

## 示例测试提示：

### 1. 金融交易平台
"我们需要构建一个高频交易平台，处理市场数据流，以亚毫秒级延迟执行交易，保持审计跟踪，并处理复杂的风险计算。系统需要全球分布，处理每秒100,000笔交易，并具有强大的灾难恢复能力。"
### 2. 多租户SaaS平台
"设计一个企业资源规划的多租户SaaS平台，需要支持每个租户的定制化，处理不同的数据驻留要求，支持离线功能，并保持租户之间的性能隔离。系统应扩展到10,000个并发用户并支持自定义集成。"

## 注意事项

- 需要DeepSeek和Anthropic API密钥
- 提供实时分析和详细解释
- 支持基于聊天的交互
- 包含所有架构决策的清晰推理
- 会产生API使用费用