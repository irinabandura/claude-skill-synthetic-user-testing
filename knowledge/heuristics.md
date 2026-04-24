# Evaluation Frameworks Reference

## Severity Rating Scale (Nielsen)

- **0 — Not a usability problem**
- **1 — Cosmetic only:** Fix if time allows.
- **2 — Minor:** Users can work around with some effort.
- **3 — Major:** Causes significant difficulty; users may fail or abandon.
- **4 — Catastrophic:** Prevents task completion entirely.

---

## Nielsen's 10 Usability Heuristics

### H1: Visibility of System Status
The design should keep users informed about what is going on, through appropriate feedback within a reasonable amount of time.

### H2: Match Between System and the Real World
The design should speak the users' language, with words, phrases, and concepts familiar to the user, rather than internal jargon.

### H3: User Control and Freedom
Users often perform actions by mistake. They need a clearly marked "emergency exit" to leave unwanted actions without extended process.

### H4: Consistency and Standards
Users should not have to wonder whether different words, situations, or actions mean the same thing. Follow platform and industry conventions.

### H5: Error Prevention
Good error messages matter, but the best designs prevent problems from occurring in the first place.

### H6: Recognition Rather Than Recall
Minimize the user's memory load by making elements, actions, and options visible. Users should not have to remember information across screens.

### H7: Flexibility and Efficiency of Use
Shortcuts — hidden from novices — can speed up interaction for experts. The design should cater to both inexperienced and experienced users.

### H8: Aesthetic and Minimalist Design
Interfaces should not contain irrelevant or rarely needed information. Every extra element competes with relevant content.

### H9: Help Users Recognize, Diagnose, and Recover from Errors
Error messages should be in plain language, precisely indicate the problem, and constructively suggest a solution.

### H10: Help and Documentation
It's best if the system needs no documentation, but when help is necessary it should be easy to search, task-focused, and concise.

---

## Don Norman's 7 Fundamental Design Principles

Use these as an optional supplementary lens, especially for onboarding flows, novel interaction patterns, or physical/hardware-adjacent interfaces.

### Discoverability
Can the user figure out what actions are possible and how to perform them?

### Affordances
Do the design elements suggest how they should be used? A button should look pressable; a text field should look editable.

### Signifiers
Are there clear, perceivable indicators that communicate where the user should act? Labels, icons, visual cues.

### Feedback
Does every action produce an immediate, informative, and perceivable response? The user should never wonder "did that work?"

### Mapping
Is the relationship between controls and their effects natural and obvious? Related controls should be near related content.

### Constraints
Does the design prevent errors by limiting possible actions? Graying out invalid options, enforcing input formats, progressive disclosure.

### Conceptual Model
Does the design help users build an accurate mental model of how the system works? Can they predict outcomes of unfamiliar actions?

---

## Cognitive Walkthrough Diagnostic Questions

At each step in the user's task flow, ask:

1. **Will the user know what to do?** Is the correct next action obvious from the persona's perspective?
2. **Will the user see how to do it?** Is the relevant control visible, recognizable, and labeled clearly?
3. **Will the user understand the feedback?** After acting, does the system communicate what happened?
4. **Will the user know they progressed toward their goal?** Is it clear the step succeeded and what comes next?

A "No" to any question is a finding. Map it to the relevant heuristic and assign severity.

---

## Finding Template

```
Heuristic: [H1–H10]
Norman Principle: [if applicable]
Cognitive Walkthrough Q: [Q1–Q4 if applicable]
Data Code: [FIND / COMPREHEND / ACT / EFFICIENCY / FEEDBACK / DELIGHT]
Location: [Where in the portal]
Description: [What the issue is]
Severity: [0–4]
Persona impact: [Which personas affected and how]
Recommendation: [Suggested fix]
```
