---
name: job-guide-schema
description: The structure and required fields of a Schola job guide — the authoritative data source that powers Ola's responses
type: concept
sources:
  - source: manual
    path: default/1781151527502-actuary_chatbase.txt
  - source: manual
    path: default/1781151527388-v11.pdf
---

# Job Guide Schema

## What It Is
The structured data format underlying each career profile on [[schola]]. Job guides are the **primary authoritative source** for [[ola-chatbot]] — they override interview content on matters of fact.

## Required Fields

### Metadata
- Job Title (EN and BM)
- URL slug (EN and BM)
- Sub-page links: Education Pathway, Future Opportunities, Job Knowledge, Job Roles, Salary & Progression
- Industry tag(s)

### Content Sections
| Section | Contents |
|---------|----------|
| Definition | 1–2 sentence plain-language description (EN and BM) |
| What the job involves | Day-to-day tasks; tools used |
| Salary & Progression | 4-level table: Early/Supervisory/Managerial/Leadership with RM ranges and typical years |
| Education Pathway | Multiple pathway table: SPM → Pre-U → Degree → Certification → Entry title |
| Demand | Where practitioners work; demand trends |
| Expert Quotes | Named interviewees with role/company, answering specific sub-questions |
| Knowledge Test | 2–4 MCQ items with correct/incorrect feedback |

### Relationship Fields
- **Aliases:** Other job titles that map to this guide (handled by Flow 1 in Ola)
- **Related Jobs (Routing Only):** Jobs without Schola guides; users are routed to closest existing guide
- **Related Jobs (With Guides):** Thematically connected jobs that have their own guides

### Optional Fields
- Video links (TikTok/approved)
- "Good for" student personality tags (e.g. "Budak Skema", "Otak Bisnes")
- Archived insights

## Bilingual Requirements
All user-facing content is produced in both English and Bahasa Malaysia. Ola uses language-matched URLs: EN questions → EN sublinks, BM/Manglish → BM sublinks (EN fallback if BM unavailable).

## Ola's Usage Rules
- Job guide data = factual source of truth for salary, education, demand, links
- Interviews = opinions and lived experience; cannot override job guide facts
- If a section exists, use it — do not say info is unavailable if partial info exists
- If truly absent: "I don't currently have that detail in our job guides"

## Related
- [[actuary-job-guide]] — concrete example of a full guide
- [[actuary]]
- [[ola-chatbot]]
- [[ola-system-prompt-v11]]
