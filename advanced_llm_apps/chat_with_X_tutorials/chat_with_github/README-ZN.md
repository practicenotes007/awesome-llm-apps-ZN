## 💬 与GitHub仓库聊天

只需30行Python代码即可实现的带RAG功能的LLM应用，可以与GitHub仓库进行聊天。该应用使用检索增强生成（RAG）技术，基于指定的GitHub仓库内容提供准确的答案。

### 功能特性

- 提供GitHub仓库名称作为输入
- 就GitHub仓库的内容提出问题
- 使用OpenAI的API和Embedchain获得准确答案

### 如何开始？

1. 克隆GitHub仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd advanced_llm_apps/chat_with_X_tutorials/chat_with_github
```
2. 安装所需依赖：

```bash
pip install -r requirements.txt
```
3. 获取您的OpenAI API密钥

- 注册[OpenAI账户](https://platform.openai.com/)（或您选择的LLM提供商）并获取您的API密钥。

4. 获取您的GitHub访问令牌

- 创建一个[个人访问令牌](https://docs.github.com/en/enterprise-server@3.6/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token)，并授予访问目标GitHub仓库所需的权限。

4. 运行Streamlit应用
```bash
streamlit run chat_github.py
```

### 工作原理？

- 应用会提示用户输入OpenAI API密钥，用于验证对OpenAI API的请求。

- 它初始化Embedchain App类的一个实例和一个带有提供的GitHub访问令牌的GithubLoader。

- 用户被提示输入GitHub仓库URL，然后使用GithubLoader将其添加到Embedchain应用的知识库中。

- 用户可以使用文本输入就GitHub仓库提出问题。

- 当提出问题时，应用使用Embedchain应用的聊天方法基于GitHub仓库的内容生成答案。

- 应用向用户显示生成的答案。