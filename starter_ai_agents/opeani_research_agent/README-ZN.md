# OpenAI研究员代理
一个使用OpenAI Agents SDK和Streamlit构建的多代理研究应用程序。该应用程序使用户能够通过利用多个专业化的AI代理对任何主题进行综合研究。

### 功能特性

- 多代理架构：
    - 分诊代理：规划研究方法并协调工作流程
    - 研究代理：搜索网络并收集相关信息
    - 编辑代理：将收集的事实编译成综合报告

- 自动事实收集：从研究中捕获重要事实并注明来源
- 结构化报告生成：创建包含标题、大纲和来源引用的组织良好的报告
- 交互式用户界面：使用Streamlit构建，便于输入研究主题和查看结果
- 跟踪和监控：集成整个研究工作流程的跟踪

### 如何开始？

1. 克隆GitHub仓库
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/ai_agent_tutorials/openai_researcher_agent
```

2. 安装所需依赖项：

```bash
cd awesome-llm-apps/ai_agent_tutorials/openai_researcher_agent
pip install -r requirements.txt
```

3. 获取您的OpenAI API密钥

- 注册[OpenAI账户](https://platform.openai.com/)并获取您的API密钥。
- 设置您的OPENAI_API_KEY环境变量。
```bash
export OPENAI_API_KEY='your-api-key-here'
```

4. 运行AI代理团队
```bash
streamlit run openai_researcher_agent.py
```

然后打开您的浏览器并导航到终端中显示的URL（通常是http://localhost:8501）。

### 研究过程：
- 在侧边栏中输入研究主题或选择提供的示例之一
- 点击"Start Research"开始过程
- 在"Research Process"标签页中实时查看研究过程
- 完成后，切换到"Report"标签页查看和下载生成的报告