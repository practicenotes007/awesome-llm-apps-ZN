# ⚡ 函数工具

函数工具是您创建并集成到代理中的**自定义Python函数**。这是为代理添加特定功能的最灵活和最常用的方法。

## 🎯 您将学到什么

- **函数工具创建**：构建自定义Python函数作为工具
- **工具注册**：如何向代理注册函数
- **参数处理**：管理工具输入和输出
- **错误处理**：工具中的健壮错误管理
- **最佳实践**：有效的函数工具设计模式

## 🧠 核心概念：函数工具

函数工具是**具有特殊特征的Python函数**：
- **描述性文档字符串**：帮助代理理解何时使用它们
- **类型注解**：清晰的输入/输出规范
- **返回字典**：结构化、信息丰富的响应
- **错误处理**：优雅的故障管理

### 主要优势
- ✅ **最大灵活性**：创建您需要的任何功能
- ✅ **易于集成**：简单的Python函数
- ✅ **完全控制**：对行为的完全控制
- ✅ **调试**：易于测试和调试

## 🔧 函数工具要求

### 1. **描述性文档字符串**
```python
def calculate_compound_interest(principal: float, rate: float, years: int) -> dict:
    """
    计算投资的复利。
    
    当用户询问投资增长、复利计算或投资未来价值时使用此函数。
    
    Args:
        principal: 初始投资金额
        rate: 年利率（以小数表示，例如0.05表示5%）
        years: 复利年数
    
    Returns:
        包含计算结果和明细的字典
    """
```

### 2. **类型注解**
- 始终指定参数类型
- 包含返回类型注解
- 使用适当的Python类型（str、int、float、dict、list）

### 3. **结构化返回**
```python
return {
    "result": final_amount,
    "calculation_breakdown": {
        "principal": principal,
        "rate": rate,
        "years": years,
        "total_interest": total_interest
    },
    "status": "success"
}
```

### 4. **错误处理**
```python
try:
    # 工具逻辑在这里
    return {"result": result, "status": "success"}
except ValueError as e:
    return {"error": str(e), "status": "error"}
```

## 🚀 教程示例

此子示例包含两个实际实现：

### 📍 **计算器代理**
**位置**：`./calculator_agent/`
- **数学运算**：基本算术、复利、百分比计算
- **单位转换**：温度转换（摄氏度、华氏度、开尔文）
- **统计分析**：数据集的均值、中位数、众数、标准差
- **财务计算**：投资增长、复利预测
- **数字工具**：四舍五入、格式化和数学表达式

### 📍 **工具代理**
**位置**：`./utility_agent/`
- **文本处理**：单词计数、大小写转换、文本转换
- **数据提取**：电子邮件和URL提取、词频分析
- **日期/时间操作**：格式转换、日期差异、年龄计算
- **数据工具**：UUID生成、文本哈希、Base64编码/解码
- **验证工具**：URL验证、JSON格式化和验证

## 📁 项目结构

```
4_2_function_tools/
├── README.md                    # 本文件 - 函数工具指南
├── requirements.txt             # 函数工具的依赖项
├── .env.example                # 环境变量模板（共享）
├── calculator_agent/           # 数学工具实现
│   ├── __init__.py
│   ├── agent.py               # 带自定义工具的计算器代理
│   └── tools.py               # 数学函数工具
└── utility_agent/              # 工具实现
    ├── __init__.py
    ├── agent.py               # 带各种工具的工具代理
    └── tools.py               # 文本处理、日期/时间和数据工具
```

## 🎯 学习目标

完成此子示例后，您将理解：
- ✅ 如何创建自定义Python函数作为工具
- ✅ 工具设计和文档的最佳实践
- ✅ 如何有效处理参数和返回值
- ✅ 错误处理和验证策略
- ✅ 何时使用函数工具与其他方法

## 🚀 开始使用

1. **设置环境**：
   ```bash
   cd 4_2_function_tools
   
   # 复制环境模板
   cp env.example .env
   
   # 编辑.env并添加您的Google AI API密钥
   # 从以下网址获取API密钥：https://aistudio.google.com/
   ```

2. **安装依赖项**：
   ```bash
   # 安装所需包
   pip install -r requirements.txt
   ```

3. **运行代理**：
   ```bash
   # 启动ADK Web界面
   adk web
   
   # 在Web界面中，选择：
   # - calculator_agent: 用于数学计算和转换
   # - utility_agent: 用于文本处理、日期/时间和数据工具
   ```

4. **尝试代理**：
   - **计算器代理**："计算200的15%"，"将100°F转换为摄氏度"，"查找[1,2,3,4,5]的统计数据"
   - **工具代理**："计算此文本中的单词数"，"格式化日期2023-12-25"，"生成UUID"

5. **创建您自己的工具**：为您的用例构建自定义工具

## 💡 专业提示

- **每个工具一个目的**：每个函数应该做好一件事
- **丰富的文档字符串**：文档字符串对代理理解至关重要
- **验证输入**：始终验证函数参数
- **返回字典**：结构化返回更容易处理
- **独立测试**：首先在代理外测试工具

## 🔧 常见函数工具模式

### 1. **简单计算器模式**
```python
def add_numbers(a: float, b: float) -> dict:
    """将两个数字相加。"""
    return {"result": a + b, "operation": "addition"}
```

### 2. **数据处理模式**
```python
def analyze_text(text: str) -> dict:
    """分析文本的单词数、情感等。"""
    return {
        "word_count": len(text.split()),
        "character_count": len(text),
        "sentiment": "neutral"  # 占位符
    }
```

### 3. **API集成模式**
```python
def get_weather(city: str) -> dict:
    """获取城市的天气信息。"""
    try:
        # API调用逻辑在这里
        return {"temperature": 72, "condition": "sunny"}
    except Exception as e:
        return {"error": str(e), "status": "failed"}
```

### 4. **转换模式**
```python
def convert_temperature(temp: float, from_unit: str, to_unit: str) -> dict:
    """在单位之间转换温度。"""
    # 转换逻辑
    return {
        "original": {"value": temp, "unit": from_unit},
        "converted": {"value": converted_temp, "unit": to_unit}
    }
```

## 🚨 重要说明

- **无默认参数**：ADK不支持默认参数
- **返回字典**：始终返回结构化数据
- **错误处理**：实现适当的错误处理
- **文档**：编写清晰、有帮助的文档字符串
- **测试**：在添加到代理之前独立测试函数

## 🔧 常见用例

### 数学工具（计算器代理）
- 基本算术运算和表达式
- 统计计算（均值、中位数、众数、标准差）
- 财务计算（复利、百分比）
- 单位转换（温度、测量）
- 数字格式化和四舍五入

### 文本处理工具（工具代理）
- 单词和字符计数
- 大小写转换和文本转换
- 从文本中提取电子邮件和URL
- 词频分析
- 字符串操作和格式化

### 日期/时间工具（工具代理）
- 日期格式转换
- 年龄计算和日期差异
- 时区处理
- 持续时间计算
- 日期解析和验证

### 数据工具（工具代理）
- 用于唯一标识符的UUID生成
- 使用各种算法的文本哈希
- Base64编码和解码
- URL验证和解析
- JSON格式化和验证

### 集成工具
- API调用和外部服务集成
- 数据库查询和数据检索
- 文件操作和数据处理
- 自定义业务逻辑实现