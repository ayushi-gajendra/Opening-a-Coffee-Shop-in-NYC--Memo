# ✅ Quiz Answers — C5M1 Graded Assignment

> **Assignment:** Opening a Coffee Shop in NYC — Memo  
> All 7 questions with correct answers, explanations, and the reasoning behind wrong options.

---

## Q1 — What is the main issue with the coworker's Notebook as a data storytelling artifact?

**✅ Correct Answer:**
> **It lacks narrative and is not well structured.**

**Explanation:**  
The notebook contains complete analysis code, visualizations, and outputs — but it has almost no narrative context. There are no explanations of *why* each analysis was done, no main conclusion at the top, and the code cells are mixed with sparse markdown. A data storytelling artifact should guide the reader through insights — this notebook just presents results without a story.

**Why the other options are wrong:**
- *"Code needs to be rewritten every time"* — False. Notebooks are designed to be re-run as-is.
- *"Lacks reproducibility"* — Actually the opposite problem; the code is there and can be reproduced. The issue is narrative, not reproducibility.
- *"Has no visualizations"* — False. It has several plots (bar charts, box plots, interactive maps).

---

## Q2 — Why should you leave out analysis code in your memo?

**✅ Correct Answers (choose two):**
> 1. **Nontechnical stakeholders may be distracted by the code if they are unfamiliar with it.**
> 2. **The code isn't necessary for understanding the results.**

**Explanation:**  
The Client Advisory Team is not a technical audience. They need business insights, not Python syntax. Code creates visual clutter for non-technical readers and can obscure the key messages. The results and their business implications are what matter in a memo.

**Why the other options are wrong:**
- *"Code should only be included in a slide deck"* — False. Code belongs in notebooks for technical audiences; it shouldn't be in slide decks either.
- *"Including the code reduces reproducibility"* — This is backwards. Code *increases* reproducibility. That's not a reason to exclude it from a memo.

---

## Q3 — Which five boroughs does the analysis cover?

**✅ Correct Answers:**
> **Manhattan, Bronx, Brooklyn, Queens, Staten Island**

**From the notebook output:**
```
BORO
Bronx             40
Brooklyn         269
Manhattan        531
Queens           146
Staten Island     18
```

**Why "Queenscliffe" is wrong:**  
Queenscliffe is not a NYC borough — it's a town in Victoria, Australia. The five NYC boroughs are Manhattan, Brooklyn, Queens, the Bronx, and Staten Island.

---

## Q4 — Most appropriate subject line for the memo?

**✅ Correct Answer:**
> **"Key Insights for New York City Coffee Shop Location"**

**Explanation:**  
A good memo subject line is:
- Specific enough to tell the reader exactly what to expect
- Concise enough to scan at a glance
- Professional and neutral in tone

**Why the other options are wrong:**
- *"Some of the best neighborhoods...Customer needs to take extra precautions..."* — Way too long and combines two separate topics. Subject lines should be one concise phrase.
- *"Coffee Shop"* — Too vague. No useful information.
- *"Main Insights"* — Vague. Doesn't tell the reader what subject the insights are about.

---

## Q5 — Best opening statement?

**✅ Correct Answer:**
> **"Coffee shop ventures face significant competition in NYC, with over 1,000 existing establishments. Our analysis has identified specific underserved locations and health compliance factors that will maximize the chances of success in this competitive market."**

**Explanation:**  
This opening works because:
1. **Establishes context** (competitive market)
2. **Previews what the memo contains** (underserved locations + health factors)
3. **Is concise** — two sentences, easy to read
4. **Doesn't overpromise** — says "maximize chances" not "guarantee success"

**Why the other options are wrong:**

| Option | Problem |
|---|---|
| "...must avoid Manhattan at all costs" | Overstates. Data shows *specific* Manhattan zip codes ARE good opportunities. Sweeping claims not supported by evidence. |
| "You shouldn't add an opening statement" | Wrong principle. Opening statements are essential — they orient the reader. |
| The very long paragraph | While comprehensive, it buries the key message in excessive detail. A memo opening should be punchy, not exhaustive. The body sections are where details belong. |

---

## Q6 — Best formatting for the Key Findings section?

**✅ Correct Answer: Option B** — the one with grouped, labeled findings:

```
Location is decisive:
  • Interesting Zip Codes: 11366 (Queens) and 10026 (Manhattan) display 
    high consumer demand with minimal competition
  • Eastern NYC represents opportunity...
  • Brooklyn shops achieve the highest average customer ratings (4.45/5)

Inspection readiness matters:
  • Coffee shops face a 50% failure rate on initial health inspections...
  • Borough differences are substantial: Manhattan establishments are 
    twice as likely to have plumbing/drainage violations...
  • Non-food contact surface issues are the top violation (12-18%)
```

**Why this format wins:**
- **Grouped by theme** — readers can navigate directly to what's relevant to them
- **Labeled with descriptive headers** — each group has a clear takeaway title
- **Specific data points** — every bullet includes a number

**Why Option A is wrong (the plain bulleted list):**
- No thematic grouping makes it harder to scan
- Findings jump between location, ratings, health compliance, and violations without a coherent structure

**Why Option C is wrong:**
- Contains the line: *"Keep prices low: the -0.315 correlation definitively shows premium pricing will drive customers away"*
- **-0.315 is a moderate correlation, not a definitive proof.** Overstating the strength of evidence is a data storytelling error — it undermines your credibility. The correct framing: "The data suggests lower pricing tends to be associated with higher ratings."

---

## Q7 — Best two next steps for the Recommendations section?

**✅ Correct Answers:**
> 1. **Investing in pre-opening health code assessment since initial inspections have only a 50% pass rate.**
> 2. **Targeting Queens Zip Code 11366 which offers exceptional review volume (~1000) and ratings (4.7/5) with minimal competition. Consider also exploring Manhattan Zip Code 10026 as a high-engagement alternative with ~1800 reviews per establishment.**

**Why these two are right:**
- Both are **directly supported by the data**
- Both are **specific and actionable**
- Together they address the two main questions: *where to open* and *how to prepare*

**Why the other options are wrong:**

| Option | Problem |
|---|---|
| "Maximizing price points to attract more reviews — data shows mid-priced shops receive more engagement" | This misrepresents the data. Mid-priced shops get more reviews, but the rating-price correlation shows higher prices hurt ratings. Recommending maximum prices is the opposite of what the data suggests. |
| "Target Lower Manhattan (Zip codes 10001-10020) because it has high density" | High density = high *competition*, which is a reason to *avoid* it, not target it. This recommendation contradicts the analysis. |

---

## 📊 Quick Reference: All Correct Answers

| Q# | Correct Answer |
|---|---|
| Q1 | It lacks narrative and is not well structured |
| Q2 | Nontechnical stakeholders may be distracted; the code isn't necessary for understanding results |
| Q3 | Manhattan, Bronx, Brooklyn, Queens, Staten Island |
| Q4 | Key Insights for New York City Coffee Shop Location |
| Q5 | "Coffee shop ventures face significant competition... Our analysis has identified specific underserved locations..." |
| Q6 | Option B — grouped findings with descriptive headers |
| Q7 | Pre-opening health assessment + Target Zip 11366 (and consider 10026) |
