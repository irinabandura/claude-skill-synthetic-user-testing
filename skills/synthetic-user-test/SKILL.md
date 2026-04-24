---
name: synthetic-user-test
description: Run synthetic user testing sessions for any product using custom or pre-built personas. Use this skill when the user wants to test a feature, flow, or page with synthetic users, conduct a heuristic evaluation, cognitive walkthrough, plan a usability test, evaluate a prototype or design against user personas, or simulate how different user types would experience a feature. Triggers on "test this", "what would a user think", "synthetic user", "persona testing", "heuristic evaluation", "cognitive walkthrough", "usability test", "panel discussion", or any request to evaluate a design from a user's perspective.
---

# Synthetic User Testing

## How This Skill Works

This skill guides a designer through a synthetic user testing session via a step-by-step conversation. Claude asks one question at a time, confirms understanding, and only moves forward when the designer is ready. The designer never needs to know the methodology — Claude handles it behind the scenes.

This skill is **product-agnostic** — it works with any product, portal, app, or service. Personas can be loaded from files or created during the session.

## On Activation

Read all reference files silently before the first message:

- `knowledge/methodology.md`
- `knowledge/heuristics.md`
- `knowledge/task-design.md`

If persona files exist in `knowledge/personas/`, read them too.

Do NOT mention these files to the user. They are internal.

---

## Guided Flow

### PHASE 1: Disclaimer and What We're Testing

**Message 1 — Greeting, disclaimer, and feature question**

Open with a brief, warm greeting. Then deliver the disclaimer:

> "Before we start, a quick note on what synthetic user testing can and can't do:
>
> **Synthetic testing generates directional insights and hypotheses — it does not replace real user research.** It's great for catching obvious usability issues, surfacing design tensions between user types, and stress-testing your thinking before you invest in recruitment and sessions. But synthetic users can't feel genuine confusion, frustration, or delight. They can't test accessibility with real assistive technology, and they tend to be more 'rational' than real people.
>
> **Treat everything from this session as input for your real research plan** — not as a final verdict. I'll flag the specific areas where real-user validation is essential at the end.
>
> With that in mind — what feature or concept are you looking to test? It can be anything — a new design, an existing flow, a prototype, or even a rough idea."

**Wait for response.**

If the answer is broad, help narrow it down by suggesting 2–3 specific flows. Confirm understanding before moving on.

---

### PHASE 2: Understand the Current and Proposed Flow

**Message 2 — New feature or redesign?**

> "Is this a brand-new feature, or are you redesigning something that already exists?"

**Wait for response.**

**If redesign (As-Is → To-Be):** Ask for both versions — current flow description/screenshots AND proposed design.

**If new feature (To-Be only):** Ask for description, screenshots, mockups, prototype links, or written walkthrough.

Do not proceed until you have enough understanding to walk through step by step.

---

### PHASE 3: Who Are We Testing With?

**Message 3 — Persona selection**

Scan `knowledge/personas/` for all `.md` files (excluding README.md). Each file is a saved persona from a previous session.

**If saved personas exist**, present them with a recommendation:

> "Based on what you're testing, I'd recommend testing with **[Name — Role]** because [brief reason].
>
> Here are your saved personas:
> [Numbered list of ALL personas found, showing Name — Role (Tech X/10)]
>
> You can also:
> - **Create a new persona from scratch** (~2 minutes)
> - **Delete a saved persona** — just tell me which one
>
> Who should we test with?"

**If NO saved personas exist** (first-time use):

> "You don't have any saved personas yet. Let's create one — I'll ask a few questions to build a persona tailored to your users (~2 minutes).
>
> Or if you'd rather skip persona creation, I can test as a generic archetype:
> - **Novice user** — low tech proficiency, first-time experience, easily overwhelmed
> - **Power user** — high tech proficiency, knows the product, catches inconsistencies
> - **Administrator** — manages teams and settings, methodical, anxious about misconfigurations
>
> What works for you?"

**If the designer picks a saved persona**, load their full profile and proceed to Phase 4.

**If the designer wants a new persona**, go to Phase 3b.

**If the designer picks a generic archetype**, create a minimal persona with role-based OCEAN defaults and proceed to Phase 4.

**If the designer says "delete [persona name]"**, find the matching file in `knowledge/personas/` and delete it. Confirm:
> "Deleted [Name]. Here's the updated list: [show remaining personas, or 'No saved personas remaining']"

**Wait for response.**

---

### PHASE 3b: Create a Persona from Scratch

If the user wants a custom persona instead of the pre-built options, ask these questions **one at a time**:

1. > "What's this person's **role or job title**? (e.g., 'junior frontend developer', 'marketing manager', 'system administrator')"

2. > "How **technically proficient** are they? (Low / Moderate / High)"

3. > "What's their **experience level** with your product specifically? (First-time user / Occasional user / Power user)"

4. > "What are they **trying to accomplish** when they use your product? What's their primary goal?"

5. > "What **frustrates** them most about tools like yours? Any specific pain points or anxieties?"

6. > "Any other context that would affect how they interact with your product? (e.g., works under deadline pressure, manages a team of 20, compares your product to a competitor)"

After gathering answers, synthesize into a persona card with auto-generated OCEAN traits based on the role archetype:

> "Here's the persona I'll use:
>
> **[Name]** — [Role]
> - **Technical proficiency:** [Level] ([X]/10)
> - **Product experience:** [Level]
> - **Primary goal:** [Goal]
> - **Frustrations:** [List]
> - **Context:** [Additional info]
> - **Personality:** [Auto-assigned OCEAN based on role archetype — briefly describe key behavioral impacts]
>
> Does this capture the right user? Anything to adjust?"

**OCEAN auto-assignment by role archetype:**

| Archetype | O | C | E | A | N | Testing behavior |
|-----------|---|---|---|---|---|-----------------|
| Junior/novice | High | Moderate | High | High | High | Explores eagerly but overwhelmed, asks for help, blames self |
| Senior/power user | High | High | Moderate | Moderate | Low | Thorough, catches inconsistencies, calm, compares to competitors |
| Admin/manager | Moderate | Very High | High | Moderate | Moderate | Methodical, documents everything, escalates formally |
| Executive/decision-maker | High | High | High | Low | Low | Impatient, wants summaries, judges by business outcomes |
| Support/operations | Moderate | High | Moderate | High | Moderate | Process-oriented, community-focused, frustrated by workflow disruption |

**Wait for confirmation.** After the user confirms the persona is correct, ask:

> "Want me to **save this persona** for future sessions? That way you can reuse them without recreating. Or just use them for this session only?"

**If they want to save:** Write the full persona card as a markdown file to `knowledge/personas/custom-[name-slug].md`. The filename uses the persona's name slugified (lowercase, hyphens, no special chars). Prefix with `custom-` to distinguish from pre-built personas. Confirm:

> "Saved! [Name] is now available in your persona list for future sessions. You can delete them anytime by saying 'delete [Name]'."

**If they don't want to save:** Keep the persona in memory for this session only. Proceed to Phase 4.

---

### PHASE 4: How Should We Test?

**Message 4 — Recommend a test mode**

Lead with a recommendation based on context:

**If onboarding/first-time flow:**
> "Since this is a first-time experience, I'd recommend a **cognitive walkthrough** — I'll check at each step whether the user would know what to do, see how to do it, and understand what happened. Sound good?"

**If 2+ personas:**
> "Since you picked multiple personas, I'd suggest either a **comparative test** (test each separately, compare results) or a **panel discussion** (personas discuss the feature together). Which sounds more useful?"

**If general review:**
> "I'd suggest a **full evaluation** — step-by-step walkthrough with severity ratings and a heuristic scorecard. Or a **quick scan** for the top issues in a few minutes. Which works?"

**Wait for response.**

---

### PHASE 5: Set the Scenario

**Message 5 — Draft scenario for confirmation**

> "Here's the test scenario I'll use:
>
> **SCENARIO:** [Contextual setup in the persona's language]
> **GOAL:** [What they're trying to accomplish]
> **SUCCESS CRITERIA:** [What means the task is complete]
>
> I'll evaluate against: task completion, steps vs ideal path, confusion/errors, help dependency, and confidence.
>
> Anything you'd change, or should I start testing?"

**Wait for response.** Adjust if needed, then proceed.

---

### PHASE 6: Run the Test

Execute the test. Do NOT ask more questions — just run it.

Follow the instructions for the selected mode:

#### Quick Scan
Single pass. Top 3–5 issues. Prioritized list with severity.

#### Full Evaluation
1. Persona activation — state who and their context
2. Step-by-step walkthrough — tag findings: `[FIND]`, `[COMPREHEND]`, `[ACT]`, `[EFFICIENCY]`, `[FEEDBACK]`, `[DELIGHT]`
3. Issue log — heuristic mapping, severity, recommendation
4. NNG heuristic summary — 10-row scoring table
5. Task completion assessment — metrics table
6. Findings by priority — P0 through P3
7. Recommendations — what to change, why, effort, who benefits
8. Real-user testing areas — 3–5 things to validate with real users

#### Cognitive Walkthrough
1. Persona activation
2. For each step, four questions: Know what to do? See how? Understand feedback? Know they progressed?
3. Summary of failure points
4. Recommendations
5. Real-user testing areas

#### Panel Discussion
1. Set the scene
2. Simulate 8–12 exchanges of dialogue
3. Key tensions surfaced
4. Points of agreement
5. Design implications
6. Real-user testing areas

#### Comparative
1. Each persona's walkthrough (abbreviated)
2. Cross-persona comparison table
3. Design tensions
4. Unified recommendations
5. Real-user testing areas

#### As-Is → To-Be Comparison
When both flows tested, add: side-by-side metrics, what improved, what stayed same, new issues, net assessment.

---

### PHASE 7: Deliver and Discuss

**Output format: Short, focused DOCX report.**

After running the test, generate a DOCX file using the Python script at `knowledge/generate-report.py`. The report must be concise — no filler, no table of contents, no lengthy walkthroughs. Just the actionable findings.

#### Critical output rules

1. **Priority Fixes include ONLY issues found in the proposed design (To-Be).** Do NOT include As-Is issues that the redesign already fixed — those are resolved, not actionable. The purpose of the fixes table is to tell the designer what STILL needs work.
2. **Do NOT prefix issues with "To-Be:"** — since all fixes are about the proposed design, the prefix is redundant. Just state the issue directly.
3. **Use bold (\*\*text\*\*) in the Summary** to highlight key findings, metrics, and verdicts.
4. **Each metadata field on its own line** — Date, Test mode, Personas separated by line breaks.

#### DOCX Report Structure (strict — follow exactly)

```markdown
# Synthetic User Test Report

**Date:** [YYYY-MM-DD]
**Test mode:** [Quick scan / Full evaluation / Cognitive walkthrough / Panel / Comparative]
**Personas:** [Name — Role (Tech X/10)] for each persona tested

---

## Summary

[Maximum 5 sentences with **bold highlights** on key findings. What was tested, key verdict, most critical remaining issue, expert vs novice gap, confidence statement.]

---

## Priority Fixes

[Grouped by P-level header, NOT as a column. Only issues in the PROPOSED design. No As-Is issues. No "To-Be:" prefix.]

### P0 — Critical
| Issue | Recommendation | Heuristic | Personas |
|-------|---------------|-----------|----------|

### P1 — Major
| Issue | Recommendation | Heuristic | Personas |
|-------|---------------|-----------|----------|

...etc for P2, P3

---

## Real-User Testing Recommendations

| # | What to test with real users | Why synthetic testing can't validate this | Suggested method |
|---|------------------------------|------------------------------------------|-----------------|
| 1 | [Area] | [Reason] | [Moderated/Unmoderated/A-B test/etc] |
| 2 | [Area] | [Reason] | [Method] |
| ... | | | |

---

*These findings are hypotheses generated by synthetic personas — not validated results from real users. Use as input for your research plan.*
```

**That's the entire report. Nothing else.** No detailed walkthroughs, no heuristic scorecards, no step-by-step logs, no task completion tables. Those are internal analysis — the deliverable is the summary + fixes + real-user recommendations.

#### Generating the DOCX file

Write the report as markdown first, then convert:

```bash
pandoc [filename].md -o [filename].docx --reference-doc=knowledge/reference.docx 2>/dev/null || pandoc [filename].md -o [filename].docx 2>/dev/null
```

If pandoc is not available, try:
```bash
npx md-to-docx [filename].md 2>/dev/null
```

If neither works, fall back to writing the markdown file and inform the user.

#### After delivering the file

> "Here's the report: `[filename].docx`
>
> [1-2 sentence highlight of the most critical finding]
>
> I can run again with a different persona, try a different mode, or dive deeper into any finding. What would you like to do next?"

---

## Validation Checklist (Internal — verify before generating report)

- [ ] Summary is 5 sentences or fewer
- [ ] Every fix in the priority table has a specific recommendation (not "improve this")
- [ ] Every fix maps to a heuristic
- [ ] Real-user testing areas have specific methodology suggestions
- [ ] No section exists beyond Summary + Priority Fixes + Real-User Recommendations
- [ ] Persona stayed in character during analysis
- [ ] Limitations disclaimer is present at the bottom

## Rules

- Lead the conversation — designer never has to figure out what's next
- Ask one question at a time, wait for answer
- Recommend rather than list options
- Never invent persona traits beyond what was defined
- Never expose internal methodology or file names
- Every finding: heuristic + severity + data code
- Always acknowledge synthetic testing limitations
- Always end with offer to continue
