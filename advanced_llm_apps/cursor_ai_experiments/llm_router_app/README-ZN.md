## 📡 RouteLLM聊天应用

> 注意：该项目受到开源[RouteLLM库](https://github.com/lm-sys/RouteLLM/tree/main)的启发，该库提供了在不同语言模型之间智能路由的功能。

这个Streamlit应用程序演示了RouteLLM的使用，这是一个根据任务复杂性在不同语言模型之间智能路由查询的系统。它提供了一个聊天界面，用户可以与AI模型交互，应用程序会自动为每个查询选择最合适的模型。

### 功能特性
- 与AI模型交互的聊天界面
- 使用RouteLLM自动选择模型
- 利用GPT-4和Meta-Llama 3.1模型
- 显示包含模型信息的聊天历史

### 如何开始？

1. 克隆GitHub仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/advanced_tools_frameworks/llm_router_app
```
2. 安装所需依赖：

```bash
pip install -r requirements.txt
```
3. 设置您的API密钥：

```bash
os.environ["OPENAI_API_KEY"] = "your_openai_api_key"
os.environ['TOGETHERAI_API_KEY'] = "your_togetherai_api_key"
```
注意：在生产环境中，建议使用环境变量或安全的配置管理系统，而不是硬编码API密钥。

4. 运行Streamlit应用
```bash
streamlit run llm_router.py
```

### 工作原理？

1. RouteLLM初始化：应用程序使用两个模型初始化RouteLLM控制器：
    - 强模型：GPT-4（mini）
    - 弱模型：Meta-Llama 3.1 70B Instruct Turbo

2. 聊天界面：用户可以通过聊天界面输入消息。

3. 模型选择：RouteLLM根据用户查询的复杂性自动选择合适的模型。

4. 响应生成：选定的模型生成对用户输入的响应。

5. 显示：应用程序显示响应以及使用的模型信息。

6. 历史记录：维护并显示聊天历史，包括每个响应的模型信息。