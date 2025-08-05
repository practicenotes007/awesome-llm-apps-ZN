# 基于 OpenAI Agents SDK 和 Firecrawl 的深度研究代理

一个强大的研究助手，利用 OpenAI 的 Agents SDK 和 Firecrawl 的深度研究功能，对任何主题和问题进行全面的网络研究。

## 功能特性

- **深度网络研究**：自动搜索网络、提取内容并综合研究发现
- **增强分析**：使用 OpenAI 的 Agents SDK 对研究结果进行拓展，补充额外背景和洞察
- **交互式用户界面**：采用简洁的 Streamlit 界面，便于用户交互
- **可下载报告**：将研究成果导出为 Markdown 文件

## 工作原理

1. **输入阶段**：用户提供研究主题及 API 凭据
2. **研究阶段**：工具使用 Firecrawl 搜索网络并提取相关信息
3. **分析阶段**：基于研究结果生成初步研究报告
4. **增强阶段**：第二个代理对初始报告进行深化，增加深度和上下文信息
5. **输出阶段**：向用户展示增强后的报告，并提供下载功能

## 系统要求

- Python 3.8+
- OpenAI API 密钥
- Firecrawl API 密钥
- 所需的 Python 包（详见 `requirements.txt`）

## 安装步骤

1. 克隆此仓库：
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd advanced_ai_agents/single_agent_apps/ai_deep_research_agent
   ```

2. 安装所需包：
   ```bash
   pip install -r requirements.txt
   ```

## 使用方法

1. 运行 Streamlit 应用：
   ```bash
   streamlit run deep_research_openai.py
   ```

2. 在侧边栏中输入您的 API 密钥：
   - OpenAI API 密钥
   - Firecrawl API 密钥

3. 在主输入框中输入您的研究主题

4. 点击 "Start Research" 并等待流程完成

5. 查看并下载您的增强研究报告

## 示例研究主题

- "量子计算的最新发展"
- "气候变化对海洋生态系统的影响"
- "可再生能源存储技术的进步"
- "人工智能中的伦理考量"
- "远程工作技术的新兴趋势"

## 技术细节

该应用使用两个专业代理：

1. **研究代理**：利用 Firecrawl 的深度研究接口，从多个网络来源收集全面信息。

2. **拓展代理**：通过添加详细解释、示例、案例研究和实际影响，增强初始研究报告。

Firecrawl 深度研究工具通过多轮次的网络搜索、内容提取和分析，确保对研究主题进行全面覆盖。