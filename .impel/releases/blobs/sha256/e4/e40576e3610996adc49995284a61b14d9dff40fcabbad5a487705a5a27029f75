---
title: "Social Media Comment Classification Pipeline"
created: 2026-06-11
sources:
  - source: "manual"
    path: "default/1781151527907-AI Automation Project_Social Media Comment Taxonomy Classifier.pdf"
---

# Social Media Comment Classification Pipeline

Five-step AI automation pipeline built by [[entities/Schola]] to extract, classify, and report on student comments from Instagram and TikTok. Uses Claude as the classification engine and the [[concepts/Schola-User-Intent-Taxonomy]] as the labelling framework.

See [[sources/social-media-comment-taxonomy-classifier]] for the full project brief.

## Architecture

```
Instagram / TikTok APIs
        ↓
Step 1: Data Extraction & Cleaning (Google Sheets Tab 1)
        ↓
Step 2: Claude Classification (embedded taxonomy prompt)
        ↓
Step 3: Output Delivery (Google Sheets Tab 2)
        ↓
Step 4: Run Report → Slack channel
        ↓
Step 5: Human Review Loop → prompt refinement
```

## Step 1 — Data Extraction

- **Platforms:** Instagram Graph API (Phase 1); TikTok Research API + Threads (Phase 2, access-dependent)
- **Scope options:** time-frame (Aug 2024+), weekly frequency, or campaign-based post list
- Non-English comments translated to English; stored in adjacent column
- Output fields: Post URL/ID · Platform · Timestamp · Comment Text · Comment Text (EN)

> [!note] Credential handling
> API credentials for the platform integrations were included in the source document. They are intentionally excluded from this wiki. Store them in a secrets manager, not in documentation.

## Step 2 — Classification Prompt

Claude receives per comment:
- Comment Text (EN)
- Full taxonomy list (embedded in prompt)

Claude returns:
- Primary Intent Code (required)
- Secondary Intent Code (optional)
- Confidence: HIGH / MEDIUM / LOW
- Reasoning note (1 sentence)

**Key prompt design principles:**
- Read the entire message before tagging; identify dominant intent, not first-mentioned topic
- Handle English, BM, and Manglish without pre-translating
- Apply [[concepts/Schola-User-Intent-Taxonomy]] classification rules (scholarship → OTHER, achieved = desired state, feedback → underlying Phase 1–4 intent)

## Step 3 — Google Sheets Output

| Tab | Content |
| --- | --- |
| Tab 1 (Raw) | Step 1 output: one row per comment, grouped by campaign |
| Tab 2 (Classified) | Step 2 output: same rows with taxonomy codes, confidence, notes |

## Step 4 — Slack Report

Per cycle: run date · comments analysed · successfully categorised · outlier count (OTHER)

## Step 5 — Review Loop

Product team samples classifications each cycle. Edge cases and misclassifications feed back into prompt refinement. Taxonomy version updates (e.g. V3 → V4) require manual prompt update.

**Open question:** Extent to which this review/improvement loop can be automated.

## Design Tensions

- Scheduling (automated frequency) vs. manual triggering — both needed
- Campaign-level filtering — needed to support specific post lists
- Account self-comment exclusion — Schola's own comments should be filtered out
