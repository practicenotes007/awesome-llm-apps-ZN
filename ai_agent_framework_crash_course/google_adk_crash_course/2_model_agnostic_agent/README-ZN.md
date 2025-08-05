# 🎯 教程2：模型无关代理

学习如何使用OpenRouter创建适用于**不同AI模型**的代理。此示例展示了ADK如何通过单独的代理实现使用OpenAI和Anthropic模型。

## 🎯 您将学到什么

- **OpenRouter集成**：使用一个API密钥访问多个模型提供商
- **独立代理实现**：并排比较不同模型
- **工具集成**：为您的代理添加简单工具
- **根代理模式**：正确的ADK代理命名约定

## 🧠 核心概念：一个API，多个模型

[OpenRouter](https://openrouter.ai/)提供统一API访问多个AI模型：
- ✅ **单一API密钥**：使用一个密钥访问OpenAI和Anthropic
- ✅ **轻松比较**：运行不同代理以比较响应
- ✅ **成本效益**：按使用量付费
- ✅ **无供应商锁定**：随时切换提供商

## 📁 项目结构

```
2_model_agnostic_agent/
├── README.md                       # 本概述
├── requirements.txt                # 共享依赖项
├── 2_1_openai_adk_agent/           # OpenAI GPT-4代理
│   └── agent.py                    # 代理实现
└── 2_2_anthropic_adk_agent/        # Anthropic Claude代理
    └── agent.py                    # 代理实现
```

## 🔧 可用代理

### **OpenAI代理** (`2_1_openai_adk_agent/`)
- **模型**：通过OpenRouter的GPT-4
- **代理名称**：`root_agent`（ADK要求）
- **功能**：带有OpenAI个性的趣味事实工具

### **Anthropic代理** (`2_2_anthropic_adk_agent/`)
- **模型**：通过OpenRouter的Claude 4 Sonnet
- **代理名称**：`root_agent`（ADK要求）
- **功能**：带有Claude个性的趣味事实工具

## 🛠️ 设置和使用

### 1. **获取OpenRouter API密钥**
- 访问：[https://openrouter.ai/keys](https://openrouter.ai/keys)
- 注册并获取您的API密钥

### 2. **设置环境变量**
在每个代理文件夹中创建一个`.env`文件：

**在`2_1_openai_adk_agent/.env`中：**
```bash
OPENROUTER_API_KEY=your_openrouter_api_key_here
```

**在`2_2_anthropic_adk_agent/.env`中：**
```bash
OPENROUTER_API_KEY=your_openrouter_api_key_here
```

### 3. **安装依赖项**
```bash
# 从2_model_agnostic_agent目录
pip install -r requirements.txt
```

### 4. **测试OpenAI代理**
```bash
cd 2_1_openai_adk_agent
adk web
```
- 尝试询问："告诉我一个有趣的事实！"
- 注意OpenAI GPT-4的响应风格

### 5. **测试Anthropic代理**
```bash
cd 2_2_anthropic_adk_agent
adk web
```
- 尝试询问："告诉我一个有趣的事实！"
- 与Claude的响应风格进行比较

## 💡 关键代码模式

每个代理都遵循相同的模式：

```python
from google.adk.agents import Agent
from google.adk.models.lite_llm import LiteLlm
import os

# 通过OpenRouter创建模型
model = LiteLlm(
    model="openrouter/openai/gpt-4",  # 或claude模型
    api_key=os.getenv("OPENROUTER_API_KEY"),
    base_url="https://openrouter.ai/api/v1"
)

# 创建root_agent（ADK要求的名称）
```

## 🎯 学习目标

完成本教程后，您将理解：
- ✅ 如何在ADK中使用OpenRouter
- ✅ 如何为不同模型创建独立代理
- ✅ 如何比较不同AI提供商的响应
- ✅ 如何使用`root_agent`正确构建ADK代理

## 🔄 比较模型

1. **运行OpenAI代理**并提问
2. **运行Anthropic代理**并提出相同问题
3. **注意响应风格和方法的差异**
4. **尝试**不同类型的提示

## 💰 费用信息

- OpenRouter按令牌使用量收费
- GPT-4o：更昂贵但功能强大
- Claude 4 Sonnet：成本和性能平衡
- 您可以在OpenRouter仪表板中设置消费限额
- 提供用于测试的免费层级

## 🚨 重要说明

- **根代理**：每个代理必须命名为`root_agent`，ADK才能识别
- **环境变量**：每个文件夹都需要自己的`.env`文件
- **API密钥**：同一个OpenRouter密钥适用于两个代理
- **比较**：分别运行代理以比较模型行为