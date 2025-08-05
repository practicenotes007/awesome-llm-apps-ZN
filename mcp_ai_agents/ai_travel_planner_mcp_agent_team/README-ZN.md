## 🌍 AI旅行规划MCP代理

这是一个基于Streamlit的应用程序，使用AI帮助用户规划旅行行程。该应用集成了各种MCP服务器，提供全面的旅行规划体验，包括天气预报、地图和日历集成。

## 功能特性

### MCP服务器集成

本项目利用多个MCP（模型上下文协议）服务器提供全面的旅行规划体验：

### 1. 天气MCP服务器
- **功能**：提供实时天气数据和预报

### 2. 地图MCP服务器
- **功能**：处理基于位置的服务和导航
- **特性**：
  - 搜索地点和兴趣点
  - 获取详细的地点信息
  - 获取驾驶/步行路线

### 3. 日历MCP服务器
- **功能**：管理日历事件和日程安排
- **特性**：
  - 创建和管理日历事件
  - 处理时区转换
  - 安排提醒和通知
- **集成**：在`calendar_mcp.py`中实现

### 4. 预订MCP服务器
- **功能**：使用Airbnb MCP服务器

## 设置

### 要求

1. **API密钥和凭据**：
    - **Google Maps API密钥**：从Google Cloud Console设置Google Maps API密钥
    - **Google Calendar API**：启用并配置日历API密钥
    - **Google OAuth凭据**：用于身份验证的客户端ID、客户端密钥和刷新令牌
    - **AccuWeather API密钥**：从https://developer.accuweather.com/获取AccuWeather API密钥
    - **OpenAI API密钥**：在OpenAI注册以获取您的API密钥。

2. **Python 3.8+**：确保您已安装Python 3.8或更高版本。

### 安装

1. 克隆此仓库：
   ```bash
   git clone https://github.com/yourusername/ai_travel_planner_mcp_agent_team
   cd ai_travel_planner_mcp_agent_team
   ```

2. 安装所需的Python包：
   ```bash
   pip install -r requirements.txt
   ```

3. 设置环境变量：
   在项目根目录中创建一个`.env`文件，包含以下变量：
   ```
   GOOGLE_CLIENT_ID=
   GOOGLE_CLIENT_SECRET=
   GOOGLE_REFRESH_TOKEN=
   GOOGLE_MAPS_API_KEY=
   OPENAI_API_KEY=
   ACCUWEATHER_API_KEY=
   ```

### 运行应用

1. 为Google日历生成OAuth令牌

2. 启动Streamlit应用：
   ```bash
   streamlit run app.py
   ```

3. 在应用界面中：
   - 使用侧边栏配置您的偏好
   - 输入您的旅行详情

## 项目结构

- `app.py`：主Streamlit应用程序
- `calendar_mcp.py`：日历MCP集成功能
- `requirements.txt`：项目依赖
- `.env`：环境变量

## 日历MCP集成

`calendar_mcp.py`模块通过MCP（模型上下文协议）框架与Google日历无缝集成。此集成允许旅行规划器：

- **创建事件**：自动为旅行活动、航班和住宿创建日历事件
- **日程管理**：处理时区转换和日程冲突
- **事件详情**：包含全面的事件信息，例如：
  - 带有Google地图链接的位置详情
  - 事件时间的天气预报
  - 旅行时间和交通详情
  - 备注和提醒

### 日历设置

1. **OAuth身份验证**：
   - 应用程序使用OAuth 2.0与Google日历进行安全身份验证
   - 首次设置需要生成刷新令牌
   - 刷新令牌安全地存储在`.env`文件中

2. **事件创建**：
   ```python
   # 创建日历事件的示例
   event = {
       'summary': '飞往巴黎的航班',
       'location': '戴高乐机场',
       'description': '航班详情和天气预报',
       'start': {'dateTime': '2024-04-20T10:00:00', 'timeZone': 'Europe/Paris'},
       'end': {'dateTime': '2024-04-20T12:00:00', 'timeZone': 'Europe/Paris'}
   }
   ```