## 💲 带网络访问功能的AI金融代理团队
这个脚本演示了如何用仅20行Python代码构建一个作为金融分析师协作的AI代理团队。该系统结合了网络搜索功能和金融数据分析工具，以提供全面的金融见解。

### 功能特性
- 具有专门角色的多代理系统：
    - 用于一般网络研究的网络代理
    - 用于详细金融分析的金融代理
    - 用于代理间协调的团队代理
- 通过YFinance访问实时金融数据
- 使用DuckDuckGo的网络搜索功能
- 使用SQLite持久化存储代理交互

### 如何开始？

1. 克隆GitHub仓库
```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd advanced_ai_agents/multi_agent_apps/agent_teams/ai_finance_agent_team
```

2. 安装所需依赖：

```bash
pip install -r requirements.txt
```

3. 获取您的OpenAI API密钥

- 注册[OpenAI账户](https://platform.openai.com/)（或您选择的LLM提供商）并获取您的API密钥。
- 将您的OpenAI API密钥设置为环境变量：
```bash
export OPENAI_API_KEY='your-api-key-here'
```

4. 运行AI代理团队
```bash
python3 finance_agent_team.py
```

5. 打开您的网络浏览器并导航到控制台输出中提供的URL，通过游乐场界面与AI代理团队交互。