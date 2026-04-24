# Synthetic User Testing Plugin

Run synthetic user testing sessions for **any product** using your own personas. No pre-built personas included — you create, save, and manage your own through guided conversations.

---

## Skills

| Skill | Purpose | How to trigger |
|-------|---------|---------------|
| **`/synthetic-user-test`** | Run a guided usability testing session — create or select a persona, choose a test mode, set scenarios, get a focused DOCX report | "test this feature", "what would a user think of this", "usability test", "cognitive walkthrough" |
| **`/persona-builder`** | Create a new persona from scratch through guided questions — save for reuse | "create a persona", "build a user profile", "new persona" |

---

## Your Personas — Create, Save, Reuse, Delete

This plugin ships with **no pre-built personas**. You build your own library over time.

### Create a persona

During a test session or via `/persona-builder`, you'll answer 6 questions:

1. Role and job title
2. Technical proficiency (Low / Moderate / High)
3. Experience with your product
4. Primary goal
5. Frustrations and pain points
6. Context and constraints

The plugin auto-assigns OCEAN personality traits based on the role archetype, then asks you to confirm.

### Save for reuse

After creating a persona, you'll be asked:

> "Want me to **save this persona** for future sessions?"

Saved personas appear in your list every time you start a new test — no need to recreate.

### Delete a persona

Say "delete [persona name]" during any session. Confirmation required.

### List your personas

Say "show my personas" to see all saved personas.

### How it works

```
knowledge/personas/
├── custom-marcus-rivera.md      ← Your saved persona
├── custom-sarah-chen.md         ← Your saved persona
└── README.md
```

---

## 5 Test Modes

| Mode | Best for | Output |
|------|----------|--------|
| **Quick Scan** | Fast gut check | Top 3–5 issues by severity |
| **Full Evaluation** | Detailed usability audit | Full report with NNG heuristic scoring |
| **Cognitive Walkthrough** | Onboarding, first-time flows | Step-by-step "will the user know what to do?" diagnostic |
| **Panel Discussion** | Design tensions between user types | Simulated multi-persona dialogue |
| **Comparative** | How diverse users differ | Side-by-side comparison |

**As-Is → To-Be comparison** supported for redesigns.

---

## Output Format

Reports are generated as **DOCX files** (open natively in Google Docs). Short and focused:

```
┌──────────────────────────────────────────┐
│ Date / Test mode / Personas              │
│                                          │
│ Summary (5 sentences, bold highlights)   │
│                                          │
│ Priority Fixes (P0/P1/P2/P3 tables)     │
│   Issue | Recommendation | Heuristic     │
│                                          │
│ Real-User Testing Recommendations        │
│   What to test | Why | Method            │
│                                          │
│ Disclaimer                               │
└──────────────────────────────────────────┘
```

---

## OCEAN Personality Traits

Each persona gets calibrated Big Five personality traits that control how they react to friction during testing:

| Trait | What it controls |
|-------|-----------------|
| **Openness** | Willingness to explore unfamiliar UI |
| **Conscientiousness** | How thoroughly they read before acting |
| **Extraversion** | Seek help vs self-solve |
| **Agreeableness** | Patience before frustration |
| **Neuroticism** | Speed of frustration escalation |

Traits are auto-assigned by role archetype when you create a persona. You can override them.

> **Note:** OCEAN is based on Costa & McCrae (1992) and Goldberg (1993). Trait levels are calibrated defaults, not psychometric measurements. Override with real research data when available.

---

## Quick Start

### First time — create a persona and test
```
Test my onboarding flow
```
→ Plugin asks you to create a persona → 6 questions → persona created → test runs → DOCX report

### Reuse a saved persona
```
Test the settings page with Marcus Rivera
```

### Create a persona without testing
```
/persona-builder
```

### Manage personas
```
Show my personas
Delete Marcus Rivera
```

---

## Limitations

Synthetic testing generates **hypotheses, not proof**. It cannot:
- Feel genuine confusion, frustration, or delight
- Test accessibility with real assistive technology
- Discover truly unexpected behavior patterns
- Measure real task completion times

Treat results as input for your real research plan.

---

## File Structure

```
synthetic-user-testing/
├── .claude-plugin/
│   └── plugin.json
├── README.md
├── skills/
│   ├── synthetic-user-test/
│   │   └── SKILL.md              ← Guided testing conversation
│   └── persona-builder/
│       └── SKILL.md              ← Create & manage personas
├── knowledge/
│   ├── personas/                 ← Your saved personas go here
│   │   └── README.md
│   ├── methodology.md
│   ├── heuristics.md
│   ├── task-design.md
│   └── generate-report.py        ← DOCX report generator
└── CHANGELOG.md
```
