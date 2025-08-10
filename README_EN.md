# LLMs-BiocharPredict

English | 简体中文: [README.md](./README.md)

## Table of Contents
- [Introduction](#introduction)
- [Paper and Purpose](#paper-and-purpose)
- [Features](#features)
- [Repository Structure](#repository-structure)
- [Environment and Installation](#environment-and-installation)
- [Quick Start](#quick-start)
- [Data and Files](#data-and-files)
- [Reproducibility Workflow](#reproducibility-workflow)
- [Contributing](#contributing)
- [Code of Conduct](#code-of-conduct)
- [Security Policy](#security-policy)
- [License](#license)
- [Cite this Work](#cite-this-work)
- [Contact](#contact)

## Introduction
This repository contains the code and data accompanying our paper on biochar property prediction. We integrate traditional machine learning (XGBoost, Random Forest, ANN) with Large Language Models (LLMs) to predict multiple biochar properties (yield, specific surface area, ash content, CHNO elements, pH, grain size), providing a complete workflow from data preparation to model training and evaluation.

## Paper and Purpose
- This repo serves as the companion code and dataset for the paper, facilitating reproducibility and community extensions.
- See “Cite this Work” for citation information.

## Features
- Multi-task prediction: yield, specific surface area, ash, CHNO, pH, grain size.
- Traditional ML + LLM preparation: classic models plus Q&A data generation for LLM fine-tuning.
- End-to-end workflow: data classification, re-extraction, imputation, Q&A generation, training, and evaluation.
- Reproducibility-first: pinned requirements and a recommended run order.

## Repository Structure
- Notebooks
  - `ML.ipynb`: Train and evaluate ML models (XGBoost, RF, ANN)
  - `Q&A pair generation.ipynb`: Build Q&A pairs for LLM fine-tuning
  - `Data classification.ipynb`: Classify/extract data by target properties
  - `Projected supplementary data.ipynb`: Missing value imputation and data enrichment
  - `Re-extraction of data.ipynb`: Re-extract data from JSON-like sources to CSV
  - `Second round of fine-tuning preparations.ipynb`: Prepare data for round-2 fine-tuning (e.g., 60/40 split)
- Data files
  - `First round of training set and validation set data.csv`
  - `First round of test set data and second round of training and test set data.csv`
- Project governance and docs
  - `requirements.txt`, `LICENSE`, `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`, `CITATION.cff`
  - `docs/` (optional)

## Environment and Installation
- Recommended: Python 3.8+ (virtual environment is encouraged)
- Optional: NVIDIA GPU + CUDA for deep learning/LLM acceleration

Windows PowerShell:
```powershell
# Clone the repo
git clone https://github.com/SinceraXY/LLMs-BiocharPredict.git
cd LLMs-BiocharPredict

# Create and activate venv
py -m venv .venv
.\.venv\Scripts\Activate.ps1

# Install dependencies
pip install -r requirements.txt
```

With Conda:
```bash
conda create -n biochar python=3.10 -y
conda activate biochar
pip install -r requirements.txt
```

Tip: For GPU-enabled PyTorch, follow the official installation matrix to match your CUDA/driver setup.

## Quick Start
1) Launch Jupyter (or VS Code/Notebook environment)
```bash
jupyter notebook
```
2) Follow the order in “Reproducibility Workflow”.
3) Train baseline models in `ML.ipynb` and record metrics.
4) Generate Q&A data in `Q&A pair generation.ipynb` for LLM fine-tuning.

## Data and Files
- Two CSVs at repo root are used for train/validation/test as listed above.
- Fields include feedstock characteristics (type, source, pretreatment), process parameters (temperature, heating rate, residence time), and targets (yield, surface area, ash, CHNO, pH, grain size).
- To rebuild CSV from raw JSON-like data, use `Re-extraction of data.ipynb`.

## Reproducibility Workflow
Recommended order for experiments:
1. `Re-extraction of data.ipynb` (if needed)
2. `Data classification.ipynb`
3. `Projected supplementary data.ipynb`
4. `Q&A pair generation.ipynb`
5. `ML.ipynb`
6. `Second round of fine-tuning preparations.ipynb`

Notes:
- For imputation, refer to AutoGluon settings and validation metrics in the notebooks.
- LLM fine-tuning/inference examples are minimal working baselines; adjust parameters and hardware settings accordingly.

## Contributing
We welcome issues and pull requests for bug fixes, documentation improvements, and feature additions.
- See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

## Code of Conduct
Please read and follow our [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md).

## Security Policy
Security issues or potential vulnerabilities should follow the instructions in [SECURITY.md](./SECURITY.md).

## License
- Code is released under the MIT License: see [LICENSE](./LICENSE)
- If the data carries additional terms, please follow those when reusing or redistributing.

## Cite this Work
If this repository or its data/models help your research or product, please cite:

```text
@software{LLMs-BiocharPredict,
  title        = {LLMs-BiocharPredict: Biochar Property Prediction with ML and LLMs},
  author       = {SinceraXY and Contributors},
  year         = {2025},
  url          = {https://github.com/SinceraXY/LLMs-BiocharPredict},
  note         = {Code and data accompanying the paper}
}
```

For formal paper details (authors, title, venue, DOI), please add BibTeX here or maintain `CITATION.cff`.

## Contact
- Issues: open a ticket on GitHub
- Email: 2952671670@qq.com

---

This project aims to advance reproducible and extensible research in biochar property prediction relevant to sustainable energy and environmental protection. 