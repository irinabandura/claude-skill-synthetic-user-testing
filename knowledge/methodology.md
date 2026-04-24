# Synthetic User Testing — Methodology

## What Are Synthetic Users?

Synthetic users are AI-generated participants that simulate user behavior based on defined persona profiles. They are best used for directional insight, not final validation.

## When to Use

**Good for:** Exploratory research, hypothesis generation, concept/prototype evaluation, feature validation for obvious usability issues, UX and copy evaluation, scaling testing across persona types quickly.

**Not suitable for:** Final validation, measuring emotional responses, accessibility compliance, discovering truly unexpected behavior, social trust or brand perception.

## Test Modes

| Mode | Best for | Participants | Output |
|---|---|---|---|
| Quick scan | Early feedback, time-constrained | 1 persona | Top issues list |
| Full evaluation | Detailed usability audit | 1 persona | Full report with heuristics |
| Cognitive walkthrough | Onboarding, first-time flows | 1 persona (usually novice) | Step-by-step diagnostic |
| Panel discussion | Design tensions, stakeholder alignment | 2–4 personas | Simulated dialogue + tensions |
| Comparative | Understanding diverse needs | 2–3 personas | Side-by-side comparison |

## Criticality Framework

| Level | Label | Definition | Action |
|---|---|---|---|
| P0 | Catastrophic | Blocks task completion. No workaround. | Fix immediately. |
| P1 | Major | Significant difficulty. Users may fail or abandon. Workaround is hard to find. | Fix before next release. |
| P2 | Minor | Creates friction but doesn't prevent completion. | Plan for upcoming sprint. |
| P3 | Cosmetic | Aesthetic or wording issue. No task impact. | Backlog. |

## Data Coding Tags

Tag each observation during the walkthrough:

| Tag | Meaning | Example |
|---|---|---|
| `[FIND]` | Discoverability issue | User can't locate the settings page |
| `[COMPREHEND]` | Terminology or mental model mismatch | "Sandbox" meaning unclear |
| `[ACT]` | Cannot complete action or makes error | Clicks wrong button, form rejects valid input |
| `[EFFICIENCY]` | Unnecessary steps or slowness | Must navigate 5 pages for a 2-step task |
| `[FEEDBACK]` | Missing or unclear system feedback | No confirmation after saving |
| `[DELIGHT]` | Something works well or exceeds expectations | Clear inline help tooltip |

## Limitations (Always Acknowledge)

- Synthetic users cannot experience genuine confusion, emotion, or fatigue
- They cannot test accessibility with real assistive technology
- They tend to be more "rational" than real users
- Findings are hypotheses to validate with real users, not final evidence
- The AI may have biases toward finding issues (or missing them)
- Synthetic users cannot discover truly novel or unexpected behavior patterns
