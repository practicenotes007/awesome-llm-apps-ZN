# 📑 Notion MCP代理

一个基于终端的Notion代理，通过Notion MCP（模型上下文协议）服务器使用自然语言与您的Notion页面交互。

## 功能特性

- 通过命令行界面与Notion页面交互
- 对您的Notion页面执行更新、插入、检索操作
- 创建和编辑块、列表、表格和其他Notion结构
- 向块添加评论
- 搜索特定信息
- 记住对话上下文以进行多轮交互
- 会话管理以保持持续对话

## 先决条件

- Python 3.9+
- 具有管理员权限的Notion账户
- Notion集成令牌
- OpenAI API密钥

## 安装

1. 克隆仓库
2. 安装所需的Python包：

```bash
pip install -r requirements.txt
```

3. 安装Notion MCP服务器（运行应用程序时会自动完成）

## 设置Notion集成

### 创建Notion集成

1. 访问[Notion集成](https://www.notion.so/my-integrations)
2. 点击"New integration"
3. 为您的集成命名（例如，"Notion Assistant"）
4. 选择所需功能（读取和写入内容）
5. 提交并复制您的"Internal Integration Token"

### 与集成共享您的Notion页面

1. 打开您的Notion页面
2. 点击页面右上角的三个点（⋮）
3. 从下拉菜单中选择"Add connections"
4. 在搜索框中搜索您的集成名称
5. 点击您的集成以将其添加到页面
6. 在出现的对话框中点击"Confirm"确认

或者，您也可以通过"Share"按钮共享：
1. 点击右上角的"Share"
2. 在共享对话框中，搜索您的集成名称（以"@"开头）
3. 点击您的集成以添加它
4. 点击"Invite"授予其对您页面的访问权限

这两种方法都会授予您的集成对页面及其内容的完全访问权限。

### 查找您的Notion页面ID

1. 在浏览器中打开您的Notion页面
2. 复制URL，格式如下：
   `https://www.notion.so/workspace/Your-Page-1f5b8a8ba283...`
3. ID是最后一个破折号后和任何查询参数前的部分
   示例：`1f5b8a8bad058a7e39a6`

## 配置

您可以使用环境变量配置代理：

- `NOTION_API_KEY`：您的Notion集成令牌
- `OPENAI_API_KEY`：您的OpenAI API密钥
- `NOTION_PAGE_ID`：您的Notion页面ID

或者，您可以直接在脚本中设置这些值。

## 使用方法

从命令行运行代理：

```bash
python notion_mcp_agent.py
```

启动代理时，它会提示您输入Notion页面ID。您可以：
1. 在提示符下输入您的页面ID
2. 不输入任何内容直接按Enter以使用默认页面ID（如果已设置）
3. 直接作为命令行参数提供页面ID（绕过提示）：

```bash
python notion_mcp_agent.py your-page-id-here
```

### 对话流程

每次启动代理时，它都会创建一个唯一的用户ID和会话ID以维护对话上下文。这使得代理能够记住之前的交互，并在您关闭和重启应用程序后继续连贯的对话。

您可以随时通过输入`exit`、`quit`、`bye`或`goodbye`退出对话。

## 示例查询

- "我的Notion页面上有什么？"
- "添加一个新段落，内容为'今天的会议记录'"
- "创建一个包含三个项目的符号列表：苹果、香蕉、橙子"
- "在第一个段落添加评论'这看起来不错！'"
- "搜索任何关于会议的提及"
- "总结我们到目前为止的对话"

## 许可证

MIT