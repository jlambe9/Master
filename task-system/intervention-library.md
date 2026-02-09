# Intervention Library — Protocol & Conflict Table

*How to select, compose, and validate intervention stacks for B/A tasks.*
*Driver-specific menus: see `intervention-drivers.md`. Category routing: see `interventions.md`.*
*Full spec: https://claude.ai/chat/da4bc234-ed5e-4635-86e4-d60d6f9ebd00*

## How It Works

1. Agent identifies dominant aversion **drivers** from Layer 0 profile
2. Queries `intervention-drivers.md` for each driver
3. Loads **validated stacks** (PROVEN first, then PRELIMINARY)
4. Checks **conflict table** below for cross-driver conflicts
5. Composes combined stack, flagging untested crossovers
6. Presents to Jamie with confidence levels

## Confidence Levels

| Level | Criteria | Action |
|-------|---------|--------|
| PROVEN | Used 3+ times, positive effect | Use by default |
| PRELIMINARY | Used 1-2 times | Suggest, flag limited data |
| UNTESTED | Never tried | Suggest from default menu, lower priority |
| NOT EFFECTIVE | Used 2+ times, no effect | Deprioritise |
| CONTRAINDICATED | Used 2+ times, negative effect | Never suggest for this driver |

## Conflict Table

| Intervention | Works For | Conflicts With |
|-------------|-----------|----------------|
| Body doubling (engagement) | Zero epistemic, low accountability | High exposure, confrontation (being witnessed amplifies) |
| Music | Zero epistemic, low engagement | Verbal processing, auditory input tasks |
| Preparation script | Interpersonal risk, confrontation | Can cause over-rigidity in fluid conversations |
| Smallest first action | Interpersonal risk, initiation | Tasks where first action IS the aversive part |
| Stimulant timing | Zero epistemic, effort-cost | Hyper-focus on wrong thing risk (stimulant paradox) |
| Draft-first/ship-later | Identity relevance, exposure | Time-critical tasks (can't separate draft from ship) |

## Stack Composition Rules

**Rule 1:** Load validated stacks as units. Don't cherry-pick unless conflict exists.
**Rule 2:** Check conflicts between stacks from different drivers. Drop conflicting interventions.
**Rule 3:** Flag untested crossovers: "These two stacks have NOT been tested together."
**Rule 4:** For untested drivers, suggest from default menu in `intervention-drivers.md`.

## Accumulation (Library Maintenance)

After each execution, Jamie notes what helped (1-2 words). Agent updates:
- Individual interventions: effective / not effective / made worse
- Stack combinations: validated as unit / component conflict detected
- New driver combinations: logged for future reference

## Validated Stacks (populated through use)

*No stacks validated yet. Stacks will be added here as interventions are tested.*
*Format: DRIVER: [driver] → STACK: [interventions] → Status: [PROVEN/PRELIMINARY] (Nx, friction Δ)*
