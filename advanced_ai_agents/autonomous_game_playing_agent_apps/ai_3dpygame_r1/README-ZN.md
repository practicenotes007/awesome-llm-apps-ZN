# 🎮 带DeepSeek R1的AI 3D PyGame可视化器
这个项目展示了R1的代码能力，包括PyGame代码生成器和带浏览器使用的可视化器。该系统使用DeepSeek进行推理，OpenAI进行代码提取，以及浏览器自动化代理在Trinket.io上可视化代码。

### 功能特性

- 从自然语言描述生成PyGame代码
- 使用DeepSeek Reasoner进行代码逻辑和解释
- 使用OpenAI GPT-4o提取干净代码
- 使用浏览器代理在Trinket.io上自动化代码可视化
- 提供简化的Streamlit界面
- 多代理系统处理不同任务（导航、编码、执行、查看）

### 如何开始？

1. 克隆GitHub仓库
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/ai_agent_tutorials/ai_3dpygame_r1
```

2. 安装所需依赖：
```bash
pip install -r requirements.txt
```

3. 获取您的API密钥
- 注册[DeepSeek](https://platform.deepseek.com/)并获取您的API密钥
- 注册[OpenAI](https://platform.openai.com/)并获取您的API密钥

4. 运行AI PyGame可视化器
```bash
streamlit run ai_3dpygame_r1.py
```

5. 浏览器使用会自动打开您的网络浏览器并导航到控制台输出中提供的URL以与PyGame生成器交互。

### 工作原理？

1. **查询处理：** 用户输入所需PyGame可视化的自然语言描述。
2. **代码生成：** 
   - DeepSeek Reasoner分析查询并提供详细的推理和代码
   - OpenAI代理从推理中提取干净、可执行的代码
3. **可视化：**
   - 浏览器代理自动化在Trinket.io上运行代码的过程
   - 多个专业代理处理不同任务：
     - 导航到Trinket.io
     - 代码输入
     - 执行
     - 可视化查看
4. **用户界面：** Streamlit为输入查询、查看代码和管理可视化过程提供直观界面。