# ☕ C5M1 Graded Assignment — Opening a Coffee Shop in NYC

> **Course:** DeepLearning.AI — Data Analytics Program (Course 5)  
> **Module:** Module 1 — Data Storytelling Fundamentals  
> **Assignment Type:** Graded Assignment + Memo Writing  
> **Estimated Time:** 45 minutes  

---

## 🗂️ Repository Structure

```
C5M1_Assignment/
│
├── README.md                        ← This file (overview + quiz answers)
├── notebook_analysis.md             ← Full notebook walkthrough with insights
├── memo_solution.md                 ← Complete memo solution (graded artifact)
└── quiz_answers.md                  ← All 7 quiz questions with explanations
```

---

## 📌 Assignment Overview

You are a **data analyst at a consulting firm** helping a client identify the best location to open a coffee shop in New York City.

A coworker has already completed the Python analysis. Your task is to:
1. Understand the notebook outputs
2. Identify the key insights
3. **Write a memo** addressed to the Client Advisory Team

**Focus areas of analysis:**
- Competition landscape across NYC boroughs and zip codes
- Health inspection compliance rates and common violations
- Customer ratings and review volume by location
- Price sensitivity and its effect on customer ratings

---

## 🔑 Key Findings at a Glance

| Finding | Data Point |
|---|---|
| Total coffee shops in NYC | **1,004** across 5 boroughs |
| Most competitive borough | **Manhattan** — 531 shops (53% of all NYC shops) |
| Highest rated borough | **Brooklyn** — avg rating 4.45/5 |
| Most reviews per shop | **Manhattan** — avg 517.8 reviews/shop |
| Initial inspection pass rate | **~50%** — most new shops fail first inspection |
| Top opportunity zip code | **11366 (Queens)** — 1 shop, ~1,000 reviews, 4.7 rating |
| Secondary opportunity | **10026 (Manhattan)** — 4 shops, ~1,800 reviews/shop, 4.3 rating |
| Price–rating correlation | **-0.315** — lower prices → higher customer ratings |

---

## 📂 Files in This Assignment

| File | Description |
|---|---|
| [`notebook_analysis.md`](./notebook_analysis.md) | Cell-by-cell walkthrough of the coworker's notebook with insights explained |
| [`memo_solution.md`](./memo_solution.md) | Complete memo solution as it should be written for the graded assignment |
| [`quiz_answers.md`](./quiz_answers.md) | All 7 quiz questions with correct answers and reasoning |

---

## 💬 Interview Angles from This Assignment

- **"How do you turn a notebook into a business communication?"**  
  → Strip the code, lead with the conclusion, structure as: main finding → key evidence → recommendations

- **"How do you identify market opportunities in a data analysis?"**  
  → Look for areas with high demand (reviews as proxy) and low supply (shop count). Zip 11366: 1 competitor but ~1,000 reviews is a clear signal.

- **"How do you handle technical analysis for non-technical stakeholders?"**  
  → Convert statistical outputs into plain business language. A -0.315 correlation between price and rating becomes: "Customers rate lower-priced shops more favorably."
