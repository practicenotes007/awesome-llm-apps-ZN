<div align="center">

  <h1>🪟 Windows使用自主代理</h1>

  <a href="https://github.com/CursorTouch/windows-use/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/license-MIT-green" alt="许可证">
  </a>
  <img src="https://img.shields.io/badge/python-3.12%2B-blue" alt="Python">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%20%7C%2011-blue" alt="平台">
  <br>

  <a href="https://x.com/CursorTouch">
    <img src="https://img.shields.io/badge/follow-%40CursorTouch-1DA1F2?logo=twitter&style=flat" alt="在Twitter上关注">
  </a>
  <a href="https://discord.com/invite/Aue9Yj2VzS">
    <img src="https://img.shields.io/badge/Join%20on-Discord-5865F2?logo=discord&logoColor=white&style=flat" alt="加入我们的Discord">
  </a>

</div>

<br>

**Windows-Use**是一个强大的自动化代理，可以直接在GUI层与Windows交互。它弥合了AI代理和Windows操作系统之间的差距，执行诸如打开应用程序、点击按钮、输入文本、执行shell命令和捕获UI状态等任务，而无需依赖传统的计算机视觉模型。使任何LLM都能执行计算机自动化，而不是依赖特定模型。

## 🛠️安装指南

### **先决条件**

- Python 3.12或更高版本
- [UV](https://github.com/astral-sh/uv)（或`pip`）
- Windows 10或11

### **安装步骤**

**使用`uv`安装：**

```bash
uv pip install windows-use
````

或者使用pip：

```bash
pip install windows-use
```

## ⚙️基本用法

```python
# main.py
from langchain_google_genai import ChatGoogleGenerativeAI
from windows_use.agent import Agent
from dotenv import load_dotenv

load_dotenv()

llm=ChatGoogleGenerativeAI(model='gemini-2.0-flash')
agent = Agent(llm=llm,use_vision=True)
query=input("输入您的查询：")
agent_result=agent.invoke(query=query)
print(agent_result.content)
```

## 🤖运行代理

您可以使用以下命令从脚本运行：

```bash
python main.py
Enter your query: <您的任务>
```

---

## 🎥演示

**提示：**写一篇关于LLM的简短笔记并保存到桌面

<https://github.com/user-attachments/assets/0faa5179-73c1-4547-b9e6-2875496b12a0>

**提示：**从深色模式更改为浅色模式

<https://github.com/user-attachments/assets/47bdd166-1261-4155-8890-1b2189c0a3fd>

## 愿景

与您的计算机对话。看着它完成任务。

## 路线图

### 🤖代理智能

* [ ] **集成记忆**：允许代理记住用户过去的交互。
* [ ] **优化令牌使用**：实施Ally Tree压缩和提示工程等策略以减少开销。
* [ ] **模拟高级类人输入**：在应用程序中实现准确和自然的鼠标和键盘交互。
* [ ] **支持本地LLM**：接近云API性能的本地模型（例如，Mistral、LLaMA等）。
* [ ] **改进推理和规划**：增强代理分解和排序复杂任务的能力。

### 🌳Ally Tree优化

* [ ] **改进UI元素检测**：自动识别和优先处理屏幕上的基本交互组件。

* [ ] **智能压缩Ally Tree**：通过修剪不相关的分支来降低复杂性。
* [ ] **上下文感知优先级**：根据与手头任务的相关性对UI元素进行排名。

### 💡用户体验

* [ ] **减少延迟**：优化以改善GUI交互之间的响应时间。
* [ ] **优化命令界面**：通过简化的UX层使编写、说话或输入命令变得更加容易。
* [ ] **更好的错误处理和恢复**：确保优雅地处理边缘情况和不明确的指令。

### 🧪评估

* [ ] **LLM评估基准**—跟踪不同模型和基准的性能。

## ⚠️注意事项

代理直接在GUI层与您的Windows操作系统交互以执行操作。虽然代理被设计为智能和安全地操作，但它可能会犯错误，这可能会带来不良的系统行为或导致意外更改。尝试在沙箱环境中运行代理。

## 🪪许可证

该项目根据MIT许可证授权—详见[LICENSE](LICENSE)文件了解详情。

## 🤝贡献

欢迎贡献！请查看[CONTRIBUTING](CONTRIBUTING)文件了解设置和开发工作流程。

由[Jeomon George](https://github.com/Jeomon)用❤️制作

---

## 引用

```bibtex
@software{
  author       = {George, Jeomon},
  title        = {Windows-Use: Enable AI to control Windows OS},
  year         = {2025},
  publisher    = {GitHub},
  url={https://github.com/CursorTouch/Windows-Use}
}
```