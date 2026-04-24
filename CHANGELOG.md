# Changelog

## 1.0.0 (2026-04-22)

### Added
- **synthetic-user-test skill** — guided 7-phase testing conversation
  - 5 test modes: quick scan, full evaluation, cognitive walkthrough, panel discussion, comparative
  - As-Is → To-Be comparison for redesigns
  - NNG heuristic evaluation (10 heuristics, severity 0-4, priority P0-P3)
  - DOCX report output (landscape, focused format)
  - Generic archetype fallback (novice/power user/admin) when no personas exist

- **persona-builder skill** — create, save, and manage personas
  - 6-step guided creation with OCEAN personality auto-assignment
  - Save to knowledge/personas/ for reuse across sessions
  - List and delete saved personas
  - No pre-built personas — you build your own library

- **Knowledge base**
  - methodology.md — test modes, criticality, data coding, limitations
  - heuristics.md — Nielsen's 10, Don Norman's 7, severity scale, cognitive walkthrough questions
  - task-design.md — task templates, success metrics, panel discussion design
  - generate-report.py — DOCX generator with landscape layout, grouped priority tables
