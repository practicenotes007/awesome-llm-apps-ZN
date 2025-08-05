## 📝 与Substack新闻通讯聊天
Streamlit应用，允许您使用OpenAI的API和Embedchain库与Substack新闻通讯进行聊天。该应用利用GPT-4根据指定的Substack新闻通讯内容提供准确的答案。

## 功能特性
- 输入Substack博客URL
- 就Substack新闻通讯的内容提出问题
- 使用OpenAI的API和Embedchain获得准确答案

### 如何开始？

1. 克隆GitHub仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/chat_with_X_tutorials/chat_with_substack
```
2. 安装所需依赖：

```bash
pip install -r requirements.txt
```
3. 获取您的OpenAI API密钥

- 注册[OpenAI账户](https://platform.openai.com/)（或您选择的LLM提供商）并获取您的API密钥。

4. 运行Streamlit应用
```bash
streamlit run chat_substack.py
```