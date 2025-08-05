# AI服务代理机构 👨‍💼

一个AI应用程序，使用多个AI代理模拟全方位服务的数字代理机构来分析和规划软件项目。每个代理代表项目生命周期中的不同角色，从战略规划到技术实施。

## 演示: 

https://github.com/user-attachments/assets/a0befa3a-f4c3-400d-9790-4b9e37254405

## 功能特性

### 五个专业AI代理

- **CEO代理**: 战略领导者和最终决策者
  - 使用结构化评估分析初创企业想法
  - 在产品、技术、营销和财务领域做出战略决策
  - 使用AnalyzeStartupTool和MakeStrategicDecision工具

- **CTO代理**: 技术架构和可行性专家
  - 评估技术要求和可行性
  - 提供架构决策
  - 使用QueryTechnicalRequirements和EvaluateTechnicalFeasibility工具

- **产品经理代理**: 产品战略专家
  - 定义产品战略和路线图
  - 协调技术和营销团队
  - 专注于产品市场契合度

- **开发代理**: 技术实施专家
  - 提供详细的技术实施指导
  - 建议最佳技术栈和云解决方案
  - 估算开发成本和时间表

- **客户成功代理**: 营销战略领导者
  - 制定市场进入策略
  - 规划客户获取方法
  - 与产品团队协调

### 自定义工具

代理机构使用OpenAI Schema构建的专业工具进行结构化分析：
- **分析工具**: AnalyzeProjectRequirements用于市场评估和初创企业想法分析
- **技术工具**: CreateTechnicalSpecification用于技术评估

### 🔄 异步通信

代理机构以异步模式运行，支持：
- 不同代理分析的并行处理
- 高效的多代理协作
- 代理间的实时通信
- 非阻塞操作以获得更好的性能

### 🔗 代理通信流程
- CEO ↔️ 所有代理（战略监督）
- CTO ↔️ 开发者（技术实施）
- 产品经理 ↔️ 市场经理（市场进入策略）
- 产品经理 ↔️ 开发者（功能实施）
- （还有更多！）

## 如何运行

按照以下步骤设置和运行应用程序：
在开始之前，请在此处获取您的OpenAI API密钥: https://platform.openai.com/api-keys

1. **克隆仓库**:
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd advanced_ai_agents/multi_agent_apps/agent_teams/ai_services_agency
   ```

2. **安装依赖**:
    ```bash
    pip install -r requirements.txt
    ```

3. **运行Streamlit应用**:
    ```bash
    streamlit run agency.py
    ```

4. **在提示时在侧边栏输入您的OpenAI API密钥**并开始分析您的初创企业想法！