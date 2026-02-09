# Layer 0 — Task Scoring Dimensions

*Agent computes from task description. Jamie does NOT score manually.*
*If agent can't infer a dimension: ask one clarifying question.*
*CHC key: Gc=knowledge, Gf=reasoning, Gv=spatial, Glr=encoding, Gs=speed, Gwm=working memory, Grw=reading-writing, Ga=auditory, Gk=kinaesthetic, Gsm=short-term memory.*

## 0A: Computational Structure

| Dimension | Scale | How to Score |
|-----------|-------|-------------|
| Information entropy | Low / Med / High | "send email" = Low; "pricing strategy" = High |
| Procedure specification | Specified / Partial / Open | Template/SOP exists? |
| Procedure complexity | Simple / Moderate / Complex | Sub-steps, conditional logic |
| Temporal delay | Immediate / Days / Weeks+ | Action-to-outcome gap |
| Error cost | Reversible / Moderate / High-stakes | Can it be undone? |
| Reward magnitude | Low / Medium / High | £ value, strategic importance |
| Reward probability | Guaranteed / Likely / Uncertain | Does finishing = reward? |
| Value density per unit | Low / Med / High | Each minute productive? |
| Feedback latency | Immediate / Delayed / Very delayed | Know if it worked: seconds? months? |
| Process legibility | Clear / Partial / Opaque | Visible progress at each step? |
| Model maturity | Novel / Familiar / Routine | Done this exact type before? |
| State-tracking load | Low / Med / High | Put down and pick up, or hold the thread? |

## 0B: Channel Requirements

**Input:** Reading (Gc,Grw) · Visual-spatial (Gv) · Listening (Ga,Gc) · Physical (Gk)

**Processing:** Verbal encoding (Glr) · Semantic (Gc,Gf) · Spatial (Gv,Gf) · Sequential (Gsm,Gwm) · Simultaneous (Gf,Gwm) · Pattern detection (Gf) · LT retrieval (Glr) · WM maintenance (Gwm)

**Output:** Speaking (Gc,Glr) · Writing (Gc,Grw,Glr) · Visual/design (Gv) · Physical (Gk,Gs)

**Channel flexibility:** Can this task use alternative cognitive routes?
- Default cultural route: [what most people would use]
- Jamie's best route: [route through Gc/Gf, avoid Glr verbal encoding]

## 0C: Affective Load

| Dimension | Present? | Intensity |
|-----------|----------|-----------|
| Interpersonal risk (judgment/rejection) | Y/N | Low / Med / High |
| Status challenge (autonomy threat) | Y/N | Low / Med / High |
| Exposure / visibility | Y/N | Low / Med / High |
| Uncertain return on effort | Y/N | Low / Med / High |
| Confrontation potential | Y/N | Low / Med / High |
| Identity-relevant outcome | Y/N | Low / Med / High |

## Layer 3 Computation (0 × Profile × State)

```
Epistemic value = entropy × (1 - model maturity) × SEEKING precision
Pragmatic value = reward magnitude × reward probability × pragmatic precision
Effort cost     = complexity × CHC mismatch × current depletion
Threat          = affective load × FEAR/PANIC sensitivity
```

→ Highest signal determines category: E / B / A / M
→ See `interventions.md` for routing
