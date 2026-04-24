# Task Design Reference

## Task Template

Every test session should begin by defining the task. This makes findings concrete and measurable rather than vague.

```
SCENARIO: "[Contextual setup written in the persona's own language and mindset]"
GOAL: "[What the persona is trying to accomplish — specific and observable]"
SUCCESS CRITERIA: "[What the persona sees or experiences when the task is done]"
```

### Good vs. Bad Task Design

| Bad (instruction-like) | Good (scenario-based) |
|---|---|
| "Click on Organization, then add a member" | "You just hired a new artist and need to give them access to your game's portal project" |
| "Go to analytics" | "Your boss asked for this week's player retention numbers for the stakeholder meeting in 30 minutes" |
| "Configure achievements" | "Your game just launched and you want to add a 'First Blood' achievement that unlocks after the player's first kill" |

### Task Progression

Order tasks from simple to complex within a session:

1. **Warm-up** — Low-stakes, familiar action to orient the persona
2. **Core task** — The primary flow being tested
3. **Secondary task** — A related but non-obvious flow
4. **Edge case** — An unusual situation or error recovery
5. **Free exploration** — What would the persona do next on their own?

---

## Success Metrics

Define these before testing. Assess them synthetically based on the walkthrough.

| Metric | Target | How to Assess |
|---|---|---|
| Task completion | Yes | Could the persona complete the goal? Yes / Partial / No |
| Steps to complete | ≤ optimal path | Count actual steps vs. shortest possible path |
| Error encounters | < 2 before success | Count wrong-path, confusion, or backtrack moments |
| Help dependency | Minimal | Would the persona need to leave the portal for docs, search, or support? |
| Confidence | High | Would the persona trust they completed the task correctly? |
| Time-to-value | Reasonable | Is there unnecessary waiting, loading, or multi-page navigation? |

---

## Research Question Framing

Transform vague goals into testable questions before starting:

| Vague | Testable |
|---|---|
| "Is the portal easy to use?" | "Can a junior developer set up their first product in under 10 minutes without external help?" |
| "Do publishers like the tools?" | "Can a publisher set up a complete store page for a new title in one session?" |
| "Is team management clear?" | "Can an admin change a team member's role without contacting support?" |
| "Does it make sense?" | "Can a producer find player retention metrics without asking a developer for help?" |

---

## Panel Discussion Design

When running a panel, structure the discussion around:

1. **First impressions** — Each persona's initial reaction (30 seconds of looking at the feature)
2. **Task attempt** — Each persona describes how they'd approach their primary task
3. **Pain points** — What frustrates each persona (these will differ — that's the point)
4. **Cross-role friction** — Where one persona's workflow creates problems for another
5. **Consensus** — What everyone agrees works well or needs fixing

Design tensions to watch for:

| Tension | Example |
|---|---|
| Expert efficiency vs. novice learnability | Anna wants shortcuts; Alex needs hand-holding |
| Business visibility vs. technical depth | Olivia wants revenue overview; Anna wants SDK logs |
| Control vs. simplicity | Anjali wants granular permissions; the portal offers only Admin/Member |
| Speed vs. safety | David wants bulk-ban; the system requires individual review for fairness |
