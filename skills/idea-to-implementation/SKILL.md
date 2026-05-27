---
name: idea-to-implementation
description: "Proactively run vague, underspecified, exploratory, or early-stage user ideas through a staged execution pipeline before building: grill-me interrogation, Trellis PRD/design/implementation planning, Codex plus ACE plus MCP implementation, and Trellis check/update-spec/finish-work closeout. Use when the user says they have an idea, gives an unclear product/feature/app/automation/project request, asks to turn an idea into a built artifact, asks to stress-test then execute a plan, or requests the grill-me to Trellis to agent workflow."
---

# Idea To Implementation

Use this skill to move an idea from rough intent to implemented work without skipping discovery, specification, execution, or closeout.

Load this skill proactively when the user asks for implementation but the actual goal, target user, scope, acceptance criteria, constraints, or success conditions are still vague. Treat ambiguity as a reason to enter Phase 0, not as a reason to guess and start coding.

The mandatory sequence is:

1. Phase 0: grill-me interrogates the idea.
2. Phase 1: Trellis turns the clarified idea into PRD, design, and implementation plan.
3. Phase 2: Codex, ACE, and MCP implement the plan.
4. Phase 3: Trellis checks the result, updates the spec, and finishes the work.

Do not implement before Phase 0 and Phase 1 have produced enough shared understanding to avoid building the wrong thing. If the user explicitly asks for a tiny throwaway change, compress the phases but keep the same order.

## Phase 0: grill-me

Invoke the `grill-me` skill when available. Ask one question at a time and be relentless about unclear decisions.

Resolve at least these branches before leaving Phase 0:

- User: target user, environment, constraints, existing workflow.
- Problem: pain, frequency, consequence of doing nothing.
- Outcome: measurable success, acceptance criteria, non-goals.
- Scope: must-have, should-have, intentionally deferred.
- Risks: security, privacy, data loss, cost, latency, maintainability.
- Interfaces: UI, CLI, API, automation, files, integrations.
- Execution constraints: deadline, repo/workspace, tech stack, deployment target.

End Phase 0 with a concise idea brief:

- Problem statement.
- Target user.
- Proposed solution.
- Success criteria.
- Non-goals.
- Open risks or assumptions.

If an answer can be discovered from the codebase or project files, inspect the codebase instead of asking the user.

## Phase 1: Trellis PRD / Design / Implement

Invoke `trellis-meta` when available and the project uses Trellis. If `.trellis/` is absent, ask before initializing Trellis or modifying project workflow files.

Create or update Trellis artifacts in this order:

1. PRD: user problem, goals, non-goals, personas, acceptance criteria, constraints.
2. Design: architecture, data model, interfaces, UX flows, dependencies, risks.
3. Implement plan: ordered tasks, owners/agents, test strategy, rollback plan.

Before moving to Phase 2, confirm that the implementation plan is concrete enough for an agent to execute. For ambiguous or high-impact work, summarize the plan and ask for approval. For low-risk work, proceed and clearly state the assumptions.

## Phase 2: Codex + ACE + MCP Implementation

Use Codex as the primary executor in the local workspace. Use ACE and MCP capabilities when they are available and relevant:

- Use MCP/app connectors for source-of-truth systems such as GitHub, issue trackers, docs, databases, browser automation, or project-specific services.
- Use ACE-style agents or subagents for independent analysis, parallel implementation, review, or validation only when the task benefits from separation of concerns.
- Keep implementation aligned with the Trellis plan; update the plan if discoveries invalidate it.

Implementation rules:

- Read the existing code and conventions before editing.
- Keep changes scoped to the accepted plan.
- Prefer existing project patterns over new abstractions.
- Add or update tests for changed behavior.
- Run the most relevant verification commands available in the repo.
- Record deviations from the plan, including why they were necessary.

If the environment does not expose ACE or a relevant MCP connector, continue with Codex and note the unavailable capability. Do not invent unavailable tools.

## Phase 3: Trellis Check / Update-Spec / Finish-Work

Return to Trellis for closeout.

Run or emulate these Trellis steps according to the local project setup:

1. check: verify implementation against acceptance criteria, tests, risks, and non-goals.
2. update-spec: update PRD/design/implementation notes for actual behavior and decisions.
3. finish-work: produce final status, changed files, tests run, unresolved risks, and follow-up tasks.

Do not mark work complete if acceptance criteria are unverified, tests could not run, or required artifacts are missing. State the exact remaining blocker instead.

## Output Shape

During the workflow, keep the user oriented with phase labels and short status updates.

For final responses, include:

- What was built or decided.
- Key files or artifacts changed.
- Verification performed.
- Remaining risks or follow-ups.

Keep the response concise unless the user asks for the full PRD, design, or implementation plan.
