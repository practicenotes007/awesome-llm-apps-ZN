# 💼 AI招聘代理团队

一个Streamlit应用程序，使用多个AI代理模拟全方位服务的招聘团队，以自动化和简化招聘流程。每个代理代表不同的招聘专家角色——从简历分析和候选人评估到面试安排和沟通——共同协作提供全面的招聘解决方案。该系统将技术招聘人员、人力资源协调员和安排专家的专业知识结合到一个连贯的自动化工作流程中。

## 功能特性

#### 专业AI代理

- 技术招聘代理：分析简历和评估技术技能
- 沟通代理：处理专业电子邮件通信
- 安排协调代理：管理面试安排和协调
- 每个代理都有特定的专业知识，并协作提供全面的招聘服务

#### 端到端招聘流程
- 自动化简历筛选和分析
- 角色特定的技术评估
- 专业的候选人沟通
- 自动化面试安排
- 集成反馈系统

## 运行应用程序前的重要事项

- 创建/使用一个新的Gmail账户作为招聘人员邮箱
- 启用两步验证并为Gmail账户生成应用密码
- 应用密码是一个16位代码（使用时不带空格），应在此处生成 - [Google应用密码](https://support.google.com/accounts/answer/185833?hl=en) 请按照步骤生成密码 - 格式为 - 'afec wejf awoj fwrv'（删除空格并在streamlit应用中输入）
- 创建/使用一个Zoom账户并前往Zoom应用市场获取API凭证：
[Zoom市场](https://marketplace.zoom.us)
- 前往开发者仪表板并创建一个新应用 - 选择服务器到服务器OAuth并获取凭证，您会看到3个凭证 - 客户端ID、客户端密钥和账户ID
- 之后，您需要为应用添加一些范围 - 以便通过邮件发送和创建候选人的zoom链接。
- 范围包括meeting:write:invite_links:admin, meeting:write:meeting:admin, meeting:write:meeting:master, meeting:write:invite_links:master, meeting:write:open_app:admin, user:read:email:admin, user:read:list_users:admin, billing:read:user_entitlement:admin, dashboard:read:list_meeting_participants:admin [最后3个是可选的]

## 如何运行

1. **设置环境**
   ```bash
   # 克隆仓库
    git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
    cd advanced_ai_agents/multi_agent_apps/agent_teams/ai_recruitment_agent_team
    
   # 安装依赖
   pip install -r requirements.txt
   ```

2. **配置API密钥**
   - OpenAI API密钥用于GPT-4o访问
   - Zoom API凭证（账户ID、客户端ID、客户端密钥）
   - 招聘人员邮箱的应用密码

3. **运行应用程序**
   ```bash
   streamlit run ai_recruitment_agent_team.py
   ```

## 系统组件

- **简历分析代理**
  - 技能匹配算法
  - 经验验证
  - 技术评估
  - 选择决策制定

- **电子邮件沟通代理**
  - 专业邮件起草
  - 自动通知
  - 反馈沟通
  - 跟进管理

- **面试安排代理**
  - Zoom会议协调
  - 日历管理
  - 时区处理
  - 提醒系统

- **候选人体验**
  - 简单上传界面
  - 实时反馈
  - 清晰沟通
  - 简化流程

## 技术栈

- **框架**：Phidata
- **模型**：OpenAI GPT-4o
- **集成**：Zoom API，Phidata的EmailTools工具
- **PDF处理**：PyPDF2
- **时间管理**：pytz
- **状态管理**：Streamlit会话状态

## 免责声明

此工具旨在协助招聘流程，但不应完全替代招聘决策中的人为判断。所有自动化决策都应由人工招聘人员审查以获得最终批准。

## 未来增强功能

- 与ATS系统集成
- 高级候选人评分
- 视频面试功能
- 技能评估集成
- 多语言支持