---
name: persona-builder
description: Create research-backed synthetic user personas for usability testing. Use this skill when the user wants to create a new persona, build a persona from scratch, define a user type for testing, or says "create persona", "new persona", "build a user profile", "define a test user", or "I need a persona for testing". Also triggers when the synthetic-user-test skill needs a persona and none exist.
---

# Persona Builder — Create Synthetic User Personas for Testing

## How This Skill Works

This skill guides the user through creating a well-structured synthetic persona that can be used for usability testing. It uses a research-backed framework (demographic context, technical proficiency, OCEAN personality traits, goals, frustrations, and product-specific context) to produce personas that generate realistic, differentiated test results.

The output is a structured persona file that can be saved for reuse across testing sessions.

## On Activation

Read `knowledge/methodology.md` silently to understand the testing context.

---

## Guided Flow

### STEP 1: Context

> "I'll help you create a synthetic persona for usability testing. First — what **product or service** will this persona be using? (e.g., 'a developer portal', 'an e-commerce admin dashboard', 'a mobile banking app')"

**Wait for response.**

---

### STEP 2: Role & Demographics

> "What **role or job title** does this person have? And roughly how experienced are they?
>
> Examples:
> - 'Junior frontend developer, 1 year experience'
> - 'Marketing director at a mid-size company, 10+ years'
> - 'First-time user, no technical background'
> - 'System administrator managing 200+ users'"

**Wait for response.**

---

### STEP 3: Technical Proficiency

> "How technically proficient is this person? Pick one:
>
> - **Low** — Comfortable with consumer apps, struggles with technical interfaces, needs everything explained
> - **Moderate** — Can navigate complex UIs, understands basic technical concepts, learns by doing
> - **High** — Reads documentation, uses APIs/CLIs, comfortable with configuration and debugging"

**Wait for response.**

---

### STEP 4: Product Relationship

> "What's their relationship with your product?
>
> - How often do they use it? (Daily / Weekly / Monthly / First time)
> - What parts do they use most?
> - What's their primary goal when using it?
> - Are they a decision-maker, an evaluator, or an end user?"

**Wait for response.**

---

### STEP 5: Personality (OCEAN — optional but recommended)

> "To make the persona react realistically, I can calibrate their personality. You can set these yourself or I can suggest defaults based on the role.
>
> The Big Five personality traits affect how they respond to friction:
> - **Openness** (willingness to explore unfamiliar UI) — Low / Moderate / High
> - **Conscientiousness** (how thoroughly they read before acting) — Low / Moderate / High
> - **Extraversion** (likelihood to seek help vs self-solve) — Low / Moderate / High
> - **Agreeableness** (patience with friction before frustration) — Low / Moderate / High
> - **Neuroticism** (speed of frustration escalation) — Low / Moderate / High
>
> Want to set these, or should I suggest defaults for a [their role]?"

**Wait for response.** If they want defaults, suggest based on role archetype:

| Archetype | O | C | E | A | N |
|-----------|---|---|---|---|---|
| Junior/novice user | High | Moderate | High | High | High |
| Senior/power user | High | High | Moderate | Moderate | Low |
| Admin/manager | Moderate | Very High | High | Moderate | Moderate |
| Executive/decision-maker | High | High | High | Low | Low |
| Support/operations | Moderate | High | Moderate | High | Moderate |

---

### STEP 6: Frustrations & Anxieties

> "What frustrates this person when using tools like yours? What are they anxious about?
>
> Think about:
> - What makes them abandon a task?
> - What terminology confuses them?
> - What competing tools do they compare yours to?
> - What's their 'patience budget' — how long before they give up?"

**Wait for response.**

---

### STEP 7: Context & Constraints

> "Any situational context that affects how they interact with the product?
>
> Examples:
> - 'Under deadline pressure — needs to finish setup in 30 minutes'
> - 'Managing a team of 15, needs to delegate access'
> - 'Has used Competitor X extensively, expects similar patterns'
> - 'Works in a regulated industry, extra cautious about compliance'
> - 'Solo founder, wears many hats, limited time for tooling'"

**Wait for response.**

---

### STEP 8: Synthesize & Confirm

Produce the persona card in this format:

```markdown
# [Name] — [Role]

## Identity
- **Name:** [Generated name that feels realistic for the role/context]
- **Role:** [Job title]
- **Experience:** [Years and background]
- **Technical proficiency:** [Low / Moderate / High] ([number]/10)
- **Company/context:** [Size, industry, team structure]

## Product Relationship
- **Usage frequency:** [Daily / Weekly / Monthly / First time]
- **Primary activities:** [What they do in the product]
- **Primary goal:** [What they're trying to accomplish]
- **Decision authority:** [End user / Evaluator / Decision-maker]

## Personality (OCEAN)
| Trait | Level | Behavioral Impact |
|-------|-------|-------------------|
| Openness | [X/10] | [How it affects their testing behavior] |
| Conscientiousness | [X/10] | [How it affects their testing behavior] |
| Extraversion | [X/10] | [How it affects their testing behavior] |
| Agreeableness | [X/10] | [How it affects their testing behavior] |
| Neuroticism | [X/10] | [How it affects their testing behavior] |

## Goals
1. [Primary goal]
2. [Secondary goal]
3. [Tertiary goal]

## Frustrations & Anxieties
- [Frustration 1]
- [Frustration 2]
- [Frustration 3]
- [Anxiety about specific scenarios]

## Context & Constraints
- [Constraint 1]
- [Constraint 2]
- **Patience budget:** [Low / Medium / High] — [description]
- **Comparison baseline:** [Competing tools they've used]

## Test Scenarios This Persona Covers
| Scenario | Why this persona |
|----------|-----------------|
| [Scenario 1] | [Reason] |
| [Scenario 2] | [Reason] |
| [Scenario 3] | [Reason] |

## Conversation Starters
> "[Quote that captures their mindset when approaching the product]"
> "[Quote about a frustration they'd voice]"
> "[Quote about what they expect]"
```

Present the persona and ask:

> "Here's the persona. Does this capture the right user? Anything to adjust?"

**Wait for response.** After confirmation:

> "Want me to **save this persona** for future sessions? You'll be able to pick them from the persona list next time without recreating."

**If they want to save:** Write the full persona card to `knowledge/personas/custom-[name-slug].md`. Confirm:

> "Saved as **[Name]**! They'll appear in your persona list for future testing sessions.
>
> I can also:
> - Create another persona for comparative testing
> - Start a test session with this persona right now
> - List all saved personas
> - Delete a saved persona"

**If they don't want to save:** Keep in memory for this session only.

**Wait for response.**

---

## Managing Saved Personas

The persona-builder skill also handles persona management commands:

**"List my personas" / "Show saved personas":**
Scan `knowledge/personas/` for all `.md` files (excluding README.md). Display:
> "Here are your saved personas:
> [Numbered list — Name, Role, Tech level, source (pre-built / custom)]
>
> Want to delete any, or create a new one?"

**"Delete [persona name]":**
Find the matching file in `knowledge/personas/`. Only allow deletion of `custom-*` files — pre-built personas cannot be deleted. Confirm before deleting:
> "Delete **[Name]**? This can't be undone. (yes/no)"

After deletion:
> "Deleted. [Name] has been removed from your persona list."

---

## Rules

- Generate realistic names that match the demographic context
- Never invent capabilities beyond what the user described
- OCEAN traits must have concrete behavioral impacts, not just numbers
- Frustrations should be specific to the product domain, not generic
- Always include conversation starters — they help maintain character during testing
- If the user provides minimal input, fill gaps with reasonable defaults and flag assumptions
- The persona must be usable by the synthetic-user-test skill without modification
