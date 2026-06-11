---
name: social-media-comment-classifier-pipeline
description: 5-step AI pipeline to extract, classify, deliver, report, and refine Schola social media comments
metadata:
  type: concept
sources:
  - source: manual
    path: default/1781151527907-AI Automation Project_Social Media Comment Taxonomy Classifier.pdf
---

# Social Media Comment Taxonomy Classifier Pipeline

## Purpose

An AI automation pipeline that pulls comments from Schola's social media posts, classifies each comment against the [[schola-user-intent-taxonomy]] using Claude, delivers structured output to Google Sheets, reports to Slack, and runs a human-in-the-loop review cycle.

**Goal:** Enable the Schola team to independently set up and manage similar AI workflows.

## Pipeline Overview

```
Step 1: Extract → Step 2: Classify → Step 3: Deliver → Step 4: Report → Step 5: Review
```

---

## Step 1: Automated Data Extraction & Cleaning

**Platforms:**
- Phase 1: Instagram (Instagram Graph API)
- Phase 2: TikTok (TikTok Research API); Threads (if access available)

**Raw data fields per comment:**
| Field | Notes |
|-------|-------|
| Post URL / ID | |
| Platform | Instagram / TikTok |
| Timestamp | |
| Comment Text | Original language |
| Comment Text (EN) | Auto-translated if not English (BM, Chinese → EN) |

Translation is stored in a new column immediately to the right of the original comment column. English comments are copied as-is.

**Open questions from brief:**
- Scheduling: set frequency + manual trigger capability needed
- Campaign-level filtering: pull only posts belonging to a specific campaign
- Account filtering: exclude comments posted by the Schola account itself

**Date ranges for pulls:**
- Time-frame mode: Aug 2024 to present
- Frequency mode: weekly
- Campaign mode: specific post URLs (12 Instagram Reels listed in source)

---

## Step 2: Analysis by Claude

Claude receives each comment with:
- Comment Text (EN)
- Full [[schola-user-intent-taxonomy]] list embedded in prompt
- Structured prompt requesting: Primary Intent Code, Secondary Intent Code, Confidence, Reasoning Note

**Classification output fields:**
| Field | Description |
|-------|-------------|
| Post URL / ID | |
| Platform | |
| Comment Text (EN) | |
| Primary Intent (Code) | e.g. 1.5, 2.3, OTHER |
| Secondary Intent (Code) | Optional — only when second distinct intent present |
| Confidence | HIGH / MEDIUM / LOW |
| Reasoning Notes | One concise sentence |

The Claude prompt role: *"Expert Qualitative Data Analyst specialising in career and pathway planning for students."* Processes English, Malay, and Manglish based on underlying meaning without translating first.

See [[social-media-classifier-brief]] for the verbatim Claude prompt.

---

## Step 3: Output Delivery (Google Sheets)

Two-tab Google Sheet:

**Tab 1 — Raw Data Pull & Translation** (Step 1 output)
One row per comment, grouped by campaign.
Columns: Post URL/ID | Platform | Timestamp | Comment Text | Comment Text (EN)

**Tab 2 — Classified Data Output** (Step 2 output)
One row per comment, with taxonomy codes and confidence.
Columns: Post URL/ID | Platform | Comment Text (EN) | Primary Intent (Code) | Secondary Intent (Code) | Confidence | Notes

---

## Step 4: Reporting

After each cycle, a summary report is sent to a **dedicated Slack channel**:
- Run date
- Number of comments analysed
- Number successfully categorised
- Number of outliers (labelled as "OTHER")

---

## Step 5: Review Loop

**Current process (human-in-the-loop):**
- Product team samples a subset of classifications each cycle
- Edge cases and misclassifications feed back into prompt refinement
- Taxonomy version updates (e.g. V3 → V4) require manual prompt updates by Product team

**Open question from brief:** Best practices and automation extent for this feedback/improvement loop.

---

## Related Pages

- [[schola-user-intent-taxonomy]] — the classification codes used in Step 2
- [[schola]] — the platform whose social media is being analysed
- [[social-media-classifier-brief]] — source document
