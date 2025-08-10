# LLMs-BiocharPredict

简体中文 | English: [README_EN.md](./README_EN.md)

## 目录
- [LLMs-BiocharPredict](#llms-biocharpredict)
  - [目录](#目录)
  - [项目简介](#项目简介)
  - [论文与目的](#论文与目的)
  - [功能与特点](#功能与特点)
  - [仓库内容](#仓库内容)
  - [环境与安装](#环境与安装)
  - [快速开始](#快速开始)
  - [数据与文件说明](#数据与文件说明)
  - [复现实验与推荐流程](#复现实验与推荐流程)
  - [贡献指南](#贡献指南)
  - [行为准则](#行为准则)
  - [安全策略](#安全策略)
  - [许可证](#许可证)
  - [引用本项目](#引用本项目)
  - [联系方式](#联系方式)

## 项目简介
本项目是面向生物炭性质预测的开源研究性仓库，提供与论文配套的代码与数据。项目结合传统机器学习与大语言模型（LLMs），用于预测生物炭的多种性质（如产量、比表面积、灰分、CHNO元素、pH、粒径等），并给出完整的数据处理与训练评估流程。

## 论文与目的
- 本仓库为论文的支撑代码与数据，用于帮助读者复现实验结果，并便于社区二次开发与扩展。
- 如需在论文中引用本仓库，请参考文末的“引用本项目”部分。

## 功能与特点
- 多任务预测：支持产量、比表面积、灰分、CHNO元素、pH、粒径等目标。
- 传统+深度：集成 XGBoost、随机森林、ANN 等模型；提供 LLM 微调准备与示例。
- 完整流程：数据分类/重提取/缺失值填补/问答对生成/训练与评估的端到端链路。
- 复现友好：提供明确的依赖文件与复现步骤说明。

## 仓库内容
- 核心笔记本
  - `ML.ipynb`：机器学习模型训练与评估（XGBoost、RF、ANN 等）
  - `Q&A pair generation.ipynb`：面向 LLM 微调的问答对构建
  - `Data classification.ipynb`：按性质对数据进行分类/抽取
  - `Projected supplementary data.ipynb`：缺失值填补与数据补充
  - `Re-extraction of data.ipynb`：从 JSON 等格式重提取训练数据至 CSV
  - `Second round of fine-tuning preparations.ipynb`：二轮微调数据准备（如 60/40 划分）
- 数据文件
  - `First round of training set and validation set data.csv`：第一轮训练+验证集
  - `First round of test set data and second round of training and test set data.csv`：第一轮测试集与第二轮训练/测试集
- 项目治理与文档
  - `requirements.txt`：核心依赖
  - `LICENSE`：开源许可证（MIT）
  - `CONTRIBUTING.md`：贡献指南
  - `CODE_OF_CONDUCT.md`：行为准则
  - `SECURITY.md`：安全策略与漏洞报告方式
  - `docs/`：扩展文档（可选）

## 环境与安装
- 推荐环境：Python 3.8+（建议使用虚拟环境）
- 可选：NVIDIA GPU + CUDA（用于深度学习/LLM 微调与推理加速）

在 Windows PowerShell 中：
```powershell
# 克隆仓库
git clone https://github.com/SinceraXY/LLMs-BiocharPredict.git
cd LLMs-BiocharPredict

# 创建并激活虚拟环境
py -m venv .venv
.\.venv\Scripts\Activate.ps1

# 安装依赖
pip install -r requirements.txt
```

如需使用 Conda：
```bash
conda create -n biochar python=3.10 -y
conda activate biochar
pip install -r requirements.txt
```

提示：若需 GPU 加速的 PyTorch，请根据硬件/驱动选择合适的 CUDA 对应版本安装。

## 快速开始
1) 打开 Jupyter（或 VS Code/Notebook 环境）
```bash
jupyter notebook
```
2) 按“复现实验与推荐流程”章节的顺序依次运行笔记本。
3) 在 `ML.ipynb` 中训练传统机器学习模型，并记录评估指标。
4) 使用 `Q&A pair generation.ipynb` 生成 LLM 微调所需的问答对（JSON）。

## 数据与文件说明
- 本仓库包含两份主要 CSV 数据用于训练/验证/测试，文件均位于仓库根目录，文件名如上所列。
- 数据字段：包含原料特性（如生物质类型、来源、预处理等）、工艺参数（温度、加热速率、停留时间等）与目标性质（产量、比表面积、灰分、CHNO、pH、粒径等）。
- 若需从原始 JSON 或其他格式重建 CSV，可使用 `Re-extraction of data.ipynb`。

## 复现实验与推荐流程
建议按照以下顺序运行，以获得与论文一致或可比的结果：
1. `Re-extraction of data.ipynb`（若需）
2. `Data classification.ipynb`
3. `Projected supplementary data.ipynb`
4. `Q&A pair generation.ipynb`
5. `ML.ipynb`
6. `Second round of fine-tuning preparations.ipynb`

说明：
- 缺失值填补建议参考笔记本中的 AutoGluon 设置与报告的验证指标。
- LLM 微调示例与推理仅提供最小可行范式，具体训练参数与硬件资源需按实际环境调整。

## 贡献指南
欢迎提交 Issue 与 Pull Request 改进本项目（修复问题、完善文档、扩展功能等）。
- 贡献流程与规范请见：[CONTRIBUTING.md](./CONTRIBUTING.md)

## 行为准则
本项目遵循开源社区基本礼仪，详情参见：[CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md)

## 安全策略
如发现安全问题或潜在漏洞，请参考：[SECURITY.md](./SECURITY.md)

## 许可证
- 代码遵循 MIT 许可证，见：[LICENSE](./LICENSE)
- 若数据另有许可条款，请在引用或再分发时遵循相应要求（如有疑问，请在 Issue 中与我们沟通）。

## 引用本项目
如本项目或其数据/模型对你的研究或产品有帮助，请引用：

```text
@software{LLMs-BiocharPredict,
  title        = {LLMs-BiocharPredict: Biochar Property Prediction with ML and LLMs},
  author       = {SinceraXY and Contributors},
  year         = {2025},
  url          = {https://github.com/SinceraXY/LLMs-BiocharPredict},
  note         = {Code and data accompanying the paper}
}
```

如有正式论文信息（作者、题目、期刊/会议、DOI 等），建议在此处补充标准 BibTeX 或提供 `CITATION.cff`。

## 联系方式
- 提交 Issue：请在 GitHub 仓库发起问题反馈与讨论
- 邮件联系：2952671670@qq.com

---

本项目旨在推动生物炭性质预测研究的可复现与可扩展，促进可持续能源与环境保护相关应用的发展。
