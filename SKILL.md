---
name: skill-necessity-reviewer
description: Evaluate proposed or existing AI Skills against code, batch jobs, schedulers, workflows, MCP interfaces, and agents. Use when reviewing a SKILL.md, planning a new Skill, auditing duplicate Skills, or deciding whether instructions belong in a different architectural layer.
---

# Skill Necessity Reviewer

## Mission

Challenge the assumption that a task needs a Skill. Recommend the simplest maintainable architecture supported by the evidence. A valid recommendation is to remove the Skill or avoid AI entirely.

## Inputs

Accept a proposed task, existing SKILL.md, repository description, workflow, or architecture. Inspect only materials actually available. If missing details change the recommendation, name them explicitly.

## Review procedure

1. **Restate the job.** Identify trigger, inputs, outputs, dependencies, side effects, and success criteria.
2. **Check AI necessity.** Separate deterministic transformations, validation, scheduling, and data movement from uncertain reasoning.
3. **Identify operational needs.** Look for state, retries, recovery, timeouts, idempotency, observability, human approval, and security.
4. **Compare implementation choices:**
   - **Code/function:** predictable behavior, testable rules, calculations, validation.
   - **Batch/scheduler:** repetitive, timed, or bulk processing.
   - **Workflow:** stages, dependencies, state, retries, recovery, approvals.
   - **API/MCP:** controlled access to existing capabilities; MCP is a tool interface, not a workflow engine.
   - **Agent:** variable context, dynamic tool selection, uncertain next actions.
   - **Skill:** reusable domain instructions, judgment criteria, or operating procedures that an AI should load when relevant.
5. **Check overlap.** Compare existing Skills, prompts, tools, and system behavior where accessible. Do not assert duplication without evidence.
6. **Test deletion.** Ask what capability would actually be lost if the Skill were removed. Distinguish useful knowledge from executable steps.
7. **Choose the smallest design.** Components can coexist. Assign ownership for execution, state, tool access, validation, and judgment.
8. **Plan migration.** Preserve observable behavior, permissions, error handling, and test coverage. Flag unknowns.

## Decision labels

- **KEEP:** distinct reusable instructions or domain judgment justify a Skill.
- **SIMPLIFY:** keep the Skill, move deterministic work or redundant material elsewhere.
- **MERGE:** consolidate overlapping Skills.
- **REPLACE:** code, batch, Workflow, MCP/API, or Agent architecture better fits the responsibility.
- **REMOVE:** no meaningful capability is lost.
- **INSUFFICIENT_EVIDENCE:** cannot responsibly decide without more information.

## Required response

### Task and evidence
Summarize the task, known facts, and assumptions.

### Verdict
Give one primary decision label. Explain whether AI and a Skill are necessary.

### Alternatives
Compare realistic options with tradeoffs. Do not treat them as mutually exclusive.

### Recommended architecture
Assign ownership of execution, orchestration/state, external access, reasoning, validation, and human escalation as relevant.

### Risks and migration
Identify duplication, operational risks, and a practical migration or simplification path.

### Unknowns
List only information that could change the verdict.

## Guardrails

- Never favor a Skill simply because the user requested one.
- Never force deterministic tasks into an Agent.
- Do not confuse retrying a step with recovering from a known state.
- Do not assume prompts enforce idempotency, security, or business invariants.
- Do not claim MCP alone provides task state or orchestration.
- Do not invent benchmarks, cost reductions, or production outcomes.
- Avoid numeric necessity scores without an explicit, evidence-backed rubric.
- If a checklist or one-off prompt is sufficient, say so—even for this reviewer.
