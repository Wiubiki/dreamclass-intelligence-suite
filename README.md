# DreamClass Intelligence Suite

The **DreamClass Intelligence Suite** is a unified analytics and data platform designed to centralize marketing, product usage, revenue, and lead-quality data into a single, coherent system. Its goal is simple:

> **Provide DreamClass with reliable, stable, and actionable intelligence across the entire customer lifecycle.**

This project forms the foundation for descriptive, diagnostic, and stability-based analytics (e.g., XmR charts), with optional predictive capabilities in later phases.

---

## 🚀 Why This Project Exists

DreamClass has multiple strong data sources:
- GA4  
- DreamClass backend  
- Stripe/ChartMogul  
- CRM  
- Supabase Lead Scoring App  
- Visitor intelligence (SwanAI, G2, etc.)

But today, these sources live in isolation.

This leads to gaps:
- No unified view of the funnel from website → trial → activation → subscription → revenue  
- No consistent metric definitions  
- No central data warehouse  
- No way to track process stability across systems  
- Limited ability to enrich anonymous website traffic into actionable company intelligence  

The Intelligence Suite addresses these issues by building one **analytics backbone**.

---

## 🎯 Project Goals (Phase 1)

### **1. Build a Central Data Warehouse in BigQuery**
A unified place for:
- Web analytics  
- Product events  
- Lead scoring runs + LQI  
- Subscription & revenue data  
- CRM pipeline stages  
- Visitor enrichment  

### **2. Define Stable Data Models**
Clear schemas for:
- `events_web`  
- `events_product`  
- `subscriptions`  
- `leads`  
- `lead_scoring_runs`  
- `visitor_enrichment`  
- `companies` (canonical identity table)

### **3. Simple, Reliable Data Pipelines**
Start small:
- GA4 → BigQuery native export  
- Python loaders for DreamClass backend, Supabase, ChartMogul/Stripe, SwanAI  
- Scheduled jobs (cron, GitHub Actions)

### **4. Establish Core Metrics**
Stable definitions for:
- Trials  
- Activation  
- Conversion  
- LQI (Lead Quality Index)  
- MRR, churn, expansion  
- Cohorts  

### **5. Build the First Analytical Layer**
Before dashboards, define:
- Aggregations  
- Timeseries  
- Stability metrics (XmR logic reused from Lead Scoring App)

---

## 🔭 Phase 2 Vision (Future)

After the foundation is solid:

### **Unified Analytics Dashboard**
A Streamlit-based internal tool combining:
- LQI XmR trends  
- Marketing conversion XmR  
- Activation rate XmR  
- Subscriber/revenue XmR  
- SwanAI/G2 company intelligence  
- Funnel analytics  
- Product usage–driven insights  

### **Predictive Models (Optional Later)**
- Churn prediction  
- Upgrade likelihood  
- High-value company detection  
- Performance forecasting  

Prediction is not the goal — it’s an optional layer once the fundamentals are strong.

---

## 🧩 Repository Structure
dreamclass-intelligence-suite/  
│  
├── README.md  
├── docs/  
│ ├── project\_vision.md  
│ ├── data\_sources.md  
│ ├── warehouse\_schema.md (future)  
│ ├── metrics\_definitions.md (future)  
│ └── roadmap.md (future)  
│  
├── warehouse/  
│ └── sql/ (future: BQ staging \+ marts)  
│  
├── pipelines/  
│ └── load\_x\_to\_bq.py (future ingestion scripts)  
│  
├── apps/  
│ └── intelligence\_dashboard/ (later Streamlit app)  
│  
└── analytics/  
└── notebooks/ (experimentation & exploration)

---

## 📚 Documentation

Core planning documents are found under `docs/`:

- **project_vision.md** – high-level purpose & guiding principles  
- **data_sources.md** – all upstream systems and how they integrate  
- **warehouse_schema.md** – schema design (once drafted)  
- **metrics_definitions.md** – single source of truth for KPI definitions  
- **roadmap.md** – phased development plan  

These documents evolve as the suite expands.

---

## 🧱 Guiding Principles

- **Data-informed > data-driven.**  
  Data supports decisions; it doesn't replace judgment.

- **Build foundations before dashboards.**  
  Strong warehouse > pretty charts.

- **Stable metric definitions are sacred.**

- **Prefer boring, reliable tools over overcomplex solutions.**

- **Iterate in small steps.**  
  No big-bang analytics rewrites.

---

## 🛠 Tech Stack (Initial)

- **BigQuery** – central warehouse  
- **Python** – ingestion scripts  
- **Streamlit** – future apps & dashboards  
- **Supabase** – integration for lead scoring data  
- **SwanAI / G2** – visitor enrichment  

Potential additions later:
- dbt  
- Airbyte / Meltano  
- Looker Studio  

---

## 🤝 Contributions

This project is internal to DreamClass.  
Contributions are made via:
1. Updating docs  
2. Proposing schema changes  
3. Adding pipeline scripts  
4. Building analytics layers  
5. Opening issues for enhancements

---

## 🏁 Current Status

**Phase 1 – Planning & Foundation**  
- Vision defined  
- Data sources documented  
- Next step: Draft warehouse_schema.md  

---

# End of README


