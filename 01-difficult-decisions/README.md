# Case 1 — Making a Difficult Decision

> *Should I quit my stable job to start my own business?*

## The problem

Big life decisions — quitting a stable job, buying vs. renting, accepting an offer — are often made on gut feeling. Numbers and emotions get mixed up, hidden costs are overlooked, and there is no clear criterion for *when* the right moment has come.

## The solution

A structured prompt that turns Claude into a **decision-structuring partner, not a decision-maker**. It follows three prompt elements:

| Element | What it does |
|---|---|
| **Setting the stage** | Role, objective and context (with real numbers) |
| **Defining the task** | Concrete, numbered actions |
| **Specifying rules** | Tone, format, an example — and "don't decide for me" |

The first answer is then refined through **iteration**: specific feedback, error correction and follow-up with new information.

## The scenario (fictional)

| | |
|---|---|
| **Person** | Mariana, 34, married, one 5-year-old daughter |
| **Current job** | Marketing analyst with a formal employment contract (CLT), R$ 8,500/month |
| **Spouse** | Formal employee (CLT), R$ 6,000/month |
| **Family expenses** | ~R$ 11,000/month |
| **Business idea** | Digital marketing consultancy for small local businesses |
| **Traction** | 3 freelance clients, ~R$ 2,000/month |
| **Savings** | R$ 45,000 |
| **Main fears** | Losing health insurance, job benefits, unstable income, not being able to return to the job market |

> **Brazilian context:** *CLT* is Brazil's formal employment regime, which includes benefits such as *FGTS* (a mandatory severance savings fund), a 13th-month salary and paid vacation. Leaving it means giving up these protections.

## Prompts

> The prompts were originally written and tested in Portuguese. The versions below are English translations.

### 1. Initial prompt

```
## ROLE
Act as a career and personal finance consultant who specializes in helping Brazilian professionals evaluate the transition from formal (CLT) employment to entrepreneurship.

## OBJECTIVE
I want help deciding whether I should quit my CLT job now to dedicate myself fully to my own business, or whether I should wait.

## CONTEXT
- I am 34 years old, married, with a 5-year-old daughter.
- I work as a marketing analyst (CLT) at a mid-sized company, earning R$ 8,500 per month.
- My husband is also a CLT employee and earns R$ 6,000.
- Our family expenses are about R$ 11,000 per month.
- I want to open a digital marketing consultancy for small businesses (restaurants, salons, neighborhood stores).
- I already serve 3 clients as a freelancer, in the evenings and on weekends, earning about R$ 2,000 per month.
- I have R$ 45,000 in savings.
- My biggest concerns are: losing the company health insurance, which covers the family; giving up FGTS, the 13th-month salary and paid vacation; unstable income with a young daughter; and the fear of not being able to return to the job market if it doesn't work out.

## TASK
1. Calculate how long our savings will support the family if I quit now, considering my husband's income and my current clients.
2. Build three scenarios for the first 12 months: pessimistic, realistic and optimistic.
3. List the pros and cons of quitting now versus waiting a while longer.
4. Point out the risks I may not be seeing.
5. Suggest objective milestones that would indicate the right time to quit (for example, number of clients or minimum revenue).
6. Ask me 5 questions I should answer for myself before deciding.

## RULES
- Tone: direct, honest and realistic, neither pessimistic nor motivational.
- Format: use headings for each part and tables for the scenarios and for the pros and cons.
- Show your calculations so I can check them.
- Do not make the decision for me. Your role is to structure the decision, not to decide.
- If any important information is missing for the analysis, tell me what it is and explain why it matters.
- Example of the expected format for the milestones:
  "Milestone: revenue of R$ 6,000/month for 3 consecutive months. Why: it covers the gap between my husband's income and our expenses."
```

### 2. Feedback and correction

```
I really liked the structure and the risks you raised, especially the ones about health insurance and FGTS.

But I found a problem: in the realistic scenario, you say the lowest point of the savings is R$ 22,600 in month 9. Recalculating quarter by quarter, the accumulated deficit up to month 9 is about R$ 24,200, so the savings drop to around R$ 20,800 that month, and R$ 22,600 is the year-end balance. I also noticed that expenses including the new costs appear as R$ 13,100 in section 1 and R$ 13,000 in section 2.

Please review these calculations and correct the scenarios table.
```

### 3. Follow-up with new information

```
Answering your questions: the salaries are gross, my husband's health plan allows me and my daughter to be added as dependents for R$ 600/month, and the 3 clients have no contracts.

With this information, redo the analysis using Reading B (gross salaries) and give me:
1. A summary of no more than 5 lines at the top, with the main conclusion.
2. Only the updated scenarios table and the 3 most important milestones.
```

## What happened

**Initial response.** Claude delivered every requested section: runway calculation, three 12-month scenarios, pros and cons, hidden risks, objective milestones and self-reflection questions. It also flagged missing information on its own (gross vs. net salary) and ran the numbers both ways. It surfaced risks most people would miss, such as losing access to FGTS when resigning, health insurance waiting periods and a tax rule that can more than double the tax rate for small service companies.

**Error found.** Because the prompt required visible calculations, it was possible to check them. One table confused the lowest point of the savings with the year-end balance, and one expense figure was inconsistent between sections.

**Correction.** Claude acknowledged both errors, fixed them, and **found a third error by itself** (the break-even month in the optimistic scenario was month 7, not month 5).

**Follow-up.** With the new information, Claude rebuilt the analysis and delivered exactly the requested short format:

| | Pessimistic | Realistic | Optimistic |
|---|---|---|---|
| Lowest point of savings | R$ 0 (month 9) | ~R$ 20,000 (month 9) | ~R$ 34,100 (month 6) |
| Break-even | Not reached | Month 10 | Month 7 |

Top milestones before quitting: contracts of at least 6 months with clients, R$ 4,000/month of recurring revenue for 3 consecutive months while still employed, and an average ticket of at least R$ 1,000 per client.

## Lessons learned

1. **Real numbers beat generic questions.** Concrete context produced concrete scenarios instead of motivational advice.
2. **"Show your calculations" makes the output verifiable.** That rule is what made the errors visible.
3. **Always check the math.** AI can make arithmetic slips; verification is part of the process.
4. **Specific feedback works.** Saying what was good *and* pointing to the exact error led to a precise correction.
5. **"Don't decide for me" keeps the human in charge.** Claude structured the decision without taking it.
6. **Iteration adds value.** The final answer was shorter, more accurate and
