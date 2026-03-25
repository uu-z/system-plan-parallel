# Examples

Use these examples to stabilize triggering and output shape. Adapt them to the current repo and constraints instead of copying them mechanically.

## Trigger Examples

- "Use `$system-plan-parallel` to plan this feature before coding."
- "先整体分析，不要直接写代码，先给我整体方案。"
- "Break this repo-wide refactor into safe parallel workstreams."
- "I want a phased plan first, then bounded parallel execution."
- "先做系统分析，再拆成 2-4 个可并行 workstreams。"

## Output Examples

### Example 1: Broad feature request

**Request**

> Add role-based access control across the admin area.

**Expected response shape**

- `Scorecard (L0-L3)`: L0/L1/L2/L3 with key scores and pass/fail.
- `Goal`: secure admin actions with the smallest viable access model.
- `Constraints`: existing auth model, current routes, rollback requirements, no broad rewrite.
- `Big Picture`: one policy boundary, one enforcement point, one audit path.
- `Plan (Phased)`: map roles, protect critical paths first, add checks at one boundary, verify with focused tests.
- `Execution Plan (Workstreams)`: split UI/backend only if file ownership and acceptance are independent.
- `Parallelization`: only split UI and backend if file ownership and acceptance are independent.
- `Risks`: hidden authorization paths, inconsistent permission checks, migration gaps.
- `Acceptance`: unauthorized paths blocked, authorized paths preserved, regression checks pass.

### Example 2: Repo-wide cleanup

**Request**

> Clean up duplicated validation logic across the codebase.

**Expected response shape**

- `Scorecard (L0-L3)`: L0/L1/L2/L3 with key scores and pass/fail.
- `Goal`: reduce duplication and inconsistent validation behavior.
- `Constraints`: no behavior regressions, minimal new abstraction, easy rollback.
- `Big Picture`: one canonical validation path used across the system.
- `Plan (Phased)`: inventory duplicates, identify one canonical path, migrate highest-leverage sites first, remove dead branches.
- `Execution Plan (Workstreams)`: split only by non-overlapping modules with independent acceptance.
- `Parallelization`: split only by non-overlapping modules with independent acceptance.
- `Risks`: hidden coupling, slightly different semantics, test gaps.
- `Acceptance`: one canonical validation path used in target modules, old duplicates removed, focused regression coverage added.

### Example 3: Parallel execution gate

**Request**

> Split this migration across multiple agents and move fast.

**Expected response shape**

- First decide if parallelism is justified.
- Refuse parallelism if modules overlap, shared state is unclear, or integration order is unstable.
- If parallelism is allowed, define for each stream:
  - `scope`
  - `owned_files`
  - `dependencies`
  - `expected_output`
  - `acceptance`
  - `non_goals`
  - `blockers`

## Anti-Example

Do not respond like this:

> "Here are 8 ideas. We can probably do all of them in parallel."

Why this is wrong:

- no scored decision,
- no critical path,
- no boundary check,
- no acceptance criteria,
- no rollback clarity.
