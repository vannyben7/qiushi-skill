---
name: qiushi-skill
description: |
  Trigger when the user types /qiushi-skill, qiushi-skill, 求是工作流, or asks to start the qiushi workflow. This is the single public entry point for the packaged qiushi method library. Internal methods are bundled reference files and should not appear or be invoked as separate slash-menu skills.
---

# Qiushi Skill

This is the only public skill for the qiushi workflow. The detailed methods live inside `references/` as internal resources, not as independently triggerable skills.

## Invocation

When invoked:

1. Preserve any text after `/qiushi-skill` as the task description.
2. If no task description is provided, ask the user what task or project they want to start.
3. Read `references/workflows/METHOD.md` and select the matching workflow.
4. Whenever the workflow names an internal method, read the corresponding file at `references/<method-name>/METHOD.md` instead of trying to trigger a separate top-level skill.
5. Execute the chosen workflow step by step, explicitly passing each step's output into the next step.

## Internal Method Map

- `workflows`: workflow selection and orchestration.
- `investigation-first`: investigate facts and evidence before judging.
- `contradiction-analysis`: identify the principal contradiction and breakthrough point.
- `concentrate-forces`: choose the main attack direction when effort is scattered.
- `practice-cognition`: test assumptions through practice and update understanding.
- `criticism-self-criticism`: review, audit, and correct completed work.
- `overall-planning`: balance multiple important goals and constraints.
- `mass-line`: collect feedback, synthesize it, and return it as an executable plan.
- `protracted-strategy`: structure long-horizon work into stages.
- `spark-prairie-fire`: start from a small viable foothold and grow outward.

Treat these as one packaged method library under `qiushi-skill`; do not mention them as separate installed skills unless the user asks about the internal structure.
