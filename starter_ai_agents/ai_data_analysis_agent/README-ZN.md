# 📊 AI 数据分析代理

一个使用 Agno Agent 框架和 Openai 的 gpt-4o 模型构建的 AI 数据分析代理。该代理帮助用户通过自然语言查询分析他们的数据 - CSV、Excel 文件，由 OpenAI 的语言模型和 DuckDB 提供支持，实现高效的数据处理 - 使数据分析对无论是否具备 SQL 专业知识的用户都变得易于访问。

## 功能特性

- 📤 **文件上传支持**：
  - 上传 CSV 和 Excel 文件
  - 自动数据类型检测和模式推断
  - 支持多种文件格式

- 💬 **自然语言查询**：
  - 将自然语言问题转换为 SQL 查询
  - 获取关于您数据的即时答案
  - 无需 SQL 知识

- 🔍 **高级分析**：
  - 执行复杂的数据聚合
  - 过滤和排序数据
  - 生成统计摘要
  - 创建数据可视化

- 🎯 **交互式用户界面**：
  - 用户友好的 Streamlit 界面
  - 实时查询处理
  - 清晰的结果展示

## 如何运行

1. **环境设置**
   ```bash
   # 克隆仓库
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd awesome-llm-apps/starter_ai_agents/ai_data_analysis_agent

   # 安装依赖
   pip install -r requirements.txt
   ```

2. **配置 API 密钥**
   - 从 [OpenAI Platform](https://platform.openai.com) 获取 OpenAI API 密钥

3. **运行应用程序**
   ```bash
   streamlit run ai_data_analyst.py
   ```

## 使用方法

1. 使用上述命令启动应用程序
2. 在 Streamlit 的侧边栏中提供您的 OpenAI API 密钥
3. 通过 Streamlit 界面上传您的 CSV 或 Excel 文件
4. 用自然语言询问关于您数据的问题
5. 查看结果和生成的可视化图表