# 多模态AI设计代理团队

一个Streamlit应用程序，使用由Google的Gemini模型驱动的专业AI代理团队提供全面的设计分析。

该应用程序利用多个专业AI代理提供产品和竞争对手UI/UX设计的全面分析，结合视觉理解、用户体验评估和市场研究见解。

## 功能特性

- **专业法律AI代理团队**

   - 🎨 **视觉设计代理**：评估设计元素、图案、配色方案、字体和视觉层次
   - 🔄 **用户体验分析代理**：评估用户流程、交互模式、可用性和可访问性
   - 📊 **市场分析代理**：提供市场见解、竞争对手分析和定位建议
   
- **多种分析类型**：从视觉设计、用户体验和市场分析中选择
- **对比分析**：上传竞争对手设计以获得对比见解
- **可定制关注领域**：选择特定方面进行详细分析
- **上下文感知**：提供额外上下文以获得更相关的见解
- **实时处理**：通过进度指示器获得即时分析
- **结构化输出**：接收组织良好、可操作的见解

## 如何运行

1. **设置环境**
   ```bash
   # 克隆仓库
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd advanced_ai_agents/multi_agent_apps/agent_teams/multimodal_design_agent_team

   # 创建并激活虚拟环境（可选）
   python -m venv venv
   source venv/bin/activate  # 在Windows上：venv\Scripts\activate

   # 安装依赖
   pip install -r requirements.txt
   ```

2. **获取API密钥**
   - 访问[Google AI Studio](https://aistudio.google.com/apikey)
   - 生成API密钥

3. **运行应用程序**
   ```bash
   streamlit run design_agent_team.py
   ```

4. **使用应用程序**
   - 在侧边栏输入您的Gemini API密钥
   - 上传设计文件（支持格式：JPG、JPEG、PNG）
   - 选择分析类型和关注领域
   - 如需要添加上下文
   - 点击"Run Analysis"获得见解

## 技术栈

- **前端**：Streamlit
- **AI模型**：Google Gemini 2.0
- **图像处理**：Pillow
- **市场研究**：DuckDuckGo搜索API
- **框架**：用于代理编排的Phidata

## 获得最佳结果的提示

- 上传清晰、高分辨率的图像
- 包含多个视图/屏幕以获得更好的上下文
- 添加竞争对手设计以进行对比分析
- 提供关于目标受众的特定上下文