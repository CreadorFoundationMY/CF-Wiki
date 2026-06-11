---
title: "Schola User Intent Taxonomy"
created: 2026-06-11
sources:
  - source: "manual"
    path: "default/1781151527907-AI Automation Project_Social Media Comment Taxonomy Classifier.pdf"
---

# Schola User Intent Taxonomy

Four-phase classification framework used by [[entities/Schola]] to tag student intent across chatbot interactions ([[entities/Ola]]) and social media comments (see [[concepts/Social-Media-Comment-Classification-Pipeline]]).

## Taxonomy Codes

### Phase 1: Self & Career Exploration

| Code | Description |
| --- | --- |
| 1.1 | No clear direction; wants general career ideas or possibilities |
| 1.2 | No clear direction; wants to understand themselves better (interests, strengths, personality) |
| 1.3 | Wants tailored career suggestions based on interests or preferences |
| 1.4 | Evaluating whether career suggestions / job info are accurate, relevant, or "fit them" |
| 1.5 | Wants factual information about a job, field/industry, or role |
| 1.6 | Confirms or affirms a chosen career goal |

### Phase 2: Pathway Planning

| Code | Description |
| --- | --- |
| 2.1 | No clear direction; wants general pathway options or next steps |
| 2.2 | Wants tailored pathway suggestions (courses, training, skills, certifications) based on goals/preferences/constraints |
| 2.3 | Wants factual information about a specific pathway (duration, requirements, cost, etc.) |
| 2.4 | Evaluating which pathways suit them |
| 2.5 | Confirms or affirms their pathway plan |

### Phase 3: Execution

| Code | Description |
| --- | --- |
| 3.1 | Looking for actual job vacancies or execution steps to get a job |

### Phase 4: Emotional Support

| Code | Description |
| --- | --- |
| 4.1 | Needs encouragement, reassurance, or confidence-building in career exploration & pathway planning |

### Special

| Code | Description |
| --- | --- |
| OTHER | Does not fit Phase 1–4; includes scholarship discussions without career intent, platform feedback unrelated to career decisions, education topics outside taxonomy |

## Classification Rules

1. **Primary tag (required):** Every item gets one code representing dominant intent — even feedback, testimonials, or feature requests (e.g. "I wish Schola had more subjects" → 1.3, not feedback)
2. **Secondary tag (optional):** Used only when a second distinct Phase 1–4 intent is clearly present
3. **Confidence levels:** HIGH (explicit/strongly implied) · MEDIUM (reasonable inference) · LOW (significant ambiguity, best guess)
4. **Scholarship rule:** Primarily scholarship-focused → OTHER; unless a Phase 1–4 intent dominates
5. **Achieved vs. desired:** Tag achieved states identically to desired states ("I found a job!" = 3.1, same as "how do I find a job?")

## Usage Context

- [[entities/Ola]] chatbot uses this framework implicitly to interpret student intent and select the right response mode
- [[concepts/Social-Media-Comment-Classification-Pipeline]] applies this taxonomy explicitly to classify social media comments via a Claude prompt
