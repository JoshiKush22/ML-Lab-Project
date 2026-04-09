# ML Lab Project: CICIDS-2018 Network Intrusion Detection

ML pipeline for network intrusion detection using the CICIDS-2018 dataset. This project processes large-scale network traffic data to effectively detect and classify modern network attacks, leveraging XGBoost for feature selection and building a powerful Random Forest + XGBoost ensemble model that achieves up to 98% accuracy.

## Overview

The primary goal of this repository is to establish a strong data foundation and machine learning pipeline for building an Intrusion Detection System (IDS). Because of the massive scale of the daily network packet captures in the CICIDS-2018 dataset, this code demonstrates how to handle Big Data constraints effectively by:
- Loading multiple massive daily capture logs efficiently via `pandas` chunking.
- Down-sampling to a representative subset for quicker iterative modeling.
- Handling unprocessable noise like missing values and infinity bounds.
- Normalizing targets and feeding them into tree-based ensemble models.

## Repository Contents

- **`CICIDS_IDS_Cleaned.ipynb`**: A Jupyter Notebook executing the data preparation pipeline.
  - **Part 1**: Environment Setup & Data Loading. It iterates through raw CSV chunks and merges a clean subset.
  - **Part 2**: Data Preprocessing & Cleaning. Exploring labels, target distributions, and preparing shapes for supervised Machine Learning models.

## Dataset Properties & Attack Vectors

The dataset contains comprehensive network flow records detailing benign and attack traffic patterns.
Attack classifications targeted by this pipeline include (but are not limited to):
- **DDoS** (HOIC, LOIC)
- **DoS** (Hulk, GoldenEye, Slowloris, SlowHTTPTest)
- **Brute Force** (FTP, SSH, Web, XSS)
- **Botnet** Activity
- **Infiltration**
- **SQL Injection**

## Getting Started

To reproduce the preprocessing workflow, especially in a cloud environment like Google Colab:
1. Mount your Google Drive to your active session.
2. Make sure the original CIC-IDS-2018 daily `.csv` files are located within your specified cloud storage directory.
3. Run the notebook successfully top-to-bottom. It will safely stream, sample, and output a cleaned master file suitable for your end-to-end classification pipeline.

## Performance
The advanced predictive pipeline utilizes XGBoost-driven feature selection to hone in on the most crucial network flow indicators, which are then modeled through an ensembled configuration of Random Forest & XGBoost, ultimately reaching robust classification figures of **~98% Accuracy** across diverse attack vectors.
