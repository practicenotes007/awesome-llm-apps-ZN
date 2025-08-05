# 🐙 GitHub MCP代理

一个Streamlit应用程序，允许您通过模型上下文协议（MCP）使用自然语言查询来探索和分析GitHub仓库。

## 功能特性

- **自然语言界面**：用简单的英语询问有关仓库的问题
- **全面分析**：探索问题、拉取请求、仓库活动和代码统计
- **交互式用户界面**：带有示例查询和自定义输入的用户友好界面
- **MCP集成**：利用模型上下文协议与GitHub的API交互
- **实时结果**：获取有关仓库活动和健康状况的即时洞察

## 设置

### 要求

- Python 3.8+
- Node.js和npm（用于MCP GitHub服务器）
  - 这是一个关键要求！应用程序使用`npx`运行MCP GitHub服务器
  - 从[nodejs.org](https://nodejs.org/)下载并安装
- 具有适当权限的GitHub个人访问令牌
- OpenAI API密钥

### 安装

1. 克隆此仓库：
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd mcp-github-agent
   ```

2. 安装所需的Python包：
   ```bash
   pip install -r requirements.txt
   ```

3. 验证Node.js和npm已安装：
   ```bash
   node --version
   npm --version
   npx --version
   ```
   所有这些命令都应返回版本号。如果没有，请安装Node.js。

4. 设置您的API密钥：
   - 将OpenAI API密钥设置为环境变量：
     ```bash
     export OPENAI_API_KEY=your-openai-api-key
     ```
   - GitHub令牌将直接在应用程序界面中输入

5. 创建GitHub个人访问令牌：
   - 访问 https://github.com/settings/tokens
   - 创建一个具有`repo`和`user`范围的新令牌
   - 将令牌保存在安全的地方

### 运行应用程序

1. 启动Streamlit应用程序：
   ```bash
   streamlit run app.py
   ```

2. 在应用程序界面中：
   - 在侧边栏中输入您的GitHub令牌
   - 指定要分析的仓库
   - 选择查询类型或编写您自己的查询
   - 点击"Run Query"

### 示例查询

#### 问题
- "按标签显示问题"
- "哪些问题正在积极讨论？"
- "查找标记为bug的问题"

#### 拉取请求
- "哪些PR需要审查？"
- "显示最近合并的PR"
- "查找有冲突的PR"

#### 仓库
- "显示仓库健康指标"
- "显示仓库活动模式"
- "分析代码质量趋势"