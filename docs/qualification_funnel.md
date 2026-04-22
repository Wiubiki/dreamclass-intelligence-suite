# Qualification Funnel

## Purpose

This document defines the **first analytical use case** for the DreamClass Intelligence Suite.

For now, the qualification funnel work is based on two main inputs:

* **GA4 data**
* **the qualification spreadsheet file**

The goal is not to produce a grand unified funnel yet.
The goal is to build a **trustworthy first prototype** that helps us judge which acquisition sources are producing quality and which are producing noise.

---

## What we need to answer

### 1. Which source combinations are the weakest links?

We need to identify which combinations of attribution dimensions perform badly enough that they should either:

* be cut
* be reduced
* be reviewed seriously

This is one of the main reasons for building the prototype.

### 2. Which combinations perform better?

We need to identify which combinations are producing stronger results and may deserve:

* more budget
* more attention
* more deliberate scaling

### 3. We must look at volume as well as ratios

Relative performance is not enough.

A source combination with the best ratio means very little if the underlying volume is tiny.
A source combination with worse efficiency but meaningful volume may matter more commercially.

So the prototype must always allow us to look at both:

* **performance ratio**
* **volume / count**

### 4. Funnel performance and drop-offs

This is a secondary priority for the first version, but it still matters.
We should be able to see where losses happen in the funnel and where the bigger drop-offs sit.

### 5. Deep dive by attribution source

The analysis should allow us to inspect how answers change depending on attribution source or attribution grouping.

That means the prototype should support breakdowns and comparisons by the relevant source dimensions, not just a single top-line view.

### 6. Track overall variability in quality

We need to track variation over time so we can separate:

* routine variation
* meaningful change

This is where XmR-style thinking matters.
The point is not just to observe movement, but to avoid overreacting to ordinary noise.

### 7. Use simple definitions

We need a glossary that defines terms, dimensions, and metrics in plain language.

No jargon for the sake of it.
If a term is important enough to appear in the prototype, it is important enough to be defined simply.

---

## Scope of the first version

The first version should stay narrow and practical.

### In scope

* GA4 acquisition data
* qualification spreadsheet data
* comparison of source combinations
* volume vs performance analysis
* quality variability over time
* basic funnel and drop-off view
* attribution-source breakdowns
* simple glossary of terms and metrics

### Out of scope for now

* full backend product usage integration
* subscription and revenue analysis
* predictive models
* complex attribution modelling
* a giant all-in-one dashboard

---

## What the first prototype should show

At minimum, the first working prototype should make it possible to inspect:

* total volume
* qualified volume
* qualification ratio
* breakdowns by attribution dimensions
* ranking of best and worst performing combinations
* enough sample size context to avoid being fooled by tiny numbers
* time-series view of overall quality
* XmR-style view of quality variation
* a secondary view of funnel performance / drop-offs

---

## Practical principle

The first version should help answer a blunt business question:

**Where are we wasting effort, and where are we finding better-quality demand worth backing harder?**

If the prototype cannot help answer that, then it is too decorative and not useful enough.

---

## Dependency: glossary

This work depends on a simple glossary document or glossary section that defines:

* the attribution dimensions we use
* the performance metrics we use
* what counts as qualification
* what counts as funnel stages and drop-offs
* how we interpret variability over time

This should be kept simple and operational, not academic.

---

