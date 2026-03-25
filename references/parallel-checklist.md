# Parallel Checklist

Use this checklist before approving parallel execution. If any critical item fails, do the work sequentially.

## Quick Gate

Approve parallelism only if all answers are `yes`:

1. Is each workstream independently valuable?
2. Is ownership explicit for every workstream?
3. Are file and module boundaries non-overlapping?
4. Are dependencies between workstreams known and ordered?
5. Does each workstream have its own acceptance criteria?
6. Can each workstream be verified without waiting on unrelated work?
7. Will coordination cost stay lower than the time saved?

If any answer is `no`, reject parallelism or shrink the split.

## Workstream Template

Define this contract for every stream:

- `name`
- `scope`
- `owned_files`
- `dependencies`
- `expected_output`
- `acceptance`
- `non_goals`
- `blockers`

Do not allow shared ownership. Do not allow vague outputs.

## Red Flags

Do not parallelize when you see any of these:

- shared state with unclear write order,
- overlapping files or modules,
- one stream designing abstractions that others depend on,
- acceptance that depends on merged behavior rather than local outcomes,
- uncertain root cause,
- broad refactors without a stable target design,
- streams that mostly produce review comments instead of concrete outputs.

## Good Split Patterns

Prefer splits like:

- backend API vs frontend integration, when contract is stable,
- independent modules with separate tests,
- migration prep vs migration execution, when interfaces are fixed,
- refactor by non-overlapping package boundaries.

## Bad Split Patterns

Avoid splits like:

- multiple agents editing the same service,
- parallelizing before the target architecture is chosen,
- one agent exploring while another implements against moving assumptions,
- dividing by "easy" vs "hard" tasks instead of system boundaries.

## Verification Order

1. Verify each stream locally.
2. Verify dependency order assumptions.
3. Integrate in the smallest valid sequence.
4. Run regression checks on the combined path.

## Refusal Language

When parallelism is not justified, say it directly:

> Parallel execution is rejected because the current split increases coordination cost or coupling. I will keep planning globally, then execute sequentially on the critical path.
