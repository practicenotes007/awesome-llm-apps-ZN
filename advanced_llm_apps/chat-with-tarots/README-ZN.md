# ✨ 魔术师IA读卡器：AI驱动的自然语言处理和塔罗牌洞察 ✨

欢迎来到**魔术师IA读卡器**！这个项目展示了一个独特的应用程序，将人工智能的力量与塔罗牌阅读的神秘魅力结合起来。

![TheMagicianDemo](https://github.com/maurizioorani/TheMagician-IA-Reader/blob/main/data/readme/TheMagicianAI.gif)

**它的功能：**

这个应用程序作为一个AI驱动的塔罗牌读卡器。它接收自然语言输入，并使用由传统塔罗牌含义引导的AI模型提供解释性洞察。

**主要功能：**

* **自然语言支持：** 理解并以自然语言交互（当前配置为英语）。
* **本地AI模型('phi4')：** 在高效的'phi4'模型上运行，非常适合本地处理和隐私保护。
* **CSV驱动的知识库：** 利用结构化CSV文件存储和引用详细的塔罗牌含义和象征意义（当前使用包含英语内容的`data/tarots.csv`）。
* **深度洞察：** 将原始文本查询转换为基于塔罗牌象征意义的有意义、符合上下文的解释。

**工作原理：**

魔术师IA读卡器的核心在于使用本地'phi4'AI模型。该模型通过包含每张塔罗牌解释的CSV文件中的综合数据进行微调或提示。当用户提供文本输入时，应用程序通过AI处理，然后生成由塔罗牌含义启发的响应。

**为什么使用它？**

* **研究人员和开发者：** 探索本地AI模型在自然语言理解和生成方面的能力。
* **AI爱好者：** 在独特领域中体验AI的实际应用。
* **好奇的用户：** 以创新的方式与AI交互以获得个人洞察。

通过魔术师IA读卡器进入AI与直觉相遇的世界！

---

## ⚙️ 安装

### 先决条件

- **Python 3.8或更高版本**
- **pip** – Python包安装器
- **Ollama** – 本地运行：
  安装地址：https://ollama.com/
  ```bash
  ollama pull phi4
  ollama serve
  ```
  
### 步骤

1. **克隆仓库**

   ```bash
   git clone https://github.com/maurizioorani/TheMagician-IA-Reader.git
   cd TheMagician-IA-Reader
   ```

2. **设置虚拟环境（推荐）**

```bash
# 在Unix/macOS上：
python -m venv venv
source venv/bin/activate


# 在Windows上：
python -m venv venv
venv\Scripts\activate
```

# 前端（Streamlit）：
首先，安装所有依赖项
```bash
pip install -r requirements.txt
```

运行应用程序

```bash
streamlit run app.py
```
Streamlit界面通常在http://localhost:8501可用。

## 📖 使用方法
访问应用程序：打开浏览器并导航到Streamlit提供的URL（通常是http://localhost:8501）。

输入您的文本数据：使用直观的界面粘贴、输入或上传您需要解答的问题。

选择阅读需要3、5或7张牌。

阅读洞察：查看详细分析和可视化，揭示抽取牌的含义。

## 🤝 贡献
欢迎贡献！如果您有改进或新功能要添加，请：

派生仓库。

为您的更改创建新分支。

提交带有清晰修改描述的拉取请求。

对于重大更改，请在实施前通过问题讨论。