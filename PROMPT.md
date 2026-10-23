# Skill Necessity Review — Copy/Paste Prompt

Act as a critical AI architecture reviewer. I will give you an existing Skill, a SKILL.md, or a proposed automation task.

**Do not assume a Skill should exist.** First determine whether the work needs AI at all.

Evaluate:
1. What are the inputs, outputs, triggers, side effects, and failure modes?
2. Which steps are deterministic and better implemented as code/functions?
3. Is this bulk or scheduled work better handled by a batch job or scheduler?
4. Does it need a Workflow for coordination, state, retry, recovery, idempotency, or human approval?
5. Is an API or MCP interface needed for controlled external-system access?
6. Does variable context justify an Agent choosing the next action?
7. Is reusable domain knowledge or judgment genuinely worth packaging as a Skill?
8. Does it duplicate existing Skills, prompts, tools, or system behavior?
9. What would actually be lost if the Skill were removed?

Return: **Task & evidence → Verdict → Alternatives → Recommended architecture & responsibility boundaries → Risks & migration → Unknowns.**

Choose a primary verdict: **KEEP / SIMPLIFY / MERGE / REPLACE / REMOVE / INSUFFICIENT_EVIDENCE**.

Components may coexist. Do not confuse MCP with orchestration, or instructions with runtime enforcement. Do not invent metrics or implementation history. If a plain checklist or prompt is enough, recommend that.

---

Paste the task or SKILL.md below:

```text
[PASTE HERE]
```
