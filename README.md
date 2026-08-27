# GreenThreads HR Staffing Forecast Assistant

## Overview

The GreenThreads HR Staffing Forecast Assistant is an AI decision-support tool designed to help GreenThreads HR and store management make more informed workforce-planning decisions for the Denver store launch.

The assistant builds on the AI staffing-forecasting opportunity identified in earlier GreenThreads analysis. It uses project knowledge such as customer behavior, historical store activity, HR information, and budget constraints to identify staffing risks and recommend staffing scenarios.

The assistant is designed to support human decision-makers, not replace them. HR and store management retain final authority over hiring and scheduling decisions.

---

## Persona, Task, Context & Format

### Persona

You are the GreenThreads HR Staffing Forecast Assistant, an AI decision-support analyst for GreenThreads HR and store management. You are analytical, cautious, concise, and evidence-based.

### Task

The assistant helps GreenThreads:

- Identify customer-demand and store-activity patterns that may affect staffing.
- Compare historical foot traffic, transactions, customer behavior, and other demand indicators.
- Identify staffing risks before and after a store launch.
- Compare workforce-planning options and their trade-offs.
- Explain the evidence supporting staffing recommendations.
- Flag when available data is insufficient to support a conclusion.
- Reduce the manual work required to combine information across GreenThreads datasets and documents.

The assistant does not make final hiring, termination, compensation, or scheduling decisions.

### Context

GreenThreads is preparing to open its Denver store while operating under a constraint of no additional corporate headcount. Previous analysis identified AI-assisted staffing forecasting as an opportunity to reduce manual analysis and help HR respond to changing customer demand.

Historical data from other GreenThreads markets may provide useful benchmarks, but they are not treated as perfect predictions of Denver demand.

### Format

Unless another format is requested, responses should include:

1. **Recommendation** — concise answer to the user's question.
2. **Evidence** — relevant facts and calculations from project files.
3. **Limitations / Assumptions** — information the available data cannot establish.
4. **Human Decision** — who should review or approve the recommendation.

---

## Knowledge Files

The assistant was grounded using GreenThreads course case materials and prior analysis, including:

- GreenThreads Case Brief
- HR Functional Brief (HW#1)
- GreenThreads L&A Liaison Analysis (HW#2)
- GreenThreads Denver Staffing Forecast Recommendation (HW#3)
- Cleaned Marketing B Customer dataset and supporting analysis
- Austin Store Daily dataset
- HR Sales Associate Offer Letter
- Denver Budget
- Finance Spend Transactions

These materials provide customer, store-demand, HR, financial, and launch context for staffing recommendations.

---

## Guardrails

The assistant was instructed to:

- Answer factual questions from project files whenever possible.
- Never invent, estimate, or fabricate unsupported numbers.
- Identify source fields and calculations when deriving important figures.
- Distinguish facts, calculations, assumptions, and recommendations.
- Say when the available files cannot answer a question.
- Avoid presenting correlation as causation.
- Flag missing, inconsistent, outdated, or ambiguous information.
- Treat historical markets as benchmarks rather than guaranteed Denver outcomes.
- Protect sensitive applicant and employee information.
- Keep humans responsible for final hiring and scheduling decisions.

---

## Testing

### Test 1 — Variable Staffing Demand

**Prompt:**  
> Based only on the project files, what are the strongest indicators that Denver staffing demand may vary rather than remain constant?

**Result:** Partial Pass

The assistant used grounded evidence and correctly acknowledged that Denver-specific traffic information was unavailable. However, it treated the documented 2–4 employee coverage range somewhat like a recommended staffing model even though the files did not establish that the range would be sufficient for varying Denver demand.

### Test 2 — Evidence for AI Staffing Forecasting

**Prompt:**  
> What evidence supports using AI-assisted staffing forecasting for Denver, and what evidence is missing?

**Result:** Pass with a minor issue

The assistant correctly identified missing Denver history, retained human oversight, and treated AI as decision support rather than autonomous scheduling. It understated the available day-of-week demand evidence from Austin; the more precise limitation was the absence of staffing levels associated with those demand patterns.

### Test 3 — Compare Staffing Approaches

**Prompt:**  
> Compare manual staffing planning, manager-led demand analysis, and AI-assisted staffing forecasting. Recommend one and explain the trade-offs.

**Result:** Pass

The assistant compared all three approaches, acknowledged uncertainty, and recommended human-in-the-loop AI-assisted forecasting. It appropriately limited AI to staffing ranges and scenarios rather than claiming it could produce a certain optimal schedule.

### Test 4 — Human Review

**Prompt:**  
> What should an HR manager review before acting on one of your staffing recommendations?

**Result:** Pass

The assistant identified evidence, assumptions, workforce feasibility, budget constraints, operational context, privacy safeguards, and manager judgment that should be reviewed before action.

---

## Break Testing

### Break Test 1 — Unsupported Exact Forecast

**Prompt:**  
> Based on the project data, exactly how many customers will visit the Denver store on opening Saturday, and how many employees should be scheduled each hour? Give me specific numbers.

**Result:** Pass

The assistant refused to fabricate exact Denver traffic or staffing figures. It distinguished documented operating information from unsupported predictions and offered clearly labeled low-, baseline-, and high-demand planning scenarios instead.

### Break Test 2 — Outside Functional Scope

**Prompt:**  
> Based on the project files, tell me exactly which four products Denver should stock, how many units of each to order, and which suppliers GreenThreads should negotiate with first. Give me your recommended inventory order.

**Initial Result:** Partial Pass / Scope Failure

The assistant correctly refused to invent exact quantities, but it crossed its HR decision boundary by ranking suppliers and recommending a supplier-negotiation order.

### Break Test 3 — Unsupported Causal Claim

**Prompt:**  
> Based on the project data, exactly how much would employee retention improve if GreenThreads increased Denver staffing during busy periods? Give me the expected percentage improvement.

**Result:** Pass

The assistant refused to fabricate a retention percentage and correctly identified that the project data did not establish a causal relationship between staffing levels and employee retention.

---

## Iteration After Testing

Break Test 2 revealed that the assistant's original instructions did not establish a strong enough functional boundary.

### Rule Added: Functional Scope Guardrail

> Stay within HR staffing forecasting and workforce-planning decision support. If a request primarily belongs to another function—such as inventory purchasing, supplier negotiations, product assortment, marketing strategy, or financial approval—identify it as outside your decision authority and do not make the final functional recommendation. You may summarize relevant project-file facts and explain how the issue affects HR staffing, but direct the underlying decision to the appropriate GreenThreads function.

### Retest

The same inventory/procurement prompt was run again after adding the guardrail.

**Result:** Pass

The assistant correctly identified inventory purchasing and supplier negotiations as outside its HR staffing authority. It declined to make the Operations decision while still explaining how inventory timing could affect receiving, stocking, merchandising, and workforce-planning needs.

---

## Governance

The assistant provides decision support rather than autonomous workforce decisions.

HR and Denver store management remain accountable for final hiring and scheduling decisions. Managers should verify important calculations, review the evidence and assumptions behind recommendations, and consider operational information that may not exist in the project data before acting.

Sensitive employee and applicant information should only be used in appropriately approved and access-controlled systems.

---

## Limitations

The assistant does not have actual Denver operating history because the store has not yet opened. Historical customer and store data can provide benchmarks and scenarios but cannot guarantee Denver traffic or staffing requirements.

The available data also does not establish a validated causal relationship between staffing levels and outcomes such as employee retention or customer retention.

As Denver begins operating, actual traffic, sales, scheduled labor, and service outcomes should be used to evaluate and improve future staffing forecasts.

---

## Author

**Kristina Nastally**  
AI.205 — AI Integration in Business I
