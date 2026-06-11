---
name: schola-user-intent-taxonomy
description: Schola User Intent Taxonomy — 12 codes across 4 phases, used by Ola chatbot and comment classifier
metadata:
  type: concept
sources:
  - source: manual
    path: default/1781151527907-AI Automation Project_Social Media Comment Taxonomy Classifier.pdf
---

# Schola User Intent Taxonomy

Shared classification system used by both the [[ola]] chatbot (for intent recognition) and the [[social-media-comment-classifier-pipeline]] (for comment tagging).

## Full Taxonomy

| Code | Phase | Definition |
|------|-------|-----------|
| **1.1** | Self & Career Exploration | User has no clear direction and wants general career ideas or possibilities |
| **1.2** | Self & Career Exploration | User has no clear direction and wants to understand themselves better (interests, strengths, personality) |
| **1.3** | Self & Career Exploration | User wants tailored career suggestions based on their interests or preferences |
| **1.4** | Self & Career Exploration | User is evaluating whether career suggestions & job information are accurate, relevant, or "fit them" |
| **1.5** | Self & Career Exploration | User wants factual information about a job, field/industry, or role |
| **1.6** | Self & Career Exploration | User confirms or affirms a chosen career goal |
| **2.1** | Pathway Planning | User has no clear direction and wants general pathway options or next steps |
| **2.2** | Pathway Planning | User wants tailored pathway suggestions (courses, training, skills, certifications) based on career goals/constraints |
| **2.3** | Pathway Planning | User wants factual information (duration, requirements, cost) about a specific pathway |
| **2.4** | Pathway Planning | User is evaluating which pathways suit them |
| **2.5** | Pathway Planning | User confirms or affirms their pathway plan |
| **3.1** | Execution | User is looking for actual job vacancies or execution steps to get a job |
| **4.1** | Emotional Support | User needs encouragement, reassurance, or confidence-building |
| **OTHER** | — | Does not fit clearly within Phase 1–4 (e.g. pure scholarship discussion, platform feedback, education topics outside taxonomy) |

## Classification Rules

1. **Primary tag (required):** Every item gets ONE primary code — the dominant/strongest intent across the whole message
2. **Secondary tag (optional):** Use only when there is a second clearly distinct intent
3. **Backward tagging:** Tag intents for completed actions too — "I found a job!" → 3.1 (same as "how do I find a job?")
4. **Platform feedback / testimonials / feature requests:** Identify the *underlying* Phase 1–4 need, not the surface form
   - "I wish Schola had more subjects to match" → 1.3 (unmet tailored career suggestion need)
   - "This website helped me find my dream job" → 1.6 (confirmed career goal)
5. **Scholarships rule:** Primary = OTHER unless a clear Phase 1–4 intent dominates

## Confidence Levels

| Level | Meaning |
|-------|---------|
| **HIGH** | Category is explicit or strongly implied by the text |
| **MEDIUM** | Reasonable inference required; some ambiguity |
| **LOW** | Significant ambiguity; best guess among several plausible options |

## Usage Contexts

- **[[ola]]:** Ola uses these intent signals (especially the 5 intent types in [[ola-response-rules]]) to determine response structure and word caps — the taxonomy codes map directly to user states
- **[[social-media-comment-classifier-pipeline]]:** Claude classifies each extracted social media comment against these codes and returns: Primary Intent Code, Secondary Intent Code, Confidence, Reasoning Note

## Related Pages

- [[ola-response-rules]] — how Ola reads intent signals
- [[social-media-comment-classifier-pipeline]] — automated classification pipeline
- [[social-media-classifier-brief]] — source project brief
