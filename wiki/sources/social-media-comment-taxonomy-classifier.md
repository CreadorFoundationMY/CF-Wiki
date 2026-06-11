---
title: "AI Automation Project — Social Media Comment Taxonomy Classifier"
created: 2026-06-11
sources:
  - source: "manual"
    path: "default/1781151527907-AI Automation Project_Social Media Comment Taxonomy Classifier.pdf"
---

# AI Automation Project — Social Media Comment Taxonomy Classifier

Project brief for an AI-powered pipeline to extract, classify, and report on social media comments from [[entities/Schola]]'s Instagram and TikTok accounts.

**Goal of session:** Teach the Schola team to set up and independently manage similar AI automation workflows.

## Pipeline Overview

See [[concepts/Social-Media-Comment-Classification-Pipeline]] for detailed architecture.

1. **Step 1 — Automated Data Extraction:** Pull comments from Schola's social media posts via platform APIs
2. **Step 2 — Analysis by Claude:** Classify each comment against the [[concepts/Schola-User-Intent-Taxonomy]]
3. **Step 3 — Output Delivery:** Write structured dataset to Google Sheets (two tabs)
4. **Step 4 — Run Report:** Summarise cycle results; send to Slack channel
5. **Step 5 — Review Loop:** Human review of sample classifications; refine prompt

## Step 1: Data Extraction

**Platforms:**
- Phase 1: Instagram (Instagram Graph API)
- Phase 2: TikTok (TikTok Research API), Threads (access-dependent)

**⚠ Note:** API credentials were present in the source document. They have been intentionally omitted from this wiki for security reasons.

**Data fields per comment:**
- Post URL / ID
- Platform
- Timestamp
- Comment Text (original language)
- Comment Text (EN) — auto-translated; stored in adjacent column

**Post scope options:**
- Time-frame: Aug 2024 to present
- Frequency: Weekly
- Campaign-based: 12 specific Instagram reels from schola.my (URLs in source document)

**Open questions:**
- Can extraction be scheduled AND manually triggered?
- Can filtering be restricted to a specific campaign?
- Can Schola account's own comments be excluded?

## Step 2: Claude Classification

Each comment is sent with the full taxonomy embedded in the prompt. Claude returns:

| Field | Description |
| --- | --- |
| Primary Intent (Code) | Dominant intent from taxonomy |
| Secondary Intent (Code) | Second distinct intent, if present |
| Confidence | HIGH / MEDIUM / LOW |
| Reasoning Notes | 1-sentence explanation |

The classification prompt instructs Claude to read the full message before tagging, identify dominant intent (not first-mentioned topic), and handle English, Malay, and Manglish.

**Special rules:**
- Scholarship messages → Primary: OTHER (unless Phase 1–4 intent is dominant)
- Platform feedback / UX suggestions → reclassify to underlying Phase 1–4 intent
- Achieved states are tagged identically to desired states ("I found a job!" = 3.1)

## Step 3: Output — Google Sheets Structure

**Tab 1 (Raw):** Post URL/ID · Platform · Timestamp · Comment Text · Comment Text (EN) — rows grouped by campaign

**Tab 2 (Classified):** Post URL/ID · Platform · Comment Text (EN) · Primary Intent · Secondary Intent · Confidence · Notes

## Step 4: Reporting

After each cycle, a summary report is sent to a dedicated Slack channel:
- Run date
- Number of comments analysed
- Number successfully categorised
- Number of outliers (labelled OTHER)

## Step 5: Review Loop

Current process:
- Product team samples classifications each cycle
- Edge cases / misclassifications feed back into prompt refinement
- Taxonomy version changes (e.g. V3 → V4) require prompt update

**Open question:** What are best practices for running and automating this feedback loop?
