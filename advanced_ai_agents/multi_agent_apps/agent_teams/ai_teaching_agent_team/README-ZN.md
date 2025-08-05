# 👨‍🏫 AI教学代理团队

一个Streamlit应用程序，汇集了一支专业教学代理团队，他们像专业教学团队一样协作。每个代理都充当专业教育者：课程设计师、学习路径专家、资源图书管理员和实践指导师——通过Google Docs协作创建完整的教育体验。

## 🪄 认识您的AI教学代理团队

#### 🧠 教授代理
- 在Google Docs中创建基础知识库
- 使用适当的标题和章节组织内容
- 包含详细的解释和示例
- 输出：带目录的综合知识库文档

#### 🗺️ 学术顾问代理
- 在结构化的Google Doc中设计学习路径
- 创建渐进式里程碑标记
- 包含时间估算和先决条件
- 输出：带清晰进展路径的可视化路线图文档

#### 📚 研究图书管理员代理
- 在有序的Google Doc中汇编资源
- 包含学术论文和教程的链接
- 添加描述和难度等级
- 输出：带质量评级的分类资源列表

#### ✍️ 助教代理
- 在交互式Google Doc中开发练习
- 创建结构化实践部分
- 包含解决方案指南
- 输出：带答案的完整练习册

## 如何运行

1. 克隆仓库
  ```bash
   # 克隆仓库
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd ai_agent_tutorials/ai_personal_learning_agent

   # 安装依赖
   pip install -r requirements.txt
   ```

## 配置 - 重要步骤

1. 获取您的OpenAI API密钥
- 在[OpenAI平台](https://platform.openai.com/)创建账户
- 导航到API密钥部分
- 创建新的API密钥

2. 获取您的Composio API密钥
- 在[Composio平台](https://composio.ai/)创建账户
- **重要** - 要使用该应用，您需要使用google docs和composio创建新的连接ID。按照以下两个步骤操作：
  - composio add googledocs（在终端中）
  - 创建新连接
  - 选择OAUTH2
  - 选择Google账户并完成。
  - 在composio账户网站上，转到应用程序，选择google docs工具，[点击创建集成](https://app.composio.dev/app/googledocs)（紫色按钮）并点击尝试连接默认的googldocs按钮，我们就完成了。

3. 注册并获取[SerpAPI密钥](https://serpapi.com/)

## 如何使用？

1. 启动Streamlit应用
```bash
streamlit run teaching_agent_team.py
```

2. 使用应用程序
- 在侧边栏输入您的OpenAI API密钥（如果未在环境中设置）
- 在侧边栏输入您的Composio API密钥
- 输入您想学习的主题（例如，"Python编程"、"机器学习"）
- 点击"Generate Learning Plan"
- 等待代理生成您的个性化学习计划
- 在界面中查看结果和终端输出