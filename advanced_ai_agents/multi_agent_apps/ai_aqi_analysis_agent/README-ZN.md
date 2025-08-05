# 🌍 AQI分析代理

AQI分析代理是一个由Firecrawl和Agno的AI代理框架驱动的强大空气质量监测和健康建议工具。该应用通过分析实时空气质量数据并提供个性化健康建议，帮助用户就户外活动做出明智决策。

## 功能特性

- **多代理系统**
    - **AQI分析器**：获取并处理实时空气质量数据
    - **健康建议代理**：生成个性化健康建议

- **空气质量指标**：
  - 整体空气质量指数(AQI)
  - 颗粒物(PM2.5和PM10)
  - 一氧化碳(CO)浓度
  - 温度
  - 湿度
  - 风速

- **全面分析**：
  - 实时数据可视化
  - 健康影响评估
  - 活动安全建议
  - 户外活动最佳时间建议
  - 天气条件关联性

- **交互功能**：
  - 基于位置的分析
  - 医疗状况考虑
  - 特定活动建议
  - 可下载报告
  - 示例查询用于快速测试

## 如何运行

按照以下步骤设置和运行应用程序：

1. **克隆仓库**：
   ```bash
   git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
   cd ai_agent_tutorials/ai_aqi_analysis_agent
   ```

2. **安装依赖**：
    ```bash
    pip install -r requirements.txt
    ```

3. **设置您的API密钥**：
    - 从以下位置获取OpenAI API密钥：https://platform.openai.com/api-keys
    - 从以下位置获取Firecrawl API密钥：[Firecrawl网站](https://www.firecrawl.dev/app/api-keys)

4. **运行Gradio应用**：
    ```bash
    python ai_aqi_analysis_agent.py
    ```

5. **访问Web界面**：
    - 终端将显示两个URL：
      - 本地URL：`http://127.0.0.1:7860`（用于本地访问）
      - 公共URL：`https://xxx-xxx-xxx.gradio.live`（用于临时公共访问）
    - 点击任一URL在浏览器中打开Web界面

## 使用方法

1. 在API配置部分输入您的API密钥
2. 输入位置详情：
   - 城市名称
   - 州（对于联邦属地/美国城市可选）
   - 国家
3. 提供个人信息：
   - 医疗状况（可选）
   - 计划的户外活动
4. 点击"Analyze & Get Recommendations"接收：
   - 当前空气质量数据
   - 健康影响分析
   - 活动安全建议
5. 尝试示例查询进行快速测试

## 注意事项

空气质量数据是使用Firecrawl的网络爬虫功能获取的。由于缓存和速率限制，数据可能并不总是与网站上的实时值匹配。要获得最准确的实时数据，请考虑直接查看源网站。