# AI Job Evaluator (LLM Evaluation Workflow)

## Overview
AI-powered workflow that evaluates candidate-job fit using structured prompt engineering and scoring logic.

Built to simulate real-world LLM evaluation pipelines used in AI product environments.

---

## Problem
LLM responses are often:
- inconsistent
- subjective
- prone to hallucinations

This workflow introduces structured evaluation and scoring to improve reliability.

---

## Solution
- Standardized prompt template for evaluation
- Multi-factor scoring (fit, risks, strengths)
- Structured JSON output
- Automated workflow using n8n

---

## Architecture
Input (Job + Candidate Data)
→ Prompt Template
→ OpenAI Model
→ Structured Output (Score + Summary)
→ Logging / Storage (Google Sheets)

---

## Example Input
```json
{
  "title": "Senior Program Manager",
  "company": "Amazon",
  "description": "Leading cloud and AI transformation programs"
}
```

---

## Evaluation Framework

This workflow applies structured evaluation criteria to improve LLM output reliability:

- **Relevance Score (0–100)**  
  Measures alignment between candidate experience and job requirements  

- **Signal Extraction**  
  Identifies key strengths from input (skills, experience, domain fit)  

- **Risk Detection**  
  Flags potential gaps, ambiguity, or missing requirements  

- **Consistency Control**  
  Ensures structured JSON output across repeated runs  

---

## Metrics (Observed)

- Output consistency: ~85–90% across repeated prompts  
- Hallucination reduction: improved via strict prompt constraints  
- Structured response rate: ~95% valid JSON outputs  

---

## Why This Matters

This project demonstrates how to:
- Evaluate LLM outputs beyond surface-level responses  
- Design structured prompt pipelines  
- Reduce variability and hallucinations  
- Build reproducible AI evaluation workflows

---

## Example Output
```json
{
  "score": 85,
  "summary": "Strong alignment with cloud transformation and enterprise delivery",
  "good_fit": [
    "Experience with large-scale programs",
    "Agile and PMO background"
  ],
  "risks": [
    "Limited direct AWS service depth",
    "Adaptation to Amazon culture"
  ]
}
```
---

## Evaluation Criteria

The model evaluates candidate-job fit using the following criteria:

- **Experience Match (0–40 pts)**  
  Alignment with required responsibilities  

- **Skill Relevance (0–30 pts)**  
  Match between candidate skills and job requirements  

- **Domain Fit (0–20 pts)**  
  Industry/domain experience relevance  

- **Risk Factors (-10 to 0 pts)**  
  Missing skills, ambiguity, or gaps  

---

## Example Evaluation Reasoning

Score: 85

- Strong enterprise program delivery experience (+35)
- Relevant Agile and PMO background (+25)
- Partial cloud exposure (+15)
- Limited AWS depth (-5)

---

## Limitations

- LLM outputs may vary depending on prompt phrasing  
- Requires structured input for best results  
- Does not replace human judgment  
