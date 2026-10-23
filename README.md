# Skill Necessity Reviewer

> **Do you really need another Skill?**

An opinionated architecture reviewer that challenges whether a proposed AI Skill should exist at all.

Before writing another `SKILL.md`, compare **code, batch jobs, schedulers, workflows, MCP tools, and agents**. The best outcome may be **no Skill**—or no AI.

## Why

Skills can provide reusable domain instructions and judgment criteria. But deterministic validation, scheduling, retries, recovery, and system access deserve explicit engineering boundaries. A Skill is not a workflow engine, and MCP is not an orchestrator.

## Use it

### Option A: Install as a Skill

If your agent supports the common `SKILL.md` convention, copy this repository's `SKILL.md` into the Skill location supported by your agent. Exact discovery and installation behavior vary by platform.

### Option B: No Skill installation

Copy [PROMPT.md](PROMPT.md) into your AI conversation, then paste the proposed Skill or describe your task.

**Example request:**

> Review this Skill. Is it necessary, or should I use code, a scheduled job, Workflow, MCP, or an Agent? Identify overlaps and recommend the simplest maintainable design.

## Review outcomes

`KEEP` · `SIMPLIFY` · `MERGE` · `REPLACE` · `REMOVE` · `INSUFFICIENT_EVIDENCE`

Every review should explain responsibilities, failure modes, migration concerns, and evidence gaps. No invented benchmarks or fake precision scores.

## Examples

See [examples/reviews.md](examples/reviews.md) for hypothetical scenarios (not production benchmarks).

## Design stance

- Code owns deterministic behavior.
- Workflows own state, coordination, retries, and recovery.
- MCP exposes controlled capabilities; it does not replace orchestration.
- Agents handle variable context and uncertain next steps.
- Skills provide reusable instructions and domain-specific judgment, when needed.
- Human review remains a valid outcome.

Even this reviewer may be better used as a plain prompt or checklist. Use the lightest form that works.

## Background

[HackMD: 每個功能都要做成 Skill 嗎？](https://hackmd.io/@jungkang/Hyq1eju3Gl)

## License

[MIT](LICENSE)
