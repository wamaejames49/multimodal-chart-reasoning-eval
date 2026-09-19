# Multi-Step Multimodal Reasoning Benchmark: Chart Data

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Domain: Multimodal AI Evaluation](https://img.shields.io/badge/Domain-Vision--Language--Reasoning-blue)](#)
[![Dataset Format: ChartQA / MMMU Compatible](https://img.shields.io/badge/Format-JSON%20Benchmark-brightgreen)](#)

This repository demonstrates the design of a rigorous, non-OCR, multi-step graphical reasoning evaluation item. It is modeled after industry standards used to train and evaluate Vision-Language Models (VLMs) and AI benchmark suites (e.g., ChartQA, MathVista, MMMU).

---

## 🎯 Task Overview

Simple chart VQA tasks often fail to test genuine reasoning because models can answer via text optical character recognition (OCR) or single data point lookup. 

This test item tests **latent variable derivation**, **dual-axis synchronization**, and **multi-period temporal aggregation**.

---

## 📊 Exhibit Description: TechCorp Quarterly Performance (2022–2024)

- **Chart Type**: Dual-axis combo chart (Bar + Line)
- **Primary Axis (Left, Bar)**: Quarterly Revenue in Millions USD ($M), range `0–200`
- **Secondary Axis (Right, Line)**: Operating Margin percentage (%), range `0%–30%`
- **X-Axis**: 12 Quarters (`Q1 2022` to `Q4 2024`)

---

## ❓ Benchmark Question

> **Question:**  
> What is the difference, in millions of dollars, between TechCorp’s total operating income in the second half of 2023 (Q3 and Q4 combined) and its total operating income in the first half of 2023 (Q1 and Q2 combined)?  
> *(Note: Calculate Operating Income as $\text{Revenue} \times \text{Operating Margin}$. Express your answer in millions of dollars rounded to two decimal places).*

---

## 🧠 Step-by-Step Reasoning Path

```text
Step 1: Multi-Axis Data Extraction (FY 2023)
  ├── Q1 2023: Revenue = $105M  |  Operating Margin = 15% (0.15)
  ├── Q2 2023: Revenue = $118M  |  Operating Margin = 18% (0.18)
  ├── Q3 2023: Revenue = $130M  |  Operating Margin = 20% (0.20)
  └── Q4 2023: Revenue = $150M  |  Operating Margin = 22% (0.22)

Step 2: Latent Metric Derivation (Operating Income = Revenue × Margin)
  ├── Q1 Operating Income: $105M × 0.15 = $15.75M
  ├── Q2 Operating Income: $118M × 0.18 = $21.24M
  ├── Q3 Operating Income: $130M × 0.20 = $26.00M
  └── Q4 Operating Income: $150M × 0.22 = $33.00M

Step 3: Semi-Annual Aggregation
  ├── First Half (H1 2023) = $15.75M + $21.24M = $36.99M
  └── Second Half (H2 2023) = $26.00M + $33.00M = $59.00M

Step 4: Comparative Difference
  └── H2 Total - H1 Total = $59.00M - $36.99M = $22.01M
