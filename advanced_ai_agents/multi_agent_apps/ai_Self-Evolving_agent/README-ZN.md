<!-- 在此处添加logo -->
<div align="center">
  <a href="https://github.com/EvoAgentX/EvoAgentX">
    <img src="./assets/EAXLoGo.svg" alt="EvoAgentX" width="50%">
  </a>
</div>

<h2 align="center">
    构建自我进化的AI代理生态系统
</h2>

<div align="center">

[![EvoAgentX主页](https://img.shields.io/badge/EvoAgentX-Homepage-blue?logo=homebridge)](https://evoagentx.org/)
[![文档](https://img.shields.io/badge/-Documentation-0A66C2?logo=readthedocs&logoColor=white&color=7289DA&labelColor=grey)](https://EvoAgentX.github.io/EvoAgentX/)
[![Discord](https://img.shields.io/badge/Chat-Discord-5865F2?&logo=discord&logoColor=white)](https://discord.gg/SUEkfTYn)
[![Twitter](https://img.shields.io/badge/Follow-@EvoAgentX-e3dee5?&logo=x&logoColor=white)](https://x.com/EvoAgentX)
[![微信](https://img.shields.io/badge/WeChat-EvoAgentX-brightgreen?logo=wechat&logoColor=white)](./assets/wechat_info.md)
[![GitHub星标图表](https://img.shields.io/github/stars/EvoAgentX/EvoAgentX?style=social)](https://star-history.com/#EvoAgentX/EvoAgentX)
[![GitHub fork](https://img.shields.io/github/forks/EvoAgentX/EvoAgentX?style=social)](https://github.com/EvoAgentX/EvoAgentX/fork)
[![许可证](https://img.shields.io/badge/License-MIT-blue.svg?)](https://github.com/EvoAgentX/EvoAgentX/blob/main/LICENSE)
<!-- [![EvoAgentX主页](https://img.shields.io/badge/EvoAgentX-Homepage-blue?logo=homebridge)](https://EvoAgentX.github.io/EvoAgentX/) -->
<!-- [![hf_space](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-EvoAgentX-ffc107?color=ffc107&logoColor=white)](https://huggingface.co/EvoAgentX) -->
</div>

<div align="center">

<h3 align="center">

<a href="./README.md" style="text-decoration: underline;">English</a> | <a href="./README-zh.md">简体中文</a>

</h3>

</div>

<h4 align="center">
  <i>一个用于评估和进化代理工作流程的自动化框架。</i>
</h4>

<p align="center">
  <img src="./assets/framework_en.jpg">
</p>


## 🔥 最新消息
- **[2025年5月]** 🎉 **EvoAgentX** 正式发布！

## ⚡ 开始使用
- [🔥 最新消息](#-最新消息)
- [⚡ 开始使用](#-开始使用)
- [安装](#安装)
- [LLM配置](#llm配置)
  - [API密钥配置](#api密钥配置)
  - [配置和使用LLM](#配置和使用llm)
- [自动工作流程生成](#自动工作流程生成)
- [演示视频](#演示视频)
  - [✨ 最终结果](#-最终结果)
- [进化算法](#进化算法)
  - [📊 结果](#-结果)
- [应用](#应用)
- [教程和用例](#教程和用例)
- [🎯 路线图](#-路线图)
- [🙋 支持](#-支持)
  - [加入社区](#加入社区)
  - [联系信息](#联系信息)
- [🙌 为EvoAgentX做贡献](#-为evoagentx做贡献)
- [📚 致谢](#-致谢)
- [📄 许可证](#-许可证)

## 安装

我们推荐使用`pip`安装EvoAgentX：

```bash
pip install git+https://github.com/EvoAgentX/EvoAgentX.git
```

对于本地开发或详细设置（例如使用conda），请参考[EvoAgentX安装指南](./docs/installation.md)。

<details>
<summary>示例（可选，用于本地开发）：</summary>

```bash
git clone https://github.com/EvoAgentX/EvoAgentX.git
cd EvoAgentX
# 创建新的conda环境
conda create -n evoagentx python=3.10

# 激活环境
conda activate evoagentx

# 安装包
pip install -r requirements.txt
# 或以开发模式安装
pip install -e .
```
</details>

## LLM配置

### API密钥配置

要将LLM与EvoAgentX一起使用（例如OpenAI），您必须设置API密钥。

<details>
<summary>选项1：通过环境变量设置API密钥</summary> 

- Linux/macOS: 
```bash
export OPENAI_API_KEY=<your-openai-api-key>
```

- Windows命令提示符: 
```cmd 
set OPENAI_API_KEY=<your-openai-api-key>
```

-  Windows PowerShell:
```powershell
$env:OPENAI_API_KEY="<your-openai-api-key>" # 需要引号
```

设置后，您可以在Python代码中访问密钥：
```python
import os
OPENAI_API_KEY = os.getenv("OPENAI_API_KEY")
```
</details>

<details>
<summary>选项2：使用.env文件</summary> 

- 在项目根目录创建.env文件并添加以下内容：
```bash
OPENAI_API_KEY=<your-openai-api-key>
```

然后在Python中加载：
```python
from dotenv import load_dotenv 
import os 

load_dotenv() # 从.env文件加载环境变量
OPENAI_API_KEY = os.getenv("OPENAI_API_KEY")
```
</details>
<!-- > 🔐 提示：别忘了将`.env`添加到`.gitignore`中以避免提交机密信息。 -->

### 配置和使用LLM
设置API密钥后，使用以下代码初始化LLM：

```python
from evoagentx.models import OpenAILLMConfig, OpenAILLM

# 从环境加载API密钥
OPENAI_API_KEY = os.getenv("OPENAI_API_KEY")

# 定义LLM配置
openai_config = OpenAILLMConfig(
    model="gpt-4o-mini",       # 指定模型名称
    openai_key=OPENAI_API_KEY, # 直接传递密钥
    stream=True,               # 启用流式响应
    output_response=True       # 将响应打印到标准输出
)

# 初始化语言模型
llm = OpenAILLM(config=openai_config)

# 从LLM生成响应
response = llm.generate(prompt="什么是代理工作流程？")
```
> 📖 更多关于支持的模型和配置选项的详细信息：[LLM模块指南](./docs/modules/llm.md)。

## 自动工作流程生成
配置好API密钥和语言模型后，您可以自动在EvoAgentX中生成和执行多代理工作流程。

🧩 核心步骤：
1. 定义自然语言目标
2. 使用`WorkFlowGenerator`生成工作流程
3. 使用`AgentManager`实例化代理
4. 通过`WorkFlow`执行工作流程

💡 最小示例：
```python
from evoagentx.workflow import WorkFlowGenerator, WorkFlowGraph, WorkFlow
from evoagentx.agents import AgentManager

goal = "生成俄罗斯方块游戏的html代码"
workflow_graph = WorkFlowGenerator(llm=llm).generate_workflow(goal)

agent_manager = AgentManager()
agent_manager.add_agents_from_workflow(workflow_graph, llm_config=openai_config)

workflow = WorkFlow(graph=workflow_graph, agent_manager=agent_manager, llm=llm)
output = workflow.execute()
print(output)
```

您还可以：
- 📊 可视化工作流程：`workflow_graph.display()`

- 💾 保存/加载工作流程：`save_module()` / `from_file()`

> 📂 有关完整的工作示例，请查看[`workflow_demo.py`](https://github.com/EvoAgentX/EvoAgentX/blob/main/examples/workflow_demo.py)

## 演示视频

[![在YouTube上观看](https://img.shields.io/badge/-Watch%20on%20YouTube-red?logo=youtube&labelColor=grey)](https://www.youtube.com/watch?v=Wu0ZydYDqgg)

<div align="center">
  <video src="https://github.com/user-attachments/assets/8f65d1af-9398-40c3-a625-4f493e13e5a5.mp4" autoplay loop muted playsinline width="600">
    您的浏览器不支持视频标签。
  </video>
</div>

在此演示中，我们通过两个示例展示EvoAgentX的工作流程生成和执行能力：

- 应用1：从简历智能推荐工作
- 应用2：A股股票视觉分析

### ✨ 最终结果

<table>
  <tr>
    <td align="center">
      <img src="./assets/demo_result_1.png" width="400"><br>
      <strong>应用&nbsp;1:</strong><br>工作推荐
    </td>
    <td align="center">
      <img src="./assets/demo_result_2.jpeg" width="400"><br>
      <strong>应用&nbsp;2:</strong><br>股票视觉分析
    </td>
  </tr>
</table>

## 进化算法

我们已将一些现有的代理/工作流程进化算法集成到EvoAgentX中，包括[TextGrad](https://www.nature.com/articles/s41586-025-08661-4)、[MIPRO](https://arxiv.org/abs/2406.11695)和[AFlow](https://arxiv.org/abs/2410.10762)。

为了评估性能，我们在三个不同任务上使用它们优化相同的代理系统：多跳问答（HotPotQA）、代码生成（MBPP）和推理（MATH）。我们随机抽取50个示例进行验证，另外100个示例进行测试。

> 提示：我们已在EvoAgentX中集成了这些基准测试和评估代码。更多详情请参考[基准测试和评估教程](https://github.com/EvoAgentX/EvoAgentX/blob/main/docs/tutorial/benchmark_and_evaluation.md)。

### 📊 结果

| 方法     | HotPotQA<br>(F1%) | MBPP<br>(Pass@1 %) | MATH<br>(解决率 %) |
|----------|--------------------|---------------------|--------------------------|
| 原始     | 63.58              | 69.00               | 66.00                    |
| TextGrad | 71.02              | 71.00               | 76.00                    |
| AFlow    | 65.09              | 79.00               | 71.00                    |
| MIPRO    | 69.16              | 68.00               | 72.30                    |

更多详情请参考`examples/optimization`文件夹。

## 应用

我们使用框架在[GAIA](https://huggingface.co/spaces/gaia-benchmark/leaderboard)基准测试上优化现有的多代理系统。我们选择了[Open Deep Research](https://github.com/huggingface/smolagents/tree/main/examples/open_deep_research)和[OWL](https://github.com/camel-ai/owl)，这两个来自GAIA排行榜的开源且可运行的代表性多代理框架。

我们应用EvoAgentX优化它们的提示。下图显示了优化后的代理在GAIA基准测试验证集上的性能。

<table>
  <tr>
    <td align="center" width="50%">
      <img src="./assets/open_deep_research_optimization_report.png" alt="Open Deep Research优化" width="100%"><br>
      <strong>Open Deep Research</strong>
    </td>
    <td align="center" width="50%">
      <img src="./assets/owl_optimization_result.png" alt="OWL优化" width="100%"><br>
      <strong>OWL代理</strong>
    </td>
  </tr>
</table>

> 完整优化报告：[Open Deep Research](https://github.com/eax6/smolagents)和[OWL](https://github.com/TedSIWEILIU/owl)。

## 教程和用例

> 💡 **EvoAgentX新手？** 从[快速入门指南](./docs/quickstart.md)开始，逐步了解。

通过以下资源探索如何有效使用EvoAgentX：

| 教程 | 描述 |
|:---|:---|
| **[构建您的第一个代理](./docs/tutorial/first_agent.md)** | 快速创建和管理具有多动作能力的代理。 |
| **[构建您的第一个工作流程](./docs/tutorial/first_workflow.md)** | 学习构建多个代理的协作工作流程。 |
| **[自动工作流程生成](./docs/quickstart.md#automatic-workflow-generation-and-execution)** | 从自然语言目标自动生成工作流程。 |
| **[基准测试和评估教程](./docs/tutorial/benchmark_and_evaluation.md)** | 使用基准数据集评估代理性能。 |
| **[TextGrad优化器教程](./docs/tutorial/textgrad_optimizer.md)** | 使用TextGrad自动优化多代理工作流程中的提示。 |
| **[AFlow优化器教程](./docs/tutorial/aflow_optimizer.md)** | 使用AFlow自动优化多代理工作流程的提示和结构。 |
<!-- | **[SEW优化器教程](./docs/tutorial/sew_optimizer.md)** | 创建SEW（自我进化工作流程）以增强代理系统。 | -->

🛠️ 跟随教程构建和优化您的EvoAgentX工作流程。

🚀 我们正在积极扩展用例库和优化策略。**更多内容即将推出——敬请期待！**

## 🎯 路线图
- [ ] **模块化进化算法**：将优化算法抽象为即插即用模块，可轻松集成到自定义工作流程中。 
- [ ] **开发任务模板和代理模块**：为典型任务构建可重用模板和标准化代理组件，以简化应用开发。
- [ ] **集成自我进化代理算法**：整合更多最近和先进的代理自我进化算法，涵盖提示调优、工作流程结构和内存模块等多个维度。 
- [ ] **启用可视化工作流程编辑界面**：提供工作流程结构显示和编辑的可视化界面，以提高可用性和调试能力。

## 🙋 支持

### 加入社区

📢 保持联系，成为**EvoAgentX**旅程的一部分！
🚩 加入我们的社区以获取最新更新、分享您的想法，并与全球AI爱好者合作。

- [Discord](https://discord.gg/SUEkfTYn) — 实时聊天、讨论和协作。
- [X (前身为Twitter)](https://x.com/EvoAgentX) — 关注我们获取新闻、更新和见解。
- [微信](https://github.com/EvoAgentX/EvoAgentX/blob/main/assets/wechat_info.md) — 与我们的中文社区连接。

### 联系信息

如果您对本项目有任何问题或反馈，请随时联系我们。我们非常感谢您的建议！

- **邮箱：** evoagentx.ai@gmail.com

我们将在2-3个工作日内回复所有问题。

## 🙌 为EvoAgentX做贡献
感谢这些优秀的贡献者

<a href="https://github.com/EvoAgentX/EvoAgentX/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=EvoAgentX/EvoAgentX" />
</a>

感谢您有兴趣为我们的开源项目做贡献。我们提供了[贡献指南](https://github.com/EvoAgentX/EvoAgentX/blob/main/CONTRIBUTING.md)文档，其中概述了为EvoAgentX做贡献的步骤。请参考此指南以确保顺利协作和成功贡献。🤝🚀

[![Star历史图表](https://api.star-history.com/svg?repos=EvoAgentX/EvoAgentX&type=Date)](https://www.star-history.com/#EvoAgentX/EvoAgentX&Date)

## 📚 致谢
本项目基于几个杰出的开源项目：[AFlow](https://github.com/FoundationAgents/MetaGPT/tree/main/metagpt/ext/aflow)、[TextGrad](https://github.com/zou-group/textgrad)、[DSPy](https://github.com/stanfordnlp/dspy)、[LiveCodeBench](https://github.com/LiveCodeBench/LiveCodeBench)等。我们要感谢这些框架的开发者和维护者为开源社区做出的宝贵贡献。

## 📄 许可证

本仓库中的源代码在[MIT许可证](./LICENSE)下提供。