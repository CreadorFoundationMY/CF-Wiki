---
name: social-media-classifier-brief
description: Source document — AI Automation Project brief for the Social Media Comment Taxonomy Classifier
metadata:
  type: source
sources:
  - source: manual
    path: default/1781151527907-AI Automation Project_Social Media Comment Taxonomy Classifier.pdf
---

# Source: Social Media Comment Taxonomy Classifier — Project Brief

**File:** `1781151527907-AI Automation Project_Social Media Comment Taxonomy Classifier.pdf`  
**Type:** Project brief (9 content pages)  
**Owner:** Schola Product Team

## Summary

Project brief and reference document for building a 5-step AI pipeline to automatically extract, classify, and report on social media comments from Schola's Instagram and TikTok accounts. Intended as a guidance and training session for the Schola team to independently manage similar workflows.

## Document Sections

| Section | Content |
|---------|---------|
| Project Scope | Overview of 5-step pipeline |
| Step 1 — Data Extraction | API connections, raw data fields, translation logic, output fields |
| Step 2 — Analysis by Claude | Prompt structure, classification output fields |
| Step 3 — Output Delivery | Google Sheets two-tab structure with column definitions and examples |
| Step 4 — Reporting | Slack channel summary report fields |
| Step 5 — Review Loop | Human-in-the-loop process; prompt refinement on taxonomy updates |
| Claude Prompt | Full verbatim Claude prompt for qualitative data analysis (see below) |
| Informatic Items | Date ranges, platform phases, full taxonomy table, confidence thresholds |

## Claude Analysis Prompt (Verbatim)

The brief includes the existing Claude classification prompt:

**Role:** Expert Qualitative Data Analyst specialising in career and pathway planning for students. Classifies qualitative text into the Schola User Intent Taxonomy with high precision and minimal over-interpretation. Handles EN/Malay/Manglish based on underlying meaning.

**Output format:** Markdown table with columns:
`Original Text | Primary Intent | Secondary Intent | Confidence | Notes/Reasoning`

Full taxonomy and classification rules are embedded in the prompt at runtime. See [[schola-user-intent-taxonomy]] for codes.

## Informatic Items

- **Time frame:** Aug 2024 to present
- **Frequency:** Weekly
- **Campaign posts (Instagram Reels):** 12 specific URLs listed (schola.my account)
- **Platform phases:** Phase 1 = Instagram; Phase 2 = TikTok + Threads (access-dependent)

## Security Note

The source document contained API credentials in plaintext. These have been intentionally omitted from this wiki. Credentials should be stored in a secrets manager, not in project briefs.

## Open Questions (From Brief)

1. Can extraction run on a set schedule AND be manually triggered?
2. Can extraction be filtered to specific campaigns?
3. Can comments from the Schola account itself be excluded?
4. What are best practices for the feedback/improvement loop, and how much can be automated?

## Extracted Pages

- Pipeline architecture → [[social-media-comment-classifier-pipeline]]
- Taxonomy → [[schola-user-intent-taxonomy]]

## Related Pages

- [[social-media-comment-classifier-pipeline]] — full pipeline concept page
- [[schola-user-intent-taxonomy]] — taxonomy codes used in Step 2
- [[schola]] — the platform whose social media is analysed
