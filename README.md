# 🛰️ AI Network Monitoring System

> ML-based anomaly detection pipeline for satellite network telemetry using Isolation Forest — achieving **92% detection accuracy** with automated observability reporting.

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=flat-square&logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.4-orange?style=flat-square&logo=scikit-learn)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?style=flat-square&logo=pandas)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)

---

## 📌 Overview

Traditional threshold-based network monitoring fails to capture complex, multi-dimensional anomalies in satellite telemetry. This system addresses that gap by applying **unsupervised machine learning** (Isolation Forest) to detect anomalies across key signal metrics — without requiring labeled training data.

The pipeline ingests raw telemetry, preprocesses it with Pandas, runs anomaly scoring, and generates automated observability reports — making it production-ready for satellite network operations.

---

## 🚀 Features

- **Unsupervised Anomaly Detection** — Isolation Forest model trained on multivariate satellite telemetry with no labeled data required
- **Multi-metric Analysis** — Monitors Latency (ms), Signal-to-Noise Ratio (SNR dB), and Packet Loss (%) simultaneously
- **Automated Observability Reports** — Generates structured HTML/CSV reports with timestamped anomaly logs
- **92% Detection Accuracy** — Validated against synthetically injected fault scenarios
- **Scalable Preprocessing Pipeline** — Pandas-based ETL handles missing values, outlier normalization, and feature engineering

---

## 🏗️ Architecture

```
Raw Telemetry Data (CSV)
        │
        ▼
┌───────────────────┐
│  Data Ingestion   │  ← Pandas read + schema validation
└───────────────────┘
        │
        ▼
┌───────────────────┐
│  Preprocessing    │  ← Null handling, normalization, rolling stats
└───────────────────┘
        │
        ▼
┌───────────────────┐
│  Isolation Forest │  ← Unsupervised anomaly scoring
│  (Scikit-learn)   │     contamination=0.05, n_estimators=100
└───────────────────┘
        │
        ▼
┌───────────────────┐
│  Anomaly Labeling │  ← Score thresholding + severity classification
└───────────────────┘
        │
        ▼
┌───────────────────┐
│  Observability    │  ← Automated CSV + HTML report generation
│  Report Generator │
└───────────────────┘
```

---

## 🧪 Tech Stack

| Layer | Technology |
|---|---|
| Language | Python 3.10+ |
| ML Model | Scikit-learn — Isolation Forest |
| Data Processing | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Reporting | Jinja2 (HTML), CSV |
| Environment | pip / virtualenv |

---

## 📊 Telemetry Metrics

| Metric | Description | Normal Range |
|---|---|---|
| **Latency (ms)** | Round-trip signal delay | 200–600 ms |
| **SNR (dB)** | Signal-to-Noise Ratio | 15–35 dB |
| **Packet Loss (%)** | Percentage of dropped packets | 0–5% |

---

## 📁 Project Structure

```
ai-network-monitor/
├── data/
│   ├── raw/                    # Raw telemetry CSV files
│   └── processed/              # Cleaned, feature-engineered data
├── src/
│   ├── ingest.py               # Data ingestion & schema validation
│   ├── preprocess.py           # Pandas preprocessing pipeline
│   ├── model.py                # Isolation Forest training & scoring
│   ├── report.py               # Observability report generator
│   └── main.py                 # Entry point — runs full pipeline
├── reports/
│   ├── anomaly_report.csv      # Timestamped anomaly log
│   └── anomaly_report.html     # Visual observability dashboard
├── notebooks/
│   └── eda.ipynb               # Exploratory data analysis
├── requirements.txt
└── README.md
```

---

## ⚙️ Setup & Usage

### 1. Clone the repository
```bash
git clone https://github.com/HarshaVardhan-49/ai-network-monitor.git
cd ai-network-monitor
```

### 2. Create virtual environment
```bash
python -m venv venv
source venv/bin/activate        # Mac/Linux
venv\Scripts\activate           # Windows
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Run the pipeline
```bash
python src/main.py
```

### 5. View the report
```
reports/anomaly_report.html     # Open in browser
reports/anomaly_report.csv      # Raw anomaly log
```

---

## 📈 Model Performance

| Metric | Value |
|---|---|
| Anomaly Detection Accuracy | **92%** |
| False Positive Rate | ~6% |
| Model | Isolation Forest |
| Contamination Factor | 0.05 |
| Estimators | 100 trees |

> Accuracy validated against synthetically injected fault scenarios: latency spikes, SNR degradation, and packet loss bursts.

---

## 🔍 Sample Output

```
Timestamp               Latency(ms)  SNR(dB)  PacketLoss(%)  Anomaly  Severity
2025-01-15 10:23:45     850.4        8.2      18.7           YES      HIGH
2025-01-15 10:24:10     210.1        28.6     1.2            NO       -
2025-01-15 10:24:55     920.7        6.1      22.4           YES      HIGH
2025-01-15 10:25:30     198.3        31.2     0.8            NO       -
```

---

## 🛣️ Roadmap

- [ ] Real-time streaming ingestion via Kafka
- [ ] REST API wrapper (FastAPI) for live anomaly scoring
- [ ] Alerting integration (PagerDuty / Slack webhook)
- [ ] LSTM-based sequential anomaly detection
- [ ] Docker containerization

---

## 👤 Author

**Harsha Vardhan**
- LinkedIn: [www.linkedin.com/in/harsha-vardhan-dev07](https://www.linkedin.com/in/harsha-vardhan-dev07)
- GitHub: [github.com/HarshaVardhan-49](https://github.com/HarshaVardhan-49)

---

## 📄 License

This project is licensed under the MIT License.
