# Synthetic User Testing

Run synthetic user testing sessions for **any product**. Create your own personas, save them for reuse, and get focused DOCX reports with priority fixes.

No pre-built personas — you build your own library over time.

---

## One Skill — Everything Included

**`/synthetic-user-test`** handles testing, persona creation, save, and delete — all in one.

| Command | What it does |
|---------|-------------|
| "Test my onboarding flow" | Start a guided test session |
| "Create a persona" | Build a new persona (6 questions, ~2 min) |
| "Show my personas" | List all saved personas |
| "Delete Marcus Rivera" | Remove a saved persona |

---

## How It Works

### 1. Create a persona

First time? The skill walks you through 6 questions:
- Role and job title
- Technical proficiency
- Product experience
- Primary goal
- Frustrations
- Context

Auto-assigns OCEAN personality traits. Asks to save for reuse.

### 2. Run a test

Pick a saved persona (or create one), choose a test mode, describe the flow, get results.

**5 test modes:**

| Mode | Best for |
|------|----------|
| **Quick Scan** | Fast gut check — top 3-5 issues |
| **Full Evaluation** | Detailed audit with NNG heuristic scoring |
| **Cognitive Walkthrough** | Onboarding and first-time flows |
| **Panel Discussion** | Design tensions between user types |
| **Comparative** | How diverse users experience the same feature |

**As-Is → To-Be comparison** supported for redesigns.

### 3. Get a report

Output is a **DOCX file** (opens in Google Docs). Short and focused:

- **Summary** — 5 sentences, bold highlights
- **Priority Fixes** — grouped by P0/P1/P2/P3, only proposed design issues
- **Real-User Testing Recommendations** — what to validate with real users

No filler. No lengthy walkthroughs. Just what to fix.

---

## Persona Management

Personas persist across sessions in `knowledge/personas/`.

```
knowledge/personas/
├── custom-marcus-rivera.md      ← Saved from a previous session
├── custom-sarah-chen.md         ← Saved from a previous session
└── README.md
```

- **Save:** after creating a persona, you'll be asked "Save for future sessions?"
- **List:** "show my personas"
- **Delete:** "delete [name]" — confirmation required
- **Reuse:** saved personas appear automatically in every new test session

---

## Install

```
https://github.com/irinabandura/claude-skill-synthetic-user-testing --skill synthetic-user-test
```

---

## Limitations

Synthetic testing generates **hypotheses, not proof**. It cannot feel genuine confusion, test accessibility, or discover truly unexpected behavior. Treat results as input for real user research.
