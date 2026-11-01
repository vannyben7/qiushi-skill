---
name: qiushi-skill
description: Trigger when the user types /qiushi-skill, qiushi-skill, 求是工作流, or asks Qoder to start a qiushi workflow. This is the single public Qoder Skill entry point for the packaged method library. Run one method alone when the user names one (矛盾分析法, 调查研究, 集中兵力, 实践认知, 批评与自我批评, 统筹兼顾, 群众路线, 持久战略, 星火燎原), then report only that method's output; run the full packaged workflow when they invoke the entry point without naming a method. Internal methods are bundled references and must not appear or be invoked as separate Skills or custom Agents.
---

# Qiushi Skill

Use this as the only public Qoder Skill for the qiushi workflow. Keep detailed methods inside `references/` as internal resources, not independently triggerable Skills, Commands, Experts, or custom Agents. Qoder discovers this package from `SKILL.md` and does not depend on legacy UI metadata.

## Attribution

The original qiushi method library was authored by HughYau. This packaged Qoder edition was adapted and optimized by vannyben7 while preserving the original method sources and public entry-point intent.

## Invocation

When invoked:

1. Preserve any text after `/qiushi-skill` as the task description.
2. If no task description is provided, ask the user what task or project they want to start.
3. Check whether the request names a specific internal method (see Single-method dispatch below). If it does, run only that method. Otherwise resolve `references/workflows/METHOD.md` relative to this `SKILL.md`, read it, and select the matching workflow.
4. Whenever the workflow names an internal method, read the corresponding file at `references/<method-name>/METHOD.md` instead of trying to trigger a separate top-level skill.
5. Execute the chosen workflow step by step, explicitly passing each step's output into the next step.

## Single-method dispatch

A method can be run on its own without starting the packaged workflow. This still goes through this one Skill; it does not mean the method became a separate Skill or Agent.

Trigger it when the user names a method in any language ("用矛盾分析法看这个", "先做调查研究", "按 mass-line 收口", "集中力量打一处"), passes a method key right after `/qiushi-skill`, or when the task clearly matches exactly one row of the Internal Method Map.

To run method `<method-name>`: read only `references/<method-name>/METHOD.md`, apply it to the stated task, and report that method's own outputs. Do not load `references/workflows/METHOD.md`, do not run the other methods, and do not announce a full workflow. A bare `/qiushi-skill`, `求是工作流`, or `/qiushi-skill <task text>` with no method named still runs the full packaged workflow through `workflows`.

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

Treat these as one packaged method library under `qiushi-skill`; do not register, generate, or mention them as separate installed Skills or custom Agents unless the user asks about the internal structure.

## Slash-menu and Edict discipline

- Keep `qiushi-skill` as the only public entry for this method library. Files below `references/` stay inside this package and are never registered as separate Skills, Agents, Commands, or slash-menu entries.
- When Edict coordinates a qiushi preflight, use the single `edict-agent` Skill plus Qoder's built-in Experts. Internal qiushi methods remain references; they do not become Agents.
- Edict's fixed-name roles are installed user-level by the `edict-agent` Skill on Qoder; on Codex they stay prose checklists. Either way, qiushi itself never installs Agents, globally or project-locally.
