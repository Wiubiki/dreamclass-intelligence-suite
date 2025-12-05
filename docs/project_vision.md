# **DreamClass Intelligence Suite — Project Vision**

## **1\. Purpose**

The DreamClass Intelligence Suite aims to create a unified, scalable, and reliable analytics foundation for all marketing, product, and revenue intelligence at DreamClass.

This suite will bring together data from multiple operational systems, consolidate it into a central warehouse (BigQuery), enrich it with external intelligence (e.g., SwanAI/G2), and expose insights through lightweight analytical applications and dashboards.

The main purpose is simple:

**Give DreamClass the ability to understand how marketing, product usage, and revenue interact over time — and detect meaningful shifts early.**

Not predictive AI magic.  
 Not random dashboards.  
 Just **good analytics**, with **stable definitions**, built on **solid data infrastructure**.

---

## **2\. Why This Project Exists**

Right now, DreamClass has strong individual data sources (GA4, backend, billing, CRM, lead scoring), but they live in isolation.

This creates several limitations:

* No unified customer or company identity

* No holistic view of the marketing → trial → activation → subscription → revenue journey

* No way to reliably track process stability over time

* No ability to correlate product usage with lead quality

* No central place to perform real analytics without manual exports

The Intelligence Suite removes those barriers.

---

## **3\. Goals (Phase 1\)**

Phase 1 focuses on building **the foundation**, not on creating complicated dashboards.

### **3.1. Build a centralized data warehouse (BigQuery)**

A single place where:

* Web analytics

* Trial activity

* Subscription data

* Lead scoring outputs

* CRM data

* Visitor enrichment signals

…all exist with consistent schema, timestamps, and join keys.

### **3.2. Define a clear data model**

A small number of well-designed staging and analytics tables:

* `events_web`

* `events_product`

* `leads`

* `lead_scoring_runs`

* `visitor_enrichment`

* `subscriptions`

* `companies`

Each table has a clear purpose and grain.

### **3.3. Ingest data reliably**

Start simple:

* Native GA4 → BigQuery export

* Python scripts to load DreamClass backend data

* Supabase → BigQuery load for lead scoring

* Stripe/ChartMogul API loader

* SwanAI/G2 enrichment loader

Zero orchestration complexity in Phase 1\.

### **3.4. Establish core metrics**

A shared definitions document for:

* Trials

* Activated users

* Conversion rates

* LQI (Lead Quality Index)

* MRR / churn / expansion

* Feature adoption metrics

This prevents metric drift.

---

## **4\. Vision for Phase 2**

Once Phase 1 solidifies, Phase 2 introduces:

### **Unified analytical dashboards**

A Streamlit or BI-app that shows:

* LQI XmR

* Activation rate XmR

* Conversion rate XmR

* MRR XmR

* Visitor intelligence (SwanAI) integrated with trial behavior

* Marketing efficiency over time

* Product usage correlated with revenue outcomes

### **Predictive capabilities (optional later)**

* Lead → trial → subscription predictive scoring

* Churn risk

* Upgrade likelihood

* Cohort forecasting

But prediction comes *after* the basics.  
 This project avoids premature AI enthusiasm.

---

## **5\. Guiding Principles**

* **Data-informed, not data-dictated.**  
   Prediction is not the point — signal detection is.

* **Favor simplicity over abstraction.**  
   Use plain tables and SQL before fancy pipelines.

* **Stable definitions are sacred.**  
   A metric defined once should remain identical across applications.

* **Every dashboard must answer a decision-making question.**  
   No vanity charts.

* **Prefer iteration over grand design.**

---

## **6\. What This Project Is Not**

This suite is NOT:

* A machine learning platform

* A “single dashboard to rule them all”

* A real-time analytics engine

* A BI tool replacement

It’s the **analytics backbone** DreamClass needs for the next decade.
