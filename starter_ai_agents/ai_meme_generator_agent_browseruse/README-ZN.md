# 🥸 AI表情包生成代理 - 浏览器使用

AI表情包生成代理是一个强大的浏览器自动化工具，使用AI代理创建表情包。该应用将多LLM功能与自动化浏览器交互相结合，通过直接网站操作基于文本提示生成表情包。

## 功能特性

- **多LLM支持**
  - Claude 3.5 Sonnet (Anthropic)
  - GPT-4o (OpenAI)
  - Deepseek v3 (Deepseek)
  - 带API密钥验证的自动模型切换

- **浏览器自动化**：
  - 直接与imgflip.com表情包模板交互
  - 自动搜索相关表情包格式
  - 顶部/底部标题的动态文本插入
  - 从生成的表情包中提取图像链接

- **智能生成工作流**：
  - 从提示中提取动作动词
  - 隐喻模板匹配
  - 多步骤质量验证
  - 生成失败的自动重试机制

- **用户友好界面**：
  - 模型配置侧边栏
  - API密钥管理
  - 带可点击链接的直接表情包预览
  - 响应式错误处理

需要API密钥：
- **Anthropic** (用于Claude)
- **Deepseek** 
- **OpenAI** (用于GPT-4o)

## 运行方法

1. **克隆仓库**：
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd ai_agent_tutorials/ai_meme_generator_browseruse
   ```
2. **安装依赖项**：
    ```bash
    pip install -r requirements.txt
    ```
    如需要，安装`playwright`。
    ```bash
    python -m playwright install --with-deps
    ```
3. **运行Streamlit应用**：
    ```bash
    streamlit run ai_meme_generator_agent.py

    ```