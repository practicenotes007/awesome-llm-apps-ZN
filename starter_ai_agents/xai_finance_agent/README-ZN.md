## 📊 使用xAI Grok的AI金融代理
该应用程序创建了一个由xAI的Grok模型驱动的金融分析代理，将实时股票数据与网络搜索功能相结合。它通过交互式演练场界面提供结构化的金融见解。

### 功能特性

- 由xAI的Grok-beta模型驱动
- 通过YFinance进行实时股票数据分析
- 通过DuckDuckGo进行网络搜索功能
- 带表格的格式化金融数据输出
- 交互式演练场界面

### 如何开始？

1. 克隆GitHub仓库
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/ai_agent_tutorials/xai_finance_agent
```

2. 安装所需依赖项：

```bash
cd awesome-llm-apps/ai_agent_tutorials/xai_finance_agent
pip install -r requirements.txt
```

3. 获取您的OpenAI API密钥

- 注册[xAI API账户](https://console.x.ai/)
- 设置您的XAI_API_KEY环境变量。
```bash
export XAI_API_KEY='your-api-key-here'
```

4. 运行AI代理团队
```bash
python xai_finance_agent.py
```

5. 打开您的网络浏览器并导航到控制台输出中提供的URL，通过演练场界面与AI金融代理交互。