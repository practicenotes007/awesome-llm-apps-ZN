# 🔍 AI领域深度研究代理

一个使用Agno代理框架、Together AI的Qwen模型和Composio工具构建的高级AI研究代理。该代理通过生成研究问题、通过多个搜索引擎查找答案，并结合Google Docs集成编译专业报告，帮助用户对任何主题进行综合研究。

## 功能特性

- 🧠 **智能问题生成**：

  - 自动为您的主题生成5个具体的研究问题
  - 根据您指定的领域定制问题
  - 专注于创建是/否问题以获得明确的研究结果
- 🔎 **多源研究**：

  - 使用Tavily搜索获取全面的网络结果
  - 利用Perplexity AI进行深入分析
  - 结合多个来源进行彻底研究
- 📊 **专业报告生成**：

  - 将研究发现编译成麦肯锡风格的报告
  - 用执行摘要、分析和结论构建内容
  - 创建包含完整报告的Google文档
- 🖥️ **用户友好界面**：

  - 清晰的Streamlit UI和直观的工作流程
  - 实时进度跟踪
  - 可展开的部分查看详细结果

## 如何运行

1. **设置环境**

   ```bash
   # 克隆仓库
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd advanced_ai_agents/single_agent_apps/ai_domain_deep_research_agent

   # 安装依赖
   pip install -r requirements.txt

   composio add googledocs
   composio add perplexityai
   ```
2. **配置API密钥**

   - 从[Together AI](https://together.ai)获取Together AI API密钥
   - 从[Composio](https://composio.ai)获取Composio API密钥
   - 将这些添加到`.env`文件中或在应用侧边栏中输入
3. **运行应用程序**

   ```bash
   streamlit run ai_domain_deep_research_agent.py
   ```

## 使用方法

1. 使用上述命令启动应用程序
2. 在侧边栏中输入您的Together AI和Composio API密钥
3. 在主界面输入您的研究主题和领域
4. 点击"Generate Research Questions"创建具体问题
5. 查看问题并点击"Start Research"开始研究过程
6. 研究完成后，点击"Compile Final Report"生成专业报告
7. 在应用中查看报告并通过Google Docs访问

## 技术细节

- **Agno框架**：用于创建和编排AI代理
- **Together AI**：提供Qwen 3 235B模型用于高级语言处理
- **Composio工具**：集成搜索引擎和Google Docs功能
- **Streamlit**：通过交互元素驱动用户界面

## 示例用例

- **学术研究**：快速收集各个学科的学术主题信息
- **市场分析**：研究市场趋势、竞争对手和行业发展
- **政策研究**：分析政策影响和历史背景
- **技术评估**：研究新兴技术及其潜在影响

## 依赖项

- agno
- composio_agno
- streamlit
- python-dotenv

## 许可证

该项目是awesome-llm-apps集合的一部分，可在MIT许可证下使用。