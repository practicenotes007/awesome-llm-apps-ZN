## 📨 与Gmail收件箱聊天

只需30行Python代码即可实现的带RAG功能的LLM应用，可以与Gmail进行聊天。该应用使用检索增强生成（RAG）技术，基于您的Gmail收件箱内容提供准确的答案。

### 功能特性

- 连接到您的Gmail收件箱
- 就您邮件的内容提出问题
- 使用RAG和所选LLM获得准确答案

### 安装步骤

1. 克隆仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd advanced_llm_apps/chat_with_X_tutorials/chat_with_gmail
```
2. 安装所需依赖

```bash
pip install -r requirements.txt
```

3. 设置您的Google Cloud项目并启用Gmail API：

- 访问[Google Cloud Console](https://console.cloud.google.com/)并创建一个新项目。
- 导航到"APIs & Services > OAuth consent screen"并配置OAuth同意屏幕。
- 通过提供必要的应用信息发布OAuth同意屏幕。
- 启用Gmail API并创建OAuth客户端ID凭证。
- 以JSON格式下载凭证并将其保存为工作目录中的`credentials.json`。

4. 获取您的OpenAI API密钥

- 注册[OpenAI账户](https://platform.openai.com/)（或您选择的LLM提供商）并获取您的API密钥。

4. 运行Streamlit应用

```bash
streamlit run chat_gmail.py
```