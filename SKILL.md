---
name: system-plan-parallel
description: Force Codex to think at the system level before implementation, produce an overall plan, and parallelize only across independent workstreams. Use when the user asks for holistic thinking, overall planning, architecture-first execution, phased delivery, repo-wide changes, parallel implementation, multi-agent coordination, or complex tasks with multiple dependent parts. Also trigger for Chinese requests such as 整体思考, 整体规划, 系统分析, 并行实施, 先别写代码先规划, 先出方案再执行, 拆成 workstreams 并行推进.
---

# System Plan Parallel

## Overview

Use this skill to force a full-pass approach: define the problem, build the system view, plan the work, split only safe parallel streams, then verify before claiming completion.

## Output Contract

Always respond in this order:

- Goal
- Constraints
- Plan
- Parallelization
- Risks
- Acceptance

Keep each section minimal, decision-oriented, and free of filler.

## Workflow

1. Define `goal`, `constraints`, `acceptance`, and `non-goals`.
2. Build the system view: modules, dependencies, critical path, coupling points, and deletion opportunities.
3. Produce the overall plan before editing code.
4. Score candidate approaches and choose the lowest-complexity, highest-leverage option.
5. Split into `2-4` workstreams only if the split reduces total coordination cost.
6. Execute in batches, not scattered one-off edits.
7. Integrate, verify, and summarize remaining risks.

## Planning Rules

- Prefer deleting complexity over adding features.
- Solve root causes before local patches.
- Prefer standard library, existing patterns, and type constraints.
- Reject premature abstraction unless it removes current complexity.
- Create a plan before coding for any non-trivial task.
- Reduce scope first when requirements expand or remain unclear.

## Parallelization Gate

Parallelize only if all conditions are true:

- workstreams are low-coupling,
- ownership is explicit,
- files or modules do not overlap,
- each stream has independent acceptance,
- integration order is clear.

Do not parallelize if any condition fails.

## Delegation Contract

Define these fields for each workstream:

- `scope`
- `owned_files`
- `expected_output`
- `acceptance`
- `non_goals`
- `blockers`

Do not duplicate exploration across workstreams. Do not assign shared ownership.

## Anti-Patterns

- Do not jump into code before the system view and plan exist.
- Do not parallelize overlapping files, shared state, or unclear ownership.
- Do not add new abstractions, branches, or concepts unless they reduce total complexity now.
- Do not optimize for local speed if it increases integration or rollback cost.

## Refusal Rules

Refuse the faster-looking path when it causes:

- scope sprawl,
- duplicated work,
- hidden coupling,
- weak acceptance,
- unverifiable completion.

## Scoring

Score each candidate plan from `0-10` on:

- `complexity_reduction`
- `leverage`
- `rollback_safety`
- `parallel_independence`
- `verification_clarity`

Do not choose a plan with obvious structural risk just because it appears faster.

## Verification Order

1. Run workstream self-checks.
2. Run integration checks.
3. Run regression checks.
4. Report unresolved risks and next constraints.

Do not claim completion before verification.
