# 👥 Customer Analysis

A comprehensive **customer analytics** project focusing on **EDA, segmentation (K‑Means/RFM), cohort analysis, and CLV**.  
Includes clean, reproducible pipelines for data preprocessing, feature engineering, **segmentation & profiling**, and **retention insights** to drive marketing and product decisions.

---

## 📖 Overview
This repository turns raw customer and transaction data into actionable insights:
- **Exploratory Data Analysis (EDA)** — distributions, correlations, anomalies  
- **Segmentation** — RFM metrics and **K‑Means** clustering with clear profiles  
- **Cohort Analysis** — retention curves by acquisition month  
- **Customer Lifetime Value (CLV)** — simple heuristic and probabilistic models  
- **Churn Risk Signals** — early‑warning indicators from behavior & recency

---

## 🗂️ Dataset
Typical CSV layout under `data/`:
```
data/
├─ customers.csv           # customer_id, join_date, demographics (optional)
├─ transactions.csv        # customer_id, date, amount, product/category
└─ events.csv              # (optional) sessions, clicks, support tickets
```
> Adjust to your source. Ensure consistent `customer_id` and timestamp formats.

---

## 🔧 Feature Engineering
- **RFM** — `Recency`, `Frequency`, `Monetary` features per customer  
- **Activity** — sessions, days active, avg basket size, product diversity  
- **Time Windows** — 30/60/90‑day aggregates, rolling spend, last purchase gap  
- **Demographics** (optional) — age bucket, region, device

---

## 🧠 Methods
- **K‑Means** clustering on standardized RFM/behavioral vectors (with elbow/silhouette selection)  
- **RFM Scoring** (1–5 bins) and segment naming (e.g., Champions, Loyal, At Risk)  
- **Cohort Retention** — by acquisition month; survival curves (Kaplan‑Meier optional)  
- **CLV** — heuristic (avg margin × expected orders) and/or BG/NBD + Gamma‑Gamma (optional)

---

## 📈 Outputs & Dashboards
- **Segment profiles** — size, ARPU, order rate, churn risk  
- **Retention plots** — cohort heatmaps, week‑over‑week/month‑over‑month curves  
- **Revenue drivers** — category contribution, AOV trends, upsell potential  
- **Actionable lists** — high‑value at‑risk customers, cross‑sell candidates

---

## 🧩 Repository Structure (suggested)
```
Customer-Analysis/
├─ notebooks/
│  ├─ 01_eda.ipynb
│  ├─ 02_rfm_segmentation.ipynb
│  ├─ 03_kmeans_and_profiles.ipynb
│  ├─ 04_cohort_and_retention.ipynb
│  └─ 05_clv.ipynb
├─ src/
│  ├─ data.py          # loading/cleaning; type casting
│  ├─ features.py      # RFM & behavioral features
│  ├─ segment.py       # K-Means + profiling utilities
│  ├─ cohort.py        # retention matrices/plots
│  ├─ clv.py           # simple CLV or BG/NBD + Gamma-Gamma
│  └─ viz.py           # common plotting helpers
├─ reports/figures/    # saved charts: cohorts, segments, trends
├─ data/               # (gitignored) raw/processed
├─ requirements.txt
├─ .gitignore
└─ README.md
```

---

## ⚙️ Setup & Usage
1) **Clone & install**
```bash
git clone https://github.com/ziaee-mohammad/Customer-Analysis.git
cd Customer-Analysis
pip install -r requirements.txt
```

2) **Run notebooks in order** (EDA → RFM → K‑Means → Cohorts → CLV)
```bash
jupyter notebook
```

3) **(Optional) Scripts**  
If you modularize:
```bash
python -m src.segment --k 4 --rfm
python -m src.cohort  --freq monthly
python -m src.clv     --method heuristic
```

---

## 📦 Requirements (example)
```
pandas
numpy
scikit-learn
matplotlib
seaborn
lifelines      # optional: survival/retention
```
> If you use probabilistic CLV: add `lifetimes` or implement BG/NBD + Gamma‑Gamma

---

## ✅ Good Practices
- Use consistent timezones; ensure monotonic timestamps  
- Standardize features before **K‑Means**; pick `k` with elbow/silhouette  
- Document business mapping from segment → action (e.g., coupons for “At Risk”)  
- Save segment assignments and profiles (`reports/`) for stakeholders

---

## 🏷 Tags
```
data-science
customer-analytics
segmentation
rfm
k-means
cohort-analysis
retention
clv
python
jupyter-notebook
```

---

## 👤 Author
**Mohammad Ziaee** — Computer Engineer | AI & Data Science  
📧 moha2012zia@gmail.com  
🔗 https://github.com/ziaee-mohammad

---

## 📜 License
MIT — free to use and adapt with attribution.
