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

The first answer is then refined through **iteration**: specific feedback, error correction and follow-up with new information. Finally, the same prompt was run **three times** to test how consistent the results are.

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

## Full outputs

The complete, unedited responses from Claude (in the original Portuguese) are available here:

| File | Content |
|---|---|
| [run-1-output.md](run-1-output.md) | Run 1: initial response, correction and follow-up |
| [run-2-output.md](run-2-output.md) | Run 2: initial response only |
| [run-3-output.md](run-3-output.md) | Run 3: initial response only |

## What happened (Run 1)

**Initial response.** Claude delivered every requested section: runway calculation, three 12-month scenarios, pros and cons, hidden risks, objective milestones and self-reflection questions. It also flagged missing information on its own (gross vs. net salary) and ran the numbers both ways. It surfaced risks most people would miss, such as losing access to FGTS when resigning, health insurance waiting periods and a tax rule that can more than double the tax rate for small service companies.

**Error found.** Because the prompt required visible calculations, it was possible to check them. One table confused the lowest point of the savings with the year-end balance, and one expense figure was inconsistent between sections.

**Correction.** Claude acknowledged both errors, fixed them, and **found a third error by itself** (the break-even month in the optimistic scenario was month 7, not month 5).

**Follow-up.** With the new information, Claude rebuilt the analysis and delivered exactly the requested short format:

| | Pessimistic | Realistic | Optimistic |
|---|---|---|---|
| Lowest point of savings | R$ 0 (month 9) | ~R$ 20,000 (month 9) | ~R$ 34,100 (month 6) |
| Break-even | Not reached | Month 10 | Month 7 |

Top milestones before quitting: contracts of at least 6 months with clients, R$ 4,000/month of recurring revenue for 3 consecutive months while still employed, and an average ticket of at least R$ 1,000 per client.

## Consistency test: same prompt, three runs

The same initial prompt was run in three separate chats to see what changes.

| | Run 1 | Run 2 | Run 3 |
|---|---|---|---|
| Structure (6 requested sections) | ✅ | ✅ | ✅ |
| Estimated monthly fixed cost | R$ 12,980 | R$ 13,600 | R$ 13,200 |
| Health insurance assumption | R$ 1,500 | R$ 2,000 | R$ 1,800 |
| Tax assumption | 6% | 6% | 15% (taxes + social security) |
| Savings runway (adjusted) | 8.8 months | 7.9 months | 8.2 months |
| Runway keeping a R$ 15,000 emergency floor | ~6 months | 5.2 months | 5.5 months |
| Revenue needed to break even | R$ 7,430 | R$ 8,100 | R$ 8,500 |
| Clients needed at current ticket | ~11 | ~12 | ~13 |
| Pessimistic: savings run out | Month 9 | Month 9 | Month 9 |
| Realistic scenario | Break-even in month 10 | Almost breaks even | Savings run out in month 12 |
| Optimistic break-even | Month 7 | Month 7 | ~Month 9 |
| Calculation method | Quarter by quarter | Quarter by quarter | Annual averages |
| Calculation errors | 3 (fixed through iteration) | None (one text contradiction) | None |
| Main conclusion | Same | Same | Same |

**What stayed the same:** structure, core risks, savings runway (~8–9 months), the pessimistic scenario (savings run out in month 9 in all three runs) and the main conclusion.

**What changed:** the assumptions the AI had to estimate (health insurance, taxes, growth pace). This made the realistic scenario swing from "breaks even in month 10" to "savings run out in month 12". The calculation method also changed between runs.

**Core risks found in all three runs:** no access to FGTS when resigning (and the mutual-agreement alternative), health insurance waiting periods, tax regime choice, the family depending on a single formal income, high churn among small clients, unpaid time spent selling, low average ticket and delivery capacity, non-compete clauses and reduced social security protection.

**Bonus:** each run surfaced at least one useful idea the others missed. Run 3, for example, suggested the cheapest test of all: asking the 3 current clients whether they would pay more for more availability.

## Lessons learned

1. **Real numbers beat generic questions.** Concrete context produced concrete scenarios instead of motivational advice.
2. **"Show your calculations" makes the output verifiable.** That rule is what made the errors visible.
3. **Always check the math.** AI can make arithmetic slips; verification is part of the process.
4. **Specific feedback works.** Saying what was good *and* pointing to the exact error led to a precise correction.
5. **"Don't decide for me" keeps the human in charge.** Claude structured the decision without taking it.
6. **Iteration adds value.** The final answer was shorter, more accurate and more useful than the first one.
7. **Same prompt, different runs.** Structure and conclusions are stable, but numbers vary with the assumptions and methods the AI chooses. Supplying key assumptions and specifying the method makes results more consistent.
8. **For important decisions, run it more than once.** Each run surfaced different risks and ideas, so multiple runs give a fuller picture.

## How to reuse

Copy the initial prompt and replace the **CONTEXT** section with your own situation: a job offer, buying vs. renting, a career change. Keep the structure, the rules and the iteration steps.

To get more consistent results:
- Provide the key assumptions yourself (for example, the real cost of health insurance and whether salaries are gross or net).
- Specify the calculation method (for example, "calculate month by month").

> Note: AI responses vary between runs. Your output will differ in wording and assumptions, but the structure and main conclusions should be similar.
