# 🕵️ Graph Neural Network Fraud Detection with LLM Explanations

An end-to-end AI-powered fraud detection system combining Graph Neural Networks (GNN) with LLM-based investigation explanations and an interactive Tableau analytics dashboard.

This project demonstrates how graph-based machine learning can uncover relational fraud patterns and how LLMs can translate model outputs into human-readable fraud investigation insights.

---

## 📌 Project Overview

Traditional fraud detection systems rely on tabular machine learning models. However, many financial fraud schemes rely on relationships between transactions, which tabular models fail to capture.

This project models transactions as a graph network and uses a Graph Neural Network (GraphSAGE) to detect suspicious behavior patterns.

The system then generates AI-generated investigation summaries using an LLM to help analysts interpret why a transaction was flagged.

---

## 🏗️ System Architecture
```
Transaction Dataset
        ↓
Feature Engineering
        ↓
Hybrid Graph Construction
        ↓
Graph Neural Network (GraphSAGE)
        ↓
Fraud Risk Scoring
        ↓
Suspicious Transaction Detection
        ↓
LLM Investigation Explanations (Groq API)
        ↓
Interactive Fraud Analytics Dashboard (Tableau)
```

---

## 📊 Dataset

Dataset used:

[European Cardholder Credit Card Fraud Dataset](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)

Features include anonymized PCA-transformed attributes (V1–V28), transaction time, and transaction amount.

The dataset is highly imbalanced:

- 🔴 Fraud Transactions: 492
- 🟢 Normal Transactions: 284,315

This imbalance makes fraud detection particularly challenging and highlights the importance of graph-based approaches.

---

## ⚙️ Feature Engineering

Additional behavioral features were created including:

- Transaction hour
- Night transaction indicator
- Log-transformed transaction amount
- Graph node degree
- Neighbor fraud ratio

These features help capture behavioral and relational patterns associated with fraud.

---

## 🕸️ Graph Construction

Transactions were converted into a hybrid similarity graph using multiple relationship rules.

Edges were created based on:

- KNN similarity in feature space
- Time proximity
- Similar transaction amounts
- Shared behavioral patterns

This hybrid graph structure allows the model to detect clusters of suspicious activity rather than isolated anomalies.

---

## 📐 Baseline Models

To benchmark performance, several traditional machine learning models were trained:

- Logistic Regression
- Random Forest
- Gradient Boosting

Performance comparison showed that the Graph Neural Network achieved stronger relational pattern detection, especially for clustered fraud behaviors.

---

## 🧠 Graph Neural Network Model

The core model uses GraphSAGE, implemented with PyTorch Geometric.

The GNN learns representations for transactions by aggregating information from neighboring nodes in the transaction graph.

This allows the model to detect:

- Coordinated fraud activity
- Transaction similarity patterns
- Suspicious transaction neighborhoods

---

## 📈 Model Evaluation

Evaluation metrics used:

- Precision
- Recall
- F1 Score
- ROC-AUC
- PR-AUC

The GNN achieved strong separation between fraudulent and legitimate transactions and improved detection of relational fraud patterns.

---

## 🎯 Fraud Risk Scoring

Each transaction receives a risk score between:

- `0` → Low fraud probability
- `1` → High fraud probability

High-risk transactions are then passed to the LLM explanation layer for investigation summaries.

---

## 🤖 LLM Fraud Investigation Layer

To make model outputs interpretable, the system generates fraud investigation explanations using an LLM via the Groq API.

The LLM analyzes:

- Transaction details
- Graph connectivity
- Fraud neighborhood density
- Risk score

And produces structured outputs such as:

- Risk Summary
- Why It Was Flagged
- Possible Fraud Pattern
- Recommended Investigator Action

### 💬 Sample LLM Output

<img width="1362" height="383" alt="image" src="https://github.com/user-attachments/assets/d3ea934e-04bc-48ac-a21b-8e0d94ec8d7c" />

### 📁 Additional LLM Outputs

More generated explanations can be found in the CSV file:

`fraud_ai_explanations_groq.csv`

This file contains explanations generated for multiple high-risk transactions.

---

## 📊 Fraud Analytics Dashboard

The results are visualized in an interactive Tableau dashboard designed for fraud analysts.

Dashboard features include:

- Fraud risk distribution
- Transaction amount vs risk score visualization
- Fraud activity patterns by hour
- High-risk transaction exploration

<img width="1918" height="927" alt="image" src="https://github.com/user-attachments/assets/eff6545a-9ad5-4fea-af7a-9844a2a09533" />

---

## 🖼️ Additional Visuals

### 🔗 Risk Level Breakdown

<img width="667" height="747" alt="image" src="https://github.com/user-attachments/assets/10f09630-029b-4d18-a953-7cfc40cd044f" />


### 📉 Fraud Risk Score Distribution

<img width="950" height="763" alt="image" src="https://github.com/user-attachments/assets/d1c3857b-bfa8-4adf-9f4d-3216195aadb4" />

### 💰 Amount vs Risk Scatter Plot

<img width="928" height="750" alt="image" src="https://github.com/user-attachments/assets/d88ca822-e722-4083-b888-dd3ca9fa29da" />

---

## 🛠️ Technologies Used

| Tool | Purpose |
|---|---|
| Python | Core language |
| Pandas | Data processing |
| Scikit-Learn | Baseline models |
| NetworkX | Graph construction |
| PyTorch + PyTorch Geometric | GNN implementation |
| Groq API | LLM explanations |
| Matplotlib | Visualizations |
| Tableau | Analytics dashboard |

---

## 🗂️ Repository Structure
```
fraud-gnn-detection
│
├── notebooks
│   └── fraud_gnn_pipeline.ipynb
│
├── outputs
│   ├── fraud_tableau_dataset.csv
│   └── fraud_ai_explanations_groq.csv
│
├── dashboard
│   └── tableau_dashboard_screenshot.png
│
├── requirements.txt
└── README.md
```

---

## ✅ Key Contributions

This project demonstrates:

- Graph-based fraud detection using GNNs
- Hybrid transaction relationship modeling
- Integration of ML predictions with LLM explanations
- Interactive fraud investigation dashboards

The system combines machine learning, graph analytics, and generative AI to create a practical fraud investigation tool.

---

## 🔭 Future Improvements

Potential extensions include:

- Real-time fraud detection pipelines
- Heterogeneous financial entity graphs (accounts, devices, merchants)
- Temporal graph neural networks
- Investigator feedback loops for model improvement
- Deployment as a web-based investigation tool

---
