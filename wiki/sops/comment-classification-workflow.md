---
name: comment-classification-workflow
description: Step-by-step SOP for running the Schola social media comment taxonomy classification pipeline — extraction, Claude analysis, output delivery, reporting, and review
type: sop
sources:
  - source: manual
    path: "default/1781151527907-AI Automation Project_Social Media Comment Taxonomy Classifier.pdf"
---

# SOP: Comment Classification Workflow

**Pipeline:** [[comment-taxonomy-pipeline]]
**Taxonomy:** [[schola-user-intent-taxonomy]]
**Owner:** Schola Product Team

---

## Step 1: Data Extraction & Cleaning

**Trigger:** Scheduled (weekly) OR manual trigger

**Platforms:**
- Phase 1: Instagram (Instagram Graph API)
- Phase 2: TikTok (TikTok Research API), Threads

**Data scope options:**
- Timeframe-based: Aug 2024 to present
- Frequency-based: Weekly cadence
- Campaign-based: Specific post URLs

**Process:**
1. Connect to platform API using stored credentials (not reproduced here — see secure credential store)
2. Pull comments with fields: Post URL, Comment Text, Timestamp, Username (anonymised)
3. For each non-English comment: translate to English → store in "Comment Text (EN)" column immediately to the right
4. Filter out comments posted by the Schola account itself (pending API configuration)
5. Write to **Tab 1** of target Google Sheet, grouped by campaign

**Output schema (Tab 1):**
```
Post URL/ID | Platform | Timestamp | Comment Text | Comment Text (EN)
```

---

## Step 2: Claude Classification

**Input:** All rows from Tab 1 with Comment Text (EN)

**Send to Claude:**
- Comment Text (EN) for each row
- Full [[schola-user-intent-taxonomy]] embedded in prompt
- Instruction to return: Primary Intent code, Secondary Intent code (if applicable), Confidence, Reasoning note

**Classification rules (summary):**
- One primary code per comment (dominant intent)
- Secondary code only if a second distinct Phase 1–4 intent is clearly present
- Tag both expressed desires and completed actions
- Scholarships without broader intent → OTHER
- Low-confidence or ambiguous → LOW + OTHER if no fit

**Output schema (Tab 2):**
```
Post URL/ID | Platform | Comment Text (EN) | Primary Intent | Secondary Intent | Confidence | Notes
```

---

## Step 3: Output Delivery

1. Write classification results to **Tab 2** of the same Google Sheet
2. Rows grouped by campaign (matching Tab 1 structure)
3. Verify row counts match between Tab 1 and Tab 2

---

## Step 4: Run Report

After each cycle completes, generate and send a summary to the **designated Slack channel**:

```
Run date: [DATE]
Comments analysed: [N]
Successfully categorised: [N]
Outliers (OTHER): [N]
```

---

## Step 5: Review Loop

**Frequency:** Each cycle

**Process:**
1. Product team reviews a random sample of classifications
2. Flag misclassifications and edge cases
3. Update the Claude classification prompt to address identified issues
4. If taxonomy version changes (V3 → V4): update all taxonomy codes in the prompt accordingly

**Best practices (open research question from brief):**
- Prioritise review of LOW-confidence items and OTHER items — highest error density
- Track recurring misclassification patterns across cycles to identify systemic prompt weaknesses
- Version-control the Claude prompt (store in shared location); date each update
- Consider A/B testing prompt variants on a subset before full rollout
- Automation potential: LOW items and OTHERs can be auto-flagged for review; true prompt improvement still requires human judgment

---

## Escalation
If the taxonomy itself needs restructuring (beyond prompt wording), escalate to whoever owns taxonomy versioning before updating the classifier prompt.

## Related
- [[comment-taxonomy-pipeline]]
- [[schola-user-intent-taxonomy]]
- [[social-media-taxonomy-classifier]]
- [[schola]]
