# UNBench Reproducibility Study
## FTEC5660 – Agentic AI for Business and FinTech

This repository reproduces **Task 1 (Co-Penholder Judgement)** from the paper:
> **"Benchmarking LLMs for Political Science: A United Nations Perspective"**  
> Liang et al., arXiv:2502.14122

We evaluate **DeepSeek-V3** on multi-choice political reasoning tasks and test a **modified prompt design** with domain-specific reasoning examples.

---

## Repository Structure

- README.md (This file)
- Reproducibility report.pdf (Detailed reproducibility report)
- original_task1.ipynb (Original UNBench Task 1 code)
- Reproduction.ipynb (Modified version with enhanced prompt)
- task1.json (Task 1 test data - 30 instances)

---

## 🎯 Reproduction Target

**Task 1: Co-Penholder Judgement**  
Given a draft resolution and candidate countries, select the most appropriate co-author country.

We reproduce DeepSeek-V3 accuracy from **Table 6** of the original paper for:
- 2-choice, 3-choice, 4-choice, 5-choice tasks

---

## ⚙️ Setup Instructions

### 1. Environment Setup

git clone https://github.com/yueqingliang1/UNBench.git
cd UNBench
pip install -r requirements.txt
pip install langchain-openai openai tqdm

### 2. API Key Configuration

This project uses the **DeepSeek API** (OpenAI-compatible). Set your API key:

**Option A: Google Colab Secrets**
from google.colab import userdata
api_key = userdata.get("DEEPSEEK_API_KEY")

**Option B: Environment Variable**
export DEEPSEEK_API_KEY="your-api-key-here"

Get your API key from: https://platform.deepseek.com

---

## 🧪 Running the Experiments

### Original Reproduction (original_task1.ipynb)
- Runs Task 1 with the original prompt template from the paper
- Evaluates DeepSeek-V3 on 2/3/4/5-choice tasks
- Outputs accuracy metrics for comparison

### Modified Experiment (Reproduction.ipynb)
- Enhanced prompt with domain-specific reasoning examples:
  - Climate change → environmentally active countries
  - Security issues → permanent members with military influence
  - Regional issues → regional actors
- Strict output rules to prevent invalid responses
- Same evaluation protocol for direct comparison

---

## 📊 Results Summary

| Choices | Paper (Original) | Reproduced (Original) | Modified Prompt |
|---------|------------------|------------------------|-----------------|
| 2       | 0.695            | 0.567                  | 0.567           |
| 3       | 0.555            | 0.400                  | 0.500           |
| 4       | 0.443            | 0.333                  | 0.333           |
| 5       | 0.422            | 0.367                  | 0.367           |

**Key Finding**: Modified prompt improved 3-choice accuracy by **+10%** (0.400 → 0.500)

---

## 📈 Key Findings

- **Trend reproducible**: All runs show decreasing accuracy as choices increase
- **Prompt engineering matters**: Domain-specific examples significantly improved mid-complexity tasks
- **Invalid responses**: Modified prompt eliminated organization names (e.g., "Group of Arab States")
- **Limitations**: 30 test instances vs. 355,126 in full dataset → results not directly comparable

---

## 📎 Submission Information

- **Student Name**: [Chen Jiaxin]
- **Student ID**: [1155246854]
- **Course**: FTEC5660 – Agentic AI for Business and FinTech
- **Date**: March 2025

---

## 📽️ Presentation

A 15-minute recorded presentation is available at:  
[Insert Zoom/YouTube/Panopto link here]

---

## 📚 References

[1] Liang, Y., Yang, L., Wang, C., Xia, C., Meng, R., Xu, X., Wang, H., Payani, A., & Shu, K. (2025). Benchmarking LLMs for Political Science: A United Nations Perspective. arXiv preprint arXiv:2502.14122.

[2] UNBench GitHub Repository: https://github.com/yueqingliang1/UNBench
