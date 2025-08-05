# 🎯 教程3：结构化输出代理

欢迎来到结构化输出！本教程教您如何创建返回**类型安全、结构化数据**而不是纯文本的代理。这对于构建需要可预测数据格式的可靠应用程序至关重要。

## 🎯 您将学到什么

- **Pydantic模式**：使用验证定义数据结构
- **类型安全**：确保代理返回预期的数据格式
- **业务逻辑**：可靠地处理结构化数据
- **错误处理**：优雅地处理验证错误
- **实际应用**：客户支持和邮件生成

## 🧠 核心概念：结构化输出

结构化输出意味着您的代理返回**经过验证的数据对象**而不是原始文本：
- ✅ **类型安全**：确切知道您将收到什么数据格式
- ✅ **验证**：自动检查必填字段和数据类型
- ✅ **可靠性**：不再需要手动解析文本响应
- ✅ **集成**：易于在应用程序和数据库中使用

### 为什么使用结构化输出？
- **可预测性**：始终获得相同的数据结构
- **验证**：Pydantic确保数据正确性
- **类型化**：完整的IDE支持和类型检查
- **可扩展性**：易于修改和扩展模式

## 🚀 教程结构

本教程包含**两个综合示例**：

### 📍 **示例1：客户支持工单代理**
**位置**：`./3_1_customer_support_ticket_agent/`
- 从客户投诉中提取结构化工单信息
- 优先级分类和紧急程度评估
- 联系信息提取
- 部门路由逻辑

### 📍 **示例2：邮件生成代理**
**位置**：`./3_2_email_agent/`
- 生成带有元数据的结构化邮件内容
- 主题行优化
- 收件人分类
- 邮件模板格式化

## 📁 项目结构

```
3_structured_output_agent/
├── README.md                           # 本教程概述
├── 3_1_customer_support_ticket_agent/  # 客户支持示例
└── 3_2_email_agent/                   # 邮件生成示例
```

每个示例目录都遵循标准结构：
- **Python文件**：包含代理实现和Streamlit应用
- **README.md**：设置和使用文档
- **requirements.txt**：依赖项列表

## 🎯 学习目标

完成本教程后，您将理解：
- ✅ 如何为结构化输出定义Pydantic模式
- ✅ 如何配置代理以返回结构化数据
- ✅ 如何优雅地处理验证错误
- ✅ 何时使用结构化输出vs纯文本
- ✅ 模式设计的最佳实践

## 💡 关键模式

### 基本结构化输出模式
```python
from pydantic import BaseModel
from google.adk.agents import Agent

class TicketInfo(BaseModel):
    title: str
    priority: str
    category: str
    urgency_level: int

agent = Agent(
    name="support_agent",
    model="gemini-2.0-flash",
    instruction="提取工单信息...",
    response_format=TicketInfo,  # 这确保了结构化输出！
)
```

### 带验证的高级模式
```python
from pydantic import BaseModel, Field, validator
from typing import List, Optional

class EmailData(BaseModel):
    subject: str = Field(..., min_length=5, max_length=100)
    recipients: List[str] = Field(..., min_items=1)
    priority: str = Field(..., regex="^(low|medium|high)$")
    
    @validator('recipients')
    def validate_emails(cls, v):
        # 自定义邮件验证逻辑
```

## 🎯 实际应用

结构化输出代理非常适合：
- **客户支持**：从投诉中提取工单信息
- **数据处理**：将非结构化文本转换为数据库记录
- **内容生成**：创建带有元数据的结构化内容
- **表单处理**：从文档中提取信息
- **API集成**：为其他系统提供一致的数据格式

## 💡 专业提示

- **清晰的模式**：使用描述性字段名并添加文档字符串
- **验证**：为您的用例添加适当的验证器
- **可选字段**：对可能缺失的字段使用`Optional`
- **示例**：在模式文档中提供示例数据
- **错误处理**：始终优雅地处理验证错误

## 🚨 重要说明

- **Pydantic必需**：您需要Pydantic进行模式定义
- **模型支持**：并非所有模型都同样好地支持结构化输出
- **验证开销**：复杂模式可能会减慢响应速度
- **模式演进**：为生产系统中的模式变化做计划