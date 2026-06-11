---
name: comment-taxonomy-pipeline
description: Schola's 5-step AI pipeline for extracting, translating, classifying, reporting, and refining social media comment data using Claude and the Schola User Intent Taxonomy
type: concept
sources:
  - source: manual
    path: "default/1781151527907-AI Automation Project_Social Media Comment Taxonomy Classifier.pdf"
---

# Comment Taxonomy Pipeline

## Overview
An automated AI pipeline that pulls comments from [[schola]]'s social media, classifies them against the [[schola-user-intent-taxonomy]] using Claude, and delivers structured outputs for analysis.

## Pipeline Stages

```
Instagram / TikTok APIs
        ↓
  1. Extract & Clean
        ↓
  2. Classify with Claude
        ↓
  3. Write to Google Sheets
        ↓
  4. Send Slack Summary Report
        ↓
  5. Human Review → Prompt Refinement Loop
```

## Stage Details

### Stage 1: Extract & Clean
- Source: Instagram Graph API (Phase 1), TikTok Research API (Phase 1), Threads (Phase 2)
- Fields captured: Post URL, Comment Text, Timestamp, Username (anonymised optional)
- Translation: Non-English comments → translated to English, stored in adjacent column
- Filtering open questions: scheduled vs manual triggers, campaign-level filtering, exclude Schola's own comments

### Stage 2: Claude Classification
The Claude prompt (see below) sends each comment with the full taxonomy and requests:
- Primary Intent code (required)
- Secondary Intent code (optional, if second distinct intent exists)
- Confidence level (HIGH / MEDIUM / LOW)
- Short reasoning note

**Confidence thresholds:**
- **HIGH** — maps clearly and unambiguously to a taxonomy code
- **MEDIUM** — probably a certain intent, some ambiguity
- **LOW** — vague/noisy/multi-directional; best guess

### Stage 3: Google Sheets Output
- Tab 1: Raw data + translation (Step 1 output), rows grouped by campaign
- Tab 2: Classified data (Step 2 output), rows grouped by campaign

### Stage 4: Slack Report (per cycle)
Automated summary sent to dedicated channel:
- Run date
- Total comments analysed
- Total successfully categorised
- Total outliers (OTHER)

### Stage 5: Review Loop
- Product team samples each cycle's classifications
- Misclassifications and edge cases feed back as prompt refinements
- Taxonomy version changes (e.g. V3 → V4) require Product team to update the Claude prompt

## Claude Prompt (Embedded)

```
# ROLE
You are an expert Qualitative Data Analyst specialising in career and pathway planning
for students. You classify qualitative text (student messages, feedback, and questions)
into the Schola User Intent Taxonomy with high precision and minimal over-interpretation.

The data is primarily from Malaysian students and will contain a mix of English, Malay,
and "Manglish." Process and categorize based on the underlying meaning, without
translating the text first.

# TASK
For each row of student text, identify the core underlying intent and tag them using the
Schola User Intent Taxonomy below.

Determine the tag by reading the entire message first, then identifying the strongest
underlying intent across the whole message, not simply the first topic mentioned.

# TAXONOMY & CODES
[Full taxonomy embedded — see [[schola-user-intent-taxonomy]]]

# CLASSIFICATION RULES
1. PRIMARY TAG (REQUIRED): One code per item; dominant intent wins.
   - Surface and platform feedback → find underlying Phase 1-4 intent
   - Completed actions tagged same as desires ("I found a job!" → 3.1)
2. SECONDARY TAG (OPTIONAL): Only if second distinct Phase 1-4 intent is clearly present.
3. CONFIDENCE: HIGH / MEDIUM / LOW (see thresholds above)
4. OTHER: Use when message does not fit Phase 1-4.
5. SCHOLARSHIPS: Primary = OTHER unless dominant Phase 1-4 intent exists.

# OUTPUT FORMAT
Markdown table:
| Original Text | Primary Intent | Secondary Intent | Confidence | Notes/Reasoning |
```

## Data Scope
- Time range: Aug 2024 to present (or weekly frequency, or campaign-based)
- Campaign-based target posts: 12 Instagram reels listed in source document

## Related
- [[social-media-taxonomy-classifier]]
- [[schola-user-intent-taxonomy]]
- [[comment-classification-workflow]]
- [[schola]]
- [[ola-chatbot]]
