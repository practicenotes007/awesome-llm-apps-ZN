# 💻 带o3-mini和Gemini的多模态AI编码代理团队
一个由多个基于新o3-mini模型构建的代理驱动的AI动力Streamlit应用程序，可作为您的个人编码助手。您还可以上传编码问题的图像或用文本描述，AI代理将分析、生成最优解决方案并在沙箱环境中执行。

## 功能特性
#### 多模态问题输入
- 上传编码问题的图像（支持PNG、JPG、JPEG）
- 用自然语言输入问题
- 从图像中自动提取问题
- 交互式问题处理

#### 智能代码生成
- 生成具有最佳时间和空间复杂度的最优解决方案
- 输出干净、有文档的Python代码
- 类型提示和适当文档
- 边界情况处理

#### 安全代码执行
- 沙箱代码执行环境
- 实时执行结果
- 错误处理和解释
- 30秒执行超时保护

#### 多代理架构
- 用于图像处理的视觉代理（Gemini-2.0-flash）
- 用于解决方案生成的编码代理（OpenAI-o3-mini）
- 用于代码运行和结果分析的执行代理（OpenAI）
- 用于安全代码执行的E2B沙箱

## 如何运行

按照以下步骤设置和运行应用程序：
- 从以下位置获取OpenAI API密钥：https://platform.openai.com/
- 从以下位置获取Google（Gemini）API密钥：https://makersuite.google.com/app/apikey
- 从以下位置获取E2B API密钥：https://e2b.dev/docs/getting-started/api-key

1. **克隆仓库**
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd advanced_ai_agents/multi_agent_apps/agent_teams/multimodal_coding_agent_team
   ```

2. **安装依赖**
    ```bash
    pip install -r requirements.txt
    ```

3. **运行Streamlit应用**
    ```bash
    streamlit run ai_coding_agent_o3.py
    ```

4. **配置API密钥**
   - 在侧边栏输入您的API密钥
   - 完整功能需要全部三个密钥（OpenAI、Gemini、E2B）

## 使用方法
1. 上传编码问题的图像或输入您的问题描述
2. 点击"Generate & Execute Solution"
3. 查看生成的带完整文档的解决方案
4. 查看执行结果和任何生成的文件
5. 查看任何错误消息或执行超时