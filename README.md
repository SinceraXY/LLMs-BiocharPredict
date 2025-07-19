# LLMs-BiocharPredict

## 项目简介

本项目是一个基于大语言模型(Large Language Models, LLMs)的生物炭性质预测研究项目。项目结合了传统机器学习方法和大语言模型微调技术，用于预测生物炭的各种物理化学性质，包括产量(yield)、比表面积(specific surface area)、灰分含量(ash content)、pH值、粒径(grain size)等关键指标。

## 项目特色

- **多模型融合**: 集成了XGBoost、随机森林、人工神经网络(ANN)等传统机器学习模型
- **大语言模型微调**: 基于Llama3.1-8B和InternLM2.5-7B等开源大模型进行微调
- **多属性预测**: 支持生物炭多种性质的同时预测
- **数据驱动**: 基于大量实验数据构建的预测模型

## 技术栈

### 机器学习框架
- **XGBoost**: 梯度提升决策树算法
- **Scikit-learn**: 随机森林等传统机器学习算法
- **TensorFlow/Keras**: 深度学习神经网络模型

### 大语言模型
- **Llama3.1-8B**: Meta开源的大语言模型
- **InternLM2.5-7B**: 上海AI实验室开源的大语言模型

### 数据处理
- **Pandas**: 数据处理和分析
- **NumPy**: 数值计算
- **JSON**: 数据格式转换和存储

## 项目结构

```
LLMs-BiocharPredict/
├── README.md                                          # 项目说明文档
├── Data classification.ipynb                          # 数据分类和预处理
├── ML.ipynb                                           # 传统机器学习模型训练和测试
├── Q&A pair generation.ipynb                         # 问答对生成(用于大模型微调)
├── Re-extraction of data.ipynb                       # 数据重新提取和处理
├── Second round of fine-tuning preparations.ipynb    # 第二轮微调数据准备
├── Projected supplementary data.ipynb                # 补充数据处理
├── First round of training set and validation set data.csv    # 第一轮训练验证集
└── First round of test set data and second round of training and test set data.csv  # 测试集和第二轮数据
```

## 数据集说明

### 输入特征
项目使用的输入特征包括：
- **生物质来源**: 生物质资源类型、原料来源
- **预处理方法**: 预处理方式、设备类型
- **组成成分**: 纤维素、半纤维素、木质素含量
- **元素分析**: C、H、N、O、S含量
- **无机元素**: K、Ca、Na、Mg、Fe、Si含量
- **工艺参数**: 最高处理温度、升温速率、停留时间

### 预测目标
- **生物炭产量** (Biochar yield)
- **比表面积** (Specific surface area)
- **灰分含量** (Ash content)
- **元素含量** (C、H、N、O含量)
- **pH值**
- **粒径** (Grain size)

## 模型性能

### 传统机器学习模型
项目实现了三种主要的机器学习算法：

1. **XGBoost回归模型**
   - 使用梯度提升决策树
   - 评估指标：R²和RMSE

2. **随机森林回归模型**
   - 集成学习方法
   - 评估指标：R²和RMSE

3. **人工神经网络(ANN)**
   - 多层感知机结构
   - 包含数据标准化预处理
   - 评估指标：R²和RMSE

### 大语言模型微调
- 基于开源大模型进行微调
- 支持自然语言输入和输出
- 可处理复杂的多属性预测任务

## 快速开始

### 环境要求
```bash
# Python环境
Python >= 3.8

# 主要依赖包
pandas
numpy
scikit-learn
xgboost
tensorflow
transformers
torch
```

### 安装依赖
```bash
pip install pandas numpy scikit-learn xgboost tensorflow transformers torch
```

### 运行示例

#### 1. 数据预处理
```bash
# 运行数据分类notebook
jupyter notebook "Data classification.ipynb"
```

#### 2. 传统机器学习模型训练
```bash
# 运行机器学习模型训练
jupyter notebook "ML.ipynb"
```

#### 3. 大语言模型数据准备
```bash
# 生成问答对数据
jupyter notebook "Q&A pair generation.ipynb"
```

## 使用方法

### 传统机器学习预测
1. 准备输入数据（CSV格式）
2. 运行相应的模型训练脚本
3. 使用训练好的模型进行预测

### 大语言模型预测
1. 准备自然语言格式的输入
2. 使用微调后的模型进行推理
3. 获得自然语言格式的预测结果

## 贡献指南

欢迎对本项目进行贡献！请遵循以下步骤：

1. Fork本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启Pull Request

## 许可证

本项目采用MIT许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

## 联系方式

如有问题或建议，请通过以下方式联系：

- 项目Issues: [GitHub Issues](https://github.com/your-username/LLMs-BiocharPredict/issues)
- 邮箱: pjf1028@163.com

## 致谢

感谢所有为本项目做出贡献的研究人员和开发者。

## 引用

如果您在研究中使用了本项目，请引用：

```bibtex
@misc{llms-biochar-predict,
  title={LLMs-BiocharPredict: A Large Language Model Approach for Biochar Property Prediction},
  author={Your Name},
  year={2024},
  url={https://github.com/your-username/LLMs-BiocharPredict}
}
```
