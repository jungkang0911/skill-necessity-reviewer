# Hypothetical review examples

These are illustrative architecture exercises, **not measured production results**.

## Example 1 — Daily order import Skill

**Proposal:** Every morning, fetch orders, validate required fields, and write to a database; retry failed operations.

**Verdict:** REPLACE.

**Reasoning:** The trigger, steps, and validation are deterministic. Use a scheduler, workflow/task state, and code-level validation. Use idempotency keys or equivalent database safeguards to prevent duplicate writes. No Skill or Agent is necessary unless a separate ambiguous decision is introduced.

## Example 2 — Product candidate matching

**Proposal:** Match incomplete product descriptions against multiple candidates; fetch additional context when evidence is insufficient.

**Verdict:** KEEP or SIMPLIFY, depending on existing instructions.

**Reasoning:** An Agent may need to choose what evidence to retrieve. A Skill can encode domain-specific matching criteria, including MATCH / UNCERTAIN / NO_MATCH. MCP or APIs can expose candidate data. A validator should enforce deterministic constraints, and uncertain cases may need human review.

## Example 3 — API wrapper Skill

**Proposal:** A Skill containing endpoint descriptions and a fixed API call sequence.

**Verdict:** SIMPLIFY or REMOVE.

**Reasoning:** Put the callable capability in an API or MCP tool. Keep a Skill only if meaningful domain-specific decision guidance remains. If it is merely API documentation duplicated elsewhere, remove it.

## Example 4 — This reviewer

**Proposal:** Automatically load Skill Necessity Reviewer for every AI interaction.

**Verdict:** SIMPLIFY.

**Reasoning:** Load only for architecture review. A plain prompt or checklist may be sufficient for occasional reviews. Do not add runtime overhead without a demonstrated need.
