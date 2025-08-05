# 🦉 Beifong：您的无垃圾、个性化信息和播客

![image](https://github.com/user-attachments/assets/b2f24f12-6f80-46fa-aa31-ee42e17765b1)

Beifong管理您信任的文章和社交媒体平台来源。它从您信任和策划的内容生成播客。它处理从数据收集和分析到脚本和视觉制作的完整流程。

▶️ [观看演示视频高清版](https://www.canva.com/design/DAGoUfv8ICM/Oj-vJ19AvZYDa2SwJrCWKw/watch?utm_content=D[…]share&utm_medium=link2&utm_source=uniquelinks&utlId=h2508379667)

▶️ [在YouTube上观看演示](https://youtu.be/dB8FZY3x9EY)

🔗 [博客](https://arun477.github.io/posts/beifong_podcast_generator/)

## 目录

- [入门指南](#getting-started)
  - [系统要求](#system-requirements)
  - [初始设置和安装](#initial-setup-and-installation)
  - [环境配置](#environment-configuration)
  - [启动应用程序](#starting-the-application)
- [如何使用Beifong](#how-to-use-beifong)
  - [三种使用方法](#three-usage-methods)
- [内容处理系统](#content-processing-system)
  - [内置内容处理器](#built-in-content-processors)
  - [创建自定义内容处理器](#creating-custom-content-processors)
- [AI代理和工具](#ai-agent-and-tools)
  - [代理架构概述](#agent-architecture-overview)
  - [添加自定义工具](#adding-custom-tools)
  - [配置代理行为](#configuring-agent-behavior)
- [网络搜索和浏览器自动化](#web-search-and-browser-automation)
  - [搜索命令](#search-commands)
  - [社交媒体登录会话](#social-media-login-sessions)
  - [高级持久会话配置](#advanced-persistent-session-configuration)
- [社交媒体监控](#social-media-monitoring)
  - [支持的平台](#supported-platforms)
  - [设置计划的Feed收集](#setting-up-scheduled-feed-collection)
  - [查看AI洞察](#viewing-ai-insights)
  - [配置自定义Feed](#configuring-custom-feeds)
  - [添加新的社交媒体账户](#adding-new-social-media-accounts)
  - [计划最佳实践](#scheduling-best-practices)
- [音频和语音生成](#audio-and-voice-generation)
  - [支持的TTS引擎](#supported-tts-engines)
  - [添加新的语音引擎](#adding-new-voice-engines)
- [集成](#integrations)
  - [Slack集成](#slack-integration)
  - [设置Slack应用](#setting-up-slack-app)
  - [所需的Slack权限](#required-slack-permissions)
  - [环境配置](#environment-configuration-1)
  - [运行Slack集成](#running-slack-integration)
- [数据存储和文件管理](#data-storage-and-file-management)
  - [数据库存储](#database-storage)
  - [媒体资产存储](#media-asset-storage)
  - [管理存储增长](#managing-storage-growth)
- [部署和访问选项](#deployment-and-access-options)
  - [本地网络访问](#local-network-access)
  - [远程访问解决方案](#remote-access-solutions)
  - [安全性](#security)
- [云选项](#cloud-options)
  - [Beifong云功能](#beifong-cloud-features)
- [故障排除](#troubleshooting)
  - [Kokoro库安装问题](#kokoro-library-installation-issues)
  - [Browseruse安装问题](#browseruse-installation-issues)
  - [FAISS库安装问题](#faiss-library-installation-issues)
  - [基于浏览器的数据收集问题](#browser-based-data-collection-issues)
- [更新](#updates)

## 入门指南

### 系统要求

在安装Beifong之前，请确保您具备：

- Python 3.11+
- Redis服务器
- OpenAI API密钥
- (可选) ElevenLabs API密钥

### 初始设置和安装

```bash
# 克隆仓库
git clone https://github.com/arun477/beifong.git
cd beifong

# 创建虚拟环境
cd beifong
python -m venv venv
source venv/bin/activate

# 安装依赖
pip install -r requirements.txt

# 安装浏览器
python -m playwright install

# (可选但推荐) 下载演示内容
# 导航到beifong目录（如果尚未在该目录中）
cd beifong  # 如果已经在beifong文件夹中则跳过
# 这将用示例数据、策划的源Feed和资产填充系统
python bootstrap_demo.py
```

### 环境配置

在`/beifong`目录中创建一个`.env`文件，包含您的API密钥：

```
OPENAI_API_KEY=your_openai_api_key
ELEVENSLAB_API_KEY=your_elevenlabs_api_key  # 可选
REDIS_HOST=localhost
REDIS_PORT=6379
REDIS_DB=0
```

### 启动应用程序

在单独的终端中启动所有必需的服务（但请确保在启动其他服务之前先启动python main.py，因为首次运行将进行数据库初始化）：

⚠️ 在启动每个脚本之前，请确保在所有终端中激活虚拟环境。

```bash
source venv/bin/activate
```

```bash
# 终端1：启动主后端（首次运行可能需要2到3分钟，因为设置过程）
cd beifong
python main.py

# 终端2：启动调度器
cd beifong
python -m scheduler

# 终端3：启动聊天工作者
cd beifong
python -m celery_worker

# 验证Redis是否正在运行
redis-cli ping
```

#### 可选：前端开发模式

```bash
# 导航到web目录
cd web

# 安装依赖
npm install

# 启动开发服务器
npm start
```

## 如何使用Beifong

### 三种使用方法

Beifong提供了与系统交互的灵活性：

1. **交互式Web UI** - 用于内容管理和播客生成的Web界面
2. **API集成** - 用于自定义应用程序和工作流的编程访问
3. **自动化调度** - 设置重复任务以实现免手动的内容处理

## 内容处理系统

### 内置内容处理器

Beifong包含几个专门用于不同内容源的处理器：

- **RSS Feed处理器** - 监控RSS Feed以获取新文章和内容
- **URL内容处理器** - 从网页中提取和处理内容
- **AI内容分析器** - 对内容进行分类、总结和分析质量
- **向量嵌入处理器** - 为内容创建可搜索的向量表示
- **FAISS搜索索引器** - 构建用于内容发现的搜索索引
- **播客脚本生成器** - 从策划的内容创建完整的播客剧集
- **X.com社交处理器** - 爬取和处理您的X.com社交媒体Feed
- **Facebook社交处理器** - 爬取和处理您的Facebook社交媒体Feed

### 创建自定义内容处理器

通过添加自己的内容处理器来扩展Beifong的功能：

#### 步骤1：创建您的处理器模块

```python
# processors/my_custom_processor.py
def process_custom_task(parameter1=None, parameter2=None):
    # 您的处理逻辑在这里
    stats = {"processed": 0, "success": 0, "errors": 0}
    # 处理实现
    return stats

if __name__ == "__main__":
    stats = process_custom_task()
    print(f"Processed: {stats['processed']}, Success: {stats['success']}")
```

#### 步骤2：注册您的处理器

在`models/tasks_schemas.py`中将您的处理器添加到系统中：

```python
class TaskType(str, Enum):
    # 现有的任务类型...
    my_custom_processor = "my_custom_processor"

TASK_TYPES = {
    # 现有的类型...
    "my_custom_processor": {
        "name": "My Custom Processor",
        "command": "python -m processors.my_custom_processor",
        "description": "Performs custom processing task",
    },
}
```

#### 步骤3：部署您的处理器

使用API或UI创建一个新任务，使用您的自定义处理器类型。

## AI代理和工具

### 代理架构概述

Beifong的AI系统基于[agno](https://github.com/agno-agi/agno)框架构建，包括：

- **搜索工具** - 语义搜索、关键词搜索和基于浏览器的网络研究
- **内容生成工具** - 自动脚本写作、横幅创建和音频制作
- **持久会话状态** - 在交互中保持对话上下文
- **工具编排** - 自动管理多步骤工作流

### 添加自定义工具

通过自定义工具扩展代理的功能：

```python
# tools/my_custom_tool.py
from agno.agent import Agent

def my_custom_tool(agent: Agent, param1: str, param2: str) -> str:
    """工具描述在这里"""
    agent.session_state["my_key"] = "my_value"
    # 工具实现
    result = f"Processed {param1} and {param2}"
    return result
```

在`services/celery_tasks.py`中注册您的工具：

```python
# 添加导入
from tools.my_custom_tool import my_custom_tool
# 添加到工具列表
tools = [my_custom_tool]
```

### 配置代理行为

在`db/agent_config_v2.py`中修改代理的指令和行为：

```python
# 更新指令以修改代理的行为
# 在添加自定义内容时要小心保留核心流程阶段
```

## 网络搜索和浏览器自动化

Beifong的搜索代理通过[browseruse](https://browser-use.com/)库具备完整的浏览器自动化功能，能够进行网络研究和从任何网站自动收集数据。

### 搜索命令

您可以给代理特定的搜索指令，例如：
- *"转到我的X.com并收集顶部积极和信息丰富的Feed"*
- *"浏览Reddit以获取本周关于AI发展的讨论"*
- *"搜索LinkedIn以获取关于数据科学趋势的最新帖子"*
- *"访问新闻网站并收集关于可再生能源的文章"*

代理将导航网站，与页面元素交互，并自动提取请求的信息。

### 社交媒体登录会话

对于需要身份验证的网站（X.com、Facebook、LinkedIn等），您需要建立登录会话：

**设置社交媒体会话：**

1. 在Beifong Web界面中**导航到社交标签**
2. 在设置部分**点击"设置会话"**
3. **登录过程** - 将打开一个浏览器窗口，您需要：
   - 正常登录您的社交媒体账户
   - 完成任何验证步骤
   - 完成后关闭浏览器
4. **会话持久化** - Beifong将在未来的自动搜索中使用这些经过身份验证的会话

### 高级持久会话配置

对于持久的登录会话和高级浏览器管理：

**持久会话路径配置：**
- 默认浏览器会话存储在`browsers/playwright_persistent_profile_web`文件夹中
- 对于持久会话路径，修改`tools/web_search`以使用`db/config.py`中的`get_browser_session_path()`函数

**重要的持久会话管理注意事项：**
- **避免并发使用** - 确保没有其他进程同时使用相同的浏览器会话
- **社交监视处理器** 通常使用`get_browser_session_path()`函数中的路径
- **禁用冲突进程** - 如果使用持久会话路径，请在Voyager部分关闭社交监控
- **未来分离** - 会话管理将在即将到来的更新中分离为单独的会话

**持久会话故障排除：**
- 如果登录会话过期，请重复社交标签设置过程
- 如果遇到身份验证问题，请清除浏览器数据
- 确保一次只有一个进程访问浏览器会话

## 社交媒体监控

### 支持的平台

Beifong目前支持自动监控：

- **X.com (Twitter)** - 收集和分析您的社交媒体Feed
- **Facebook.com** - 监控您的Facebook时间线和互动

### 设置计划的Feed收集

要自动收集您的社交媒体Feed：

1. 在Beifong Web界面中**导航到Voyager标签**
2. **为社交媒体监控创建计划任务**
3. **配置收集频率** - 设置您希望收集Feed的频率
4. **选择平台** - 在X.com或Facebook.com处理器之间选择

### 查看AI洞察

收集社交媒体Feed后：

1. 在Web界面中**导航到社交标签**
2. **查看综合分析** - 每个帖子都通过AI进行分析，提供：
   - 内容情感分析
   - 主题分类
   - 参与度洞察
   - 相关性评分
3. **浏览完整洞察** - 所有收集的社交媒体内容的详细分析

### 配置自定义Feed

您可以轻松自定义要监控的Feed：

**修改Feed源：**
- 导航到`/tools/social/`目录
- 更新社交媒体处理器中的URL
- **监控特定配置文件** - 配置以跟踪特定的X.com配置文件或Facebook页面
- **自定义Feed类型** - 适应URL以用于不同类型的Content Feed

**URL配置示例：**
- 跟踪特定的X.com用户：修改URL以定位特定的配置文件
- 监控Facebook页面：为特定的Facebook Feed配置URL
- 自定义标签监控：设置URL以跟踪特定的标签或主题

### 添加新的社交媒体账户

Beifong支持轻松扩展到其他平台：

**当前支持：**
- X.com (Twitter)
- Facebook.com

**易于集成的选项：**
- **LinkedIn**
- **Reddit** 
- **其他平台** - 大多数社交媒体平台可以使用相同框架集成，但您必须编写自定义爬虫或使用API。

**未来更新：**
- 下一版本将包含更多针对流行社交媒体平台的内置连接器
- 支持每个平台的多个账户管理

### 计划最佳实践

**重要的计划注意事项：**

⚠️ **避免并发执行** - 在调度多个社交媒体Feed收集任务时，确保它们不会同时运行。所有社交媒体处理器共享相同的持久浏览器会话。

**推荐的计划方法：**
- **错开收集时间** - 在不同时间安排X.com和Facebook.com收集
- **允许处理间隙** - 在不同的社交媒体任务之间留出足够的时间
- **监控执行时间** - 跟踪每个收集所需的时间以避免重叠

**安全计划示例：**
- X.com Feed收集：每2小时在:00分钟
- Facebook.com Feed收集：每2小时在:30分钟

**未来改进：**
- 下一版本将为每个社交媒体账户提供单独的持久浏览器会话
- 这将消除仔细计划的需要，并允许从多个平台并发收集

## 音频和语音生成

### 支持的TTS引擎

Beifong支持多种文本到语音选项：

**商业选项：**
- **OpenAI TTS** 
- **ElevenLabs** 

**开源选项：**
- **Kokoro**

### 添加新的语音引擎

TTS系统支持集成额外的引擎：

**潜在的下一个开源集成选项：**
- **[Dia TTS](https://yummy-fir-7a4.notion.site/dia)** 
- **[CSM](https://github.com/SesameAILabs/csm)** 
- **[Orpheus-TTS](https://github.com/canopyai/Orpheus-TTS)** 

通过**utils**目录中的tts_selector引擎接口添加自定义TTS引擎。

## 集成

Beifong可以与其他平台集成。

### Slack集成

Beifong的Slack集成使您能够直接从Slack工作区与AI代理交互。与Beifong的每次对话都会为会话创建一个专用的Slack线程。

**主要功能：**
- 在Slack频道中直接与BeifongAI消息交互

### 设置Slack应用

要将Beifong与您的Slack工作区集成，您需要在Socket模式下创建一个Slack应用：

#### 步骤1：创建Slack应用

1. 访问[Slack API Apps](https://api.slack.com/apps)并点击"Create New App"
2. 选择"From scratch"并提供：
   - **App Name**: BeifongAI（或您喜欢的名称）
   - **Workspace**: 选择您的目标Slack工作区
3. **启用Socket模式**：
   - 在左侧边栏导航到"Socket Mode"
   - 将"Enable Socket Mode"切换为ON
   - 生成具有`connections:write`范围的应用级令牌
   - 保存**应用级令牌**（这是您的`SLACK_APP_TOKEN`）

#### 步骤2：配置Bot用户

1. 在左侧边栏导航到"OAuth & Permissions"
2. 滚动到"Bot Token Scopes"并添加所需的权限（见下一节）
3. 点击"Install to Workspace"并授权应用
4. 复制**Bot User OAuth Token**（这是您的`SLACK_BOT_TOKEN`）

#### 步骤3：启用事件订阅

1. 在左侧边栏导航到"Event Subscriptions"
2. 将"Enable Events"切换为ON
3. 添加所需的bot事件（见下面的权限部分）

### 所需的Slack权限

您的Slack应用需要特定权限才能与Beifong正常工作：

#### OAuth & Permissions - Bot Token Scopes

在"OAuth & Permissions" → "Bot Token Scopes"下添加以下范围：

- **`app_mentions:read`** - 查看应用所在对话中直接提及@BeifongAI的消息
- **`assistant:write`** - 允许BeifongAI作为应用代理行动
- **`channels:history`** - 查看BeifongAI已加入的公共频道中的消息和其他内容
- **`channels:read`** - 查看工作区中公共频道的基本信息
- **`chat:write`** - 以@BeifongAI身份发送消息
- **`files:read`** - 查看BeifongAI已加入的频道和对话中共享的文件
- **`files:write`** - 以@BeifongAI身份上传、编辑和删除文件
- **`im:read`** - 查看BeifongAI已加入的直接消息的基本信息
- **`im:write`** - 与人员开始直接消息

#### Event Subscriptions - Bot Events

在"Event Subscriptions" → "Subscribe to bot events"下，添加：

- **`app_mention`** - 仅订阅提及您的应用或bot的消息事件
  - *所需范围: `app_mentions:read`*
- **`message.channels`** - 频道中发布了消息
  - *所需范围: `channels:history`*

### 环境配置

将您的Slack令牌添加到`/beifong`目录中的`.env`文件：

```env
# 现有的环境变量...
OPENAI_API_KEY=your_openai_api_key
ELEVENSLAB_API_KEY=your_elevenlabs_api_key  # 可选

# Slack集成
SLACK_BOT_TOKEN=xoxb-your-bot-user-oauth-token
SLACK_APP_TOKEN=xapp-your-app-level-token

# Redis配置
REDIS_HOST=localhost
REDIS_PORT=6379
REDIS_DB=0
```

### 运行Slack集成

配置Slack应用和环境变量后：

#### 步骤1：在工作区中安装应用

1. 确保您的Slack应用已安装在您的工作区中
2. 将BeifongAI添加到您想要使用的频道中
3. 您也可以向BeifongAI发送直接消息

#### 步骤2：启动Slack集成

```bash
# 导航到beifong目录
cd beifong

# 确保您的环境已激活
source venv/bin/activate

# 运行Slack集成脚本
python -m integrations.slack.chat
```

#### 步骤3：与BeifongAI交互

**在Slack频道中：**
- 提及@BeifongAI以开始对话
- 每次提及都会为上下文连续性创建一个新线程
- 示例：`@BeifongAI 您能帮我分析最新的AI发展新闻吗？`

**参考文档：**
- [Slack Socket Mode API](https://api.slack.com/apis/socket-mode)

## 数据存储和文件管理

### 数据库存储

所有应用程序数据库都组织在**databases**目录中，便于管理和备份。

### 媒体资产存储

生成的播客、音频文件和视觉资产存储在**podcasts**目录中。

### 管理存储增长

如果资产存储增长，考虑这些存储优化策略：

**云存储集成：**
- 使用s3fs将S3存储桶挂载为本地文件夹以存储媒体资产
- 在`.env`中配置自定义存储路径以使用更大的驱动器

**自动清理：**
- 设置定期归档旧播客剧集
- 实现临时录音和未使用资产的自动清理
- 为不同类型的内容配置保留策略

**存储监控：**
- 监控磁盘使用情况，因为您的内容库增长
- 为存储容量阈值设置警报

**注意：** 更高效的存储管理和云连接器将在下一个版本中添加。

## 部署和访问选项

### 本地网络访问

```bash
# 启动具有网络访问权限的后端
cd beifong
python main.py --host 0.0.0.0 --port 7000
```

这使得应用程序可以通过您机器的IP地址在本地网络上访问。

### 远程访问解决方案

从本地网络外部访问Beifong（解决方法）：

#### SSH端口转发
```bash
# 将本地端口转发到远程机器
ssh -L 7000:localhost:7000 username@your-server-ip
```

#### Ngrok隧道
```bash
# 创建临时公共隧道
ngrok http 7000
```
提供一个临时的公共URL，转发到您的本地实例。

### 安全性

Beifong尚未包含认证层。认证将在下一个版本中添加。

## 云选项

### Beifong云功能
即将推出！

✅ Beifong云版本

✅ 更多社交媒体连接器

✅ 更多API选项。Claude、Gemini、OpenAI、Ollama

✅ 更多样式的播客定制

✅ 更多语音选项

✅ 更好的数据收集和存储管理

✅ 认证层

## 故障排除

### Kokoro库安装问题

如果由于Kokoro库导致安装失败，您可以跳过安装此库，仅在需要时作为TTS引擎安装。Kokoro是可选的，仅在您想使用它进行文本到语音生成时才需要。

有关Kokoro的更多信息，请查看参考：https://github.com/hexgrad/kokoro

### Browseruse安装问题

如果由于browseruse导致安装失败，请确保Playwright版本已正确安装。浏览器自动化功能依赖于Playwright的正确设置。

更多参考和故障排除：https://github.com/browser-use/browser-use

### FAISS库安装问题

如果FAISS库安装失败，您可以安全地忽略此错误并跳过安装FAISS。此库仅在您想使用语义搜索功能时才需要。如果您不需要语义搜索功能，可以安全地忽略FAISS安装失败。

参考：https://github.com/facebookresearch/faiss

### 基于浏览器的数据收集问题

一些数据收集功能依赖于浏览器自动化，在服务器环境中有时无法正常工作。虽然Beifong仍会运行，但某些浏览器依赖功能在没有适当浏览器设置的服务器环境中可能无法工作。

## 更新

🚀 **[仓库](https://github.com/arun477/beifong)**