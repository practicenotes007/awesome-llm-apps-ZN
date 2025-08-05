## 🦙💬 使用Llama-3构建的ChatGPT克隆
本项目演示了如何使用在您计算机上本地运行的Llama-3模型构建ChatGPT克隆。该应用程序使用Python和Streamlit构建，为与语言模型交互提供了用户友好的界面。最重要的是，它是100%免费的，不需要互联网连接！

### 功能特性
- 在您的计算机上本地运行，无需互联网连接，完全免费使用。
- 利用Llama-3 instruct模型生成响应
- 提供类似聊天的界面以实现无缝交互

### 如何开始？

1. 克隆GitHub仓库

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/advanced_tools_frameworks/local_chatgpt_clone
```
2. 安装所需依赖：

```bash
pip install -r requirements.txt
```
3. 下载并安装[LM Studio桌面应用](https://lmstudio.ai/)。下载Llama-3 instruct模型。

4. 通过在LM Studio中启动服务器，将Llama-3模型作为OpenAI API暴露。观看此[视频演练](https://x.com/Saboo_Shubham_/status/1783715814790549683)。

5. 运行Streamlit应用
```bash
streamlit run chatgpt_clone_llama3.py
```