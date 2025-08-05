## 🦙 用30行Python代码微调Llama 3.2

本脚本演示了如何使用[Unsloth](https://unsloth.ai/)库微调Llama 3.2模型，该库使微调过程变得简单快捷。您可以在Google Colab中免费运行此示例来微调Llama 3.1 1B和3B模型。

### 特性

- 使用Unsloth库微调Llama 3.2模型
- 实现低秩适应(LoRA)以进行高效微调
- 使用FineTome-100k数据集进行训练
- 可配置不同模型大小(1B和3B)

### 安装

1. 克隆仓库：

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd awesome-llm-apps/llm_finetuning_tutorials/llama3.2_finetuning
```

2. 安装所需依赖：

```bash
pip install -r requirements.txt
```

## 使用方法

1. 在Google Colab或您首选的Python环境中打开脚本。

2. 运行脚本开始微调过程：

```bash
# 运行整个脚本
python finetune_llama3.2.py
```

3. 微调后的模型将保存在"finetuned_model"目录中。

## 工作原理

1. **模型加载**：脚本使用Unsloth的FastLanguageModel加载Llama 3.2 3B Instruct模型。

2. **LoRA设置**：对模型的特定层应用低秩适应以进行高效微调。

3. **数据准备**：使用聊天模板加载并预处理FineTome-100k数据集。

4. **训练配置**：脚本使用特定的训练参数设置SFTTrainer。

5. **微调**：模型在准备好的数据集上进行微调。

6. **模型保存**：将微调后的模型保存到磁盘。

## 配置

您可以在脚本中修改以下参数：

- `model_name`：更改为"unsloth/Llama-3.1-1B-Instruct"以使用1B模型
- `max_seq_length`：调整最大序列长度
- `r`：LoRA秩
- `TrainingArguments`中的训练超参数

## 自定义

- 要使用不同的数据集，请将`load_dataset`函数调用替换为您想要的数据集。
- 调整LoRA设置中的`target_modules`以微调模型的不同层。
- 如果您使用不同的对话格式，请修改`get_chat_template`中的聊天模板。

## 在Google Colab上运行

1. 打开一个新的Google Colab笔记本。
2. 将整个脚本复制到代码单元格中。
3. 在开头添加一个单元格以安装所需的库：

```
!pip install torch transformers datasets trl unsloth
```

4. 运行单元格以开始微调过程。

## 注意事项

- 此脚本针对Google Colab免费层进行了优化，该层提供GPU访问权限。
- 微调过程可能需要一些时间，具体取决于模型大小和可用的计算资源。
- 确保您的Colab实例中有足够的存储空间来保存微调后的模型。