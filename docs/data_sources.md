# **DreamClass Intelligence Suite — Data Sources**

This document lists the major data sources that will feed into the Intelligence Suite, what they contain, and how they will be used.

---

## **1\. GA4 (Google Analytics 4\)**

### **Type: Web analytics**

### **Grain: Event-level**

### **Examples of data:**

* Pageviews

* Sessions

* Events (sign\_up click, video views, contact form, etc.)

* Campaign attribution

* Device / location

* Traffic channels

### **How we will use it:**

* Top-of-funnel traffic insights

* Detection of shifts in marketing effectiveness (XmR)

* Enrichment of LQI context (lead quality vs traffic source)

* Feeding SwanAI/G2 enrichment signals into company-level analytics

### **Ingestion:**

* Native GA4 → BigQuery export (ideal)

* Or periodic API pulls

---

## **2\. DreamClass Backend Events**

### **Type: Product usage analytics**

### **Grain: Event-level (user or account actions)**

### **Examples:**

* Account created

* Classes created

* Students added

* Billing page viewed

* Email invitations sent

* Feature-specific actions

### **How used:**

* Activation scoring

* Product-led growth analysis

* XmR for activation stability

* Predictive churn/upgrade modeling later

### **Ingestion:**

* Custom REST API → BigQuery script

* Scheduled job (simple cron or GitHub action)

---

## **3\. ChartMogul / Stripe**

### **Type: Subscription \+ revenue**

### **Grain: Subscription, invoice, event**

### **Examples:**

* MRR

* Churn events

* Expansion events

* Trial-to-paid conversion

* Invoices

* Plan-level metrics

### **How used:**

* Financial XmR charts (net new MRR, churn volatility)

* Cohort revenue analysis

* Understanding the revenue consequences of lead quality

### **Ingestion:**

* API loader (Stripe or ChartMogul API)

* Store into `subscriptions` and `invoices` tables

---

## **4\. CRM Data (if available)**

### **Type: Lead → opportunity → customer pipeline**

### **Grain: Lead-level or company-level**

### **Examples:**

* Lead qualification

* Sales stages

* Notes and outcomes

* Close win/loss reasons

### **How used:**

* Sales pipeline XmR

* Correlation between website behavior and sales outcomes

* Empirical definitions for high-value leads

### **Ingestion:**

* REST API → BigQuery

* Or CSV/manual imports initially

---

## **5\. Lead Scoring (Supabase)**

### **Type: Lead quality evaluations**

### **Grain: Per scoring run (2-week window), and per-row**

### **Metrics:**

* Class distribution

* LQI (Lead Quality Index)

* Total leads

* Lead class per individual lead

### **How used:**

* XmR charts (already proven valuable)

* Marketing quality tracking

* Predictive enrichment later

### **Ingestion:**

* Copy from Supabase → BigQuery via Python script

---

## **6\. SwanAI / G2 Company Identification**

### **Type: Visitor enrichment**

### **Grain: Company-level**

### **Examples:**

* Company name

* Company size

* Tech stack

* Vertical

* Identified visit patterns

* Buyer intent signals

### **How used:**

* Connect anonymous web traffic to actual companies

* Identify high-value companies early

* Attribute LQI changes to meaningful sources

* Improve trial conversion forecasting

### **Ingestion:**

* API → BigQuery

* Small daily batch jobs

---

## **7\. Internal Supporting Tables**

* `companies` (canonical identity table merging CRM \+ SwanAI \+ billing)

* `dim_dates` (date dimension for time-series joins)
