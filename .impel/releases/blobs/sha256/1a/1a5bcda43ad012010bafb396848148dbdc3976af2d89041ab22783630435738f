---
name: social-media-taxonomy-classifier
description: Project brief for Schola's AI automation pipeline to extract, translate, classify, and report on social media comments using Claude and the Schola User Intent Taxonomy
type: source
sources:
  - source: manual
    path: "default/1781151527907-AI Automation Project_Social Media Comment Taxonomy Classifier.pdf"
---

# Social Media Comment Taxonomy Classifier — Project Brief

## Goal
A guided collaboration session for the Schola team to build and self-manage an automated pipeline for classifying social media comments against the [[schola-user-intent-taxonomy]].

## 5-Step Pipeline Overview
1. **Data Extraction** — auto-pull comments from social platforms
2. **Analysis by Claude** — classify each comment against the taxonomy
3. **Output Delivery** — write structured dataset to Google Sheets
4. **Run Report** — summarise cycle results, surface outliers
5. **Review Loop** — human-in-loop prompt refinement

See [[comment-taxonomy-pipeline]] for concept detail and [[comment-classification-workflow]] SOP.

---

## Step 1: Data Extraction & Cleaning

**Platforms:**
- Instagram: Instagram Graph API
- TikTok: TikTok Research API
- Phase 2 (planned): Threads (subject to API access)

**Credentials:** Stored separately; not reproduced in this wiki. Refer to secure credential store.

**Required raw fields per comment:**
- Post URL
- Comment text
- Timestamp
- Username (optional/anonymised)

**Translation rule:** Non-English comments (BM, Chinese, etc.) → translated to English, stored in an adjacent column.

**Final output fields:** Post URL, Comment Text, Comment Text (EN), Timestamp

**Open questions:**
- Can extraction be scheduled (fixed frequency) AND manually triggered?
- Campaign-level filtering: run extraction only for specific campaigns?
- Account filtering: exclude comments posted by the Schola account itself?

---

## Step 2: Analysis by Claude

**Claude receives per comment:**
- Comment Text (EN)
- Full taxonomy list (embedded in prompt)
- Structured prompt requesting: Primary Intent code, Secondary Intent code (optional), Confidence level, short reasoning note

**Output fields:**
- Post URL / ID
- Platform
- Comment Text (EN)
- Primary Intent (Code)
- Secondary Intent (Code)
- Confidence
- Reasoning Notes

**Existing Claude prompt:** See [[comment-taxonomy-pipeline#claude-prompt]] for the full taxonomy categorisation prompt text.

---

## Step 3: Output Delivery (Google Sheets)

**Tab 1 — Raw Data Pull & Translation** (output of Step 1):

| Post URL/ID | Platform | Timestamp | Comment Text | Comment Text (EN) |
|-------------|----------|-----------|--------------|-------------------|
| Campaign group header rows |

**Tab 2 — Classified Data** (output of Step 2):

| Post URL/ID | Platform | Comment Text (EN) | Primary Intent | Secondary Intent | Confidence | Notes |
|-------------|----------|-------------------|----------------|-----------------|------------|-------|
| Campaign group header rows |

**Sample classified data:**
| Comment | Primary | Secondary | Confidence | Notes |
|---------|---------|-----------|------------|-------|
| "Once you succeed later, everyone will go quiet." | OTHER | — | MEDIUM | Career-related sentiment but intent unclear |
| "Is there a proper guide for filling in UPU?" | 2.3 | — | HIGH | Request for specific pathway information |

---

## Step 4: Reporting

After each cycle, a summary report is sent to a **dedicated Slack channel** covering:
- Run date
- Number of comments analysed
- Number successfully categorised
- Number of outliers (labelled "OTHER")

---

## Step 5: Review Loop

**Current process:**
- Product team samples classifications each cycle
- Edge cases and misclassifications feed back into prompt refinement
- When taxonomy version changes (e.g. V3 → V4), Product team updates the prompt

**Open question:** Best practices for this feedback/improvement loop — to what extent can it be automated?

---

## Informatic Items

**Post date range options:**
- Specific timeframe: Aug 2024 to present
- Frequency-based: Weekly
- Campaign-based: See list of Instagram reels in source document

**Phase rollout:**
- Phase 1: Instagram
- Phase 2: TikTok, Threads (API access dependent)

---

## Related
- [[schola-user-intent-taxonomy]]
- [[comment-taxonomy-pipeline]]
- [[comment-classification-workflow]]
- [[schola]]
- [[ola-chatbot]]
