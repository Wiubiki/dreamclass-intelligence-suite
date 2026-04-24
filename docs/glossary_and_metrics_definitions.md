# Glossary & Metrics Definitions

## Purpose

This document defines the core terms, dimensions, and metrics for the first qualification funnel prototype.

It is intentionally narrow.
For this first version, the prototype is based mainly on:

* **GA4 data**
* **the qualification spreadsheet file**

The purpose of this document is to make sure we use the same language and the same logic everywhere.

---

## 1. Main analysis buckets

The first version of the analysis has two main buckets:

### A. CPC analysis

This focuses on paid traffic only.

Main questions:

* which paid source combinations are weakest and should be cut or reviewed?
* which paid source combinations perform better and may deserve more investment?
* how do ratios and volume compare together?

### B. Overall inbound analysis

This looks across inbound traffic more broadly by medium.

Main examples:

* cpc
* organic
* referral
* direct, if included

Main questions:

* how does quality differ by medium?
* how does performance change when target markets are isolated from irrelevant geographies?

---

## 2. Core dimensions

## 2.1 Medium

**Medium** is the high-level traffic type.

Examples:

* `cpc`
* `organic`
* `referral`
* `direct`

This is mainly used for the overall inbound view.

---

## 2.2 First user source

**First user source** is the main source field for acquisition analysis.

For version 1, attribution uses **first-user fields only**.
We do **not** use session-level attribution.

The prototype should use:

* all relevant **first user dimensions**
* all relevant **first user Google Ads dimensions**
* all relevant **first user manual dimensions**

Examples include first user source, medium, campaign, Google Ads campaign fields, and manual campaign fields.

This is the main top-level source dimension for CPC analysis.

---

## 2.3 Source family

**Source family** is a grouped source label used when multiple related websites or sources need to be treated as one parent group.

For the current use case, the main example is:

* `gartner`

This is a practical business grouping, even if the external branding changes later.

For now, keeping the familiar umbrella term is sensible because it supports continuity in reporting.

---

## 2.4 Source detail

**Source detail** is the individual source within a source family.

For the Gartner family, the current breakdown is:

* `capterra`
* `getapp`
* `software_advice`

This allows us to analyze both:

* the family total
* the individual websites separately

---

## 2.5 Target market tier / target market flag

A **target market tier** groups countries by commercial relevance.
This is especially important for overall inbound analysis, where organic traffic can bring volume from geographies that are not commercially useful.

Suggested tiering for version 1:

* **Tier 1**: `US`

  * top target market and current core customer base
* **Tier 2**: `Canada`, `UK`, `Australia`

  * not the ideal fit, but there are existing customers
* **Tier 3**: `Italy`, `Germany`, `France`, `Spain`, `Slovenia`, `Greece`, `Ireland`, `New Zealand`

  * occasional customers
* **Tier 4**: everything else

The prototype may use this in two ways:

### A. Detailed market-tier view

* tier 1
* tier 2
* tier 3
* tier 4

### B. Simpler target-market flag

* `target_market = yes` for tiers 1 to 3
* `target_market = no` for tier 4

This gives us both a simple commercial filter and a more nuanced market breakdown.

---

## 2.6 Normalized campaign

**Normalized campaign** is the standard comparison bucket used for CPC analysis.

It exists because raw campaign naming differs by platform and campaign structure.

### Rule set

#### Rule 1: Google CPC, Features campaign

If:

* `first user source / medium = google / cpc`
* and `first user Google Ads campaign = [NA] Features`

then:

* `normalized_campaign = first user Google Ads ad group name`

#### Rule 2: Bing CPC, Features campaign

If:

* `first user source / medium = bing / cpc`
* or `Bing / cpc`
* or `bing.com / cpc`
* and `first user manual campaign name = [NA] Features`

then:

* `normalized_campaign = first user manual ad content`

#### Rule 3: Google CPC, non-Features campaigns

If:

* `first user source / medium = google / cpc`
* and `first user Google Ads campaign IS NOT [NA] Features`

then:

* `normalized_campaign = first user Google Ads campaign`

#### Rule 4: All other cases

* `normalized_campaign = first user manual ad campaign`

This rule set should be implemented explicitly in transformation logic and not handled manually in reporting.

---

## 2.7 Source combination

A **source combination** is a grouped attribution view used to compare performance.

The exact grouping may vary by analysis view, but the main combinations for version 1 should be:

### CPC default comparison level

* first user source
* normalized campaign

### Optional deeper CPC comparison

* source family
* source detail
* normalized campaign

### Overall inbound comparison level

* medium
* optionally target market tier or target market flag

These groupings should be kept stable across the prototype.

---

## 3. Qualification terms

## 3.1 Lead

A **lead** is a row or record in the qualification dataset representing an inbound opportunity under evaluation.

The exact identifier and row logic should match the spreadsheet structure.

If deduplication is needed later, it must be defined explicitly.

---

## 3.2 Qualified lead

A **qualified lead** is a lead that completes the qualification funnel and is assigned to:

* **Path A (strong fit)**
* or **Path B (potential fit)**

For version 1, the qualification spreadsheet is the source of truth for this outcome.

The exact spreadsheet field that identifies the path is:

* `grade`

### Weighting logic

For weighted quality calculations:

* **Path A** gets coefficient **1.0**
* **Path B** gets coefficient **0.6**

This means all qualified leads count toward qualification volume, but not all qualified leads are treated as equally strong in weighted quality analysis.

---

## 3.3 Unqualified lead

An **unqualified lead** is a lead that does not fall into Path A or Path B.

In practice, this includes lower-fit paths such as:

* Path C
* Path D

These path values are identified from the spreadsheet field:

* `grade`

For version 1, the main distinction remains:

* qualified = Path A or Path B
* not qualified = everything else

---

## 3.4 Qualification rate

**Qualification rate** is:

`qualified leads / total leads`

This is one of the main performance metrics in the prototype.

It should always be interpreted together with volume.

---

## 4. Core metrics

## 4.1 Total leads

The number of leads in the selected slice.

Examples:

* total leads by source
* total leads by medium
* total leads by normalized channel
* total leads over time

---

## 4.2 Qualified leads

The number of qualified leads in the selected slice.

---

## 4.3 Unqualified leads

The number of leads in the selected slice that are not qualified.

---

## 4.4 Qualification rate

The share of total leads that are qualified.

Formula:

`qualified leads / total leads`

---

## 4.5 Share of volume

The proportion of total lead volume contributed by a given segment.

This helps avoid overvaluing strong ratios built on trivial sample sizes.

---

## 4.6 Share of qualified volume

The proportion of all qualified leads contributed by a given segment.

This helps identify which sources are actually contributing meaningful quality at scale.

---

## 4.7 Weighted quality score

A **weighted quality score** can be used as a supporting metric to reflect differences in lead quality across qualification outcomes.

For now, the weighting logic is:

* Path A = 10
* Path B = 6
* Path C = 3
* Path D = 0

This mirrors the existing Lead QI logic.

---

## 4.8 Lead QI

**Lead QI** is calculated as:

`[(Path A leads x 10) + (Path B leads x 6) + (Path C leads x 3)] / qualification funnel completions`

Equivalently, the denominator can be treated as the sum of all leads across Paths A, B, C, and D, where that matches the spreadsheet structure.

This is a supporting quality metric alongside the simpler qualification rate.

---

## 5. Volume guardrails

High ratios with very low volume should not be treated as strong evidence.

The prototype should therefore support volume-aware interpretation.

At minimum:

* every performance ratio should be shown next to volume
* low-volume segments should be easy to spot
* rankings should not encourage overconfidence from tiny sample sizes

The exact minimum-volume threshold can be decided later, but the principle must be built in from the start.

---

## 6. Funnel and drop-off terms

This is a secondary analytical layer in version 1.

### 6.1 Simple working funnel

The default secondary funnel should be:

* new users
* unique `/qualification/` pageviews or qualification starts
* qualification completions

This gives us a simple view of movement into and through the qualification process.

### 6.2 Expanded funnel

A more detailed version should include each individual qualification step:

* step 1 start / completion
* step 2 start / completion
* step 3 start / completion
* step 4 start / completion

This allows us to inspect where users drop off within the funnel rather than only at the top and bottom.

The expanded funnel is desirable if the event data supports it cleanly.

---

## 7. Time and variability

## 7.1 Time grain

The prototype should support at least:

* day
* week
* month

Weekly views may be especially useful for stability analysis.

---

## 7.2 Variability over time

The purpose of variability analysis is to distinguish:

* routine variation
* meaningful change

This is where XmR-style thinking comes in.

The point is not to react to every movement.
The point is to identify when the process appears to have genuinely shifted.

For version 1, this should apply at minimum to:

* overall qualification rate over time
* possibly qualification rate by major source bucket

---

## 8. Source of truth rules

For version 1:

* **GA4** is the source of truth for attribution dimensions
* **the qualification spreadsheet** is the source of truth for qualification outcome
* attribution should use first-user fields only

---

## 9. Final decisions captured here

The following decisions are now fixed for version 1:

* attribution uses **first-user fields only**
* the prototype should use all relevant first user dimensions, first user Google Ads dimensions, and first user manual dimensions
* the field identifying qualification path in the spreadsheet is **`grade`**
* **Gartner** remains the source family umbrella for `capterra`, `getapp`, and `software_advice`
* **G2 remains separate** from the Gartner family for now
* there is **no fixed low-volume warning threshold yet**
* for now, ratios should always be shown together with volume, and threshold rules can be added later

### Deduplication note

There are some users who appear to run the funnel more than once, for example where the same GA cookie is associated with more than one funnel UUID.

From the current spreadsheet view, this does not appear to be a large issue, but it should be monitored.

For version 1:

* do not force aggressive deduplication unless analysis shows it is materially distorting results
* include a simple monitoring rule or diagnostic to track repeated runs by the same user / cookie where possible

