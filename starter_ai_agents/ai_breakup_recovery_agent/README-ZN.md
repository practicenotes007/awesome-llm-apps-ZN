# 💔 分手恢复代理团队

这是一个AI驱动的应用程序，旨在通过提供支持、指导和来自专业AI代理团队的情感出口信息，帮助用户从分手中情感恢复。该应用使用**Streamlit**和**Agno**构建，利用**Gemini 2.0 Flash（Google视觉模型）**。

## 🚀 功能特性

- 🧠 **多代理团队：** 
    - **治疗师代理：** 提供共情支持和应对策略。
    - **释怀代理：** 编写用户不应发送的情感信息以达到宣泄效果。
    - **日常规划代理：** 建议情感恢复的日常安排。
    - **直率代理：** 对分手提供直接、不含糊的反馈。
- 📷 **聊天截图分析：**
    - 上传截图进行聊天分析。
- 🔑 **API密钥管理：**
    - 通过Streamlit的侧边栏安全存储和管理您的Gemini API密钥。
- ⚡ **并行执行：** 
    - 代理以协调模式处理输入以获得全面结果。
- ✅ **用户友好界面：** 
    - 简单直观的UI，便于交互和显示代理响应。

---

## 🛠️ 技术栈

- **前端：** Streamlit（Python）
- **AI模型：** Gemini 2.0 Flash（Google视觉模型）
- **图像处理：** PIL（用于显示截图）
- **文本提取：** Google的Gemini视觉模型分析聊天截图
- **环境变量：** 在Streamlit中使用`st.session_state`管理API密钥

---

## 📦 安装

1. **克隆仓库：**
   ```bash
   git clone <repository_url>
   cd breakup-recovery-agent-team
   ```

2. **创建虚拟环境（可选但推荐）：**
   ```bash
   conda create --name <env_name> python=<version>
   conda activate <env_name>
   ```

3. **安装依赖项：**
   ```bash
   pip install -r requirements.txt
   ```

4. **运行Streamlit应用：**
   ```bash
   streamlit run app.py
   ```

---

## 🔑 环境变量

确保在Streamlit侧边栏中提供您的**Gemini API密钥**：

- GEMINI_API_KEY=your_google_gemini_api_key

---

## 🛠️ 使用方法

1. **输入您的感受：** 
    - 在文本区域描述您的感受。
2. **上传截图（可选）：**
    - 上传聊天截图（PNG、JPG、JPEG）进行分析。
3. **执行代理：**
    - 点击**"Get Recovery Support"**运行多代理团队。
4. **查看结果：**
    - 显示各个代理的响应。
    - 团队领导提供最终摘要。

---

## 🧑‍💻 代理概述

- **治疗师代理**
    - 提供共情支持和应对策略。
    - 使用**Gemini 2.0 Flash（Google视觉模型）**和DuckDuckGo工具获取洞察。
  
- **释怀代理**
    - 生成未发送的情感信息以达到情感释放。
    - 确保信息真诚感人。

- **日常规划代理**
    - 创建包含平衡活动的日常恢复计划。
    - 包括自我反思、社交互动和健康的消遣。

- **直率代理**
    - 对分手提供直接、客观的反馈。
    - 使用事实性语言，不含糖衣。

---

## 📄 许可证

本项目根据**MIT许可证**授权。

---