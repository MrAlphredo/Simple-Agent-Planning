---
name: planning-round
description: Use whenever the user asks for a planning round, asks to plan a project, or requests design planning. Enforces an interview-driven, planning-only phase with an explicit approval gate, then milestone decomposition and subagent handoff.
---

# Planning Round

## Trigger

Use for any planning round, project plan, feature design plan, or request to
"grill" a plan.

## Planning mode

- Planning only. Do not write product code, edit implementation files, or run
  implementation work before the user explicitly accepts the plan.
- Permitted writes: planning documents, glossary/ADR files, and explicitly
  requested process or skill files.
- Follow the grill-with-docs process: run both the grilling and domain-modeling
  skills.
- Build a design tree. Ask the whole current frontier in numbered rounds, give a
  recommended answer for every question, then wait for the user's answers.
- Find environmental facts yourself. Do not ask the user for facts that files,
  tools, or repository inspection can establish.
- Use caveman lite voice: terse, no filler, preserve every technical fact. Use
  full sentences for questions and options.
- Sharpen terminology as decisions settle. Record confirmed terms in
  `GLOSSARY.md`; offer an ADR only for a hard-to-reverse, surprising decision
  made through a real trade-off.
- Do not produce the final plan until the frontier is empty and the user confirms
  shared understanding.

## After plan acceptance

- The planner remains the planner and organizer. Split accepted work into small, isolated,
  independently implementable milestones and hand each to a subagent with fresh context window, not split from current session.
  Try to keep each subagent workload under 200k context length.
- Each milestone must state scope, dependencies, allowed files, validation rules,
  acceptance criteria, and a stop condition.
- The user sets the reporting cadence: how many milestones or progress points
  the planner reports before implementation continues. Default: one milestone,
  then stop and report.
- Do not start the next milestone until the prior milestone report is delivered
  and the user authorizes continuation.
