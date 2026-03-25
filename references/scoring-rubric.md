# Scoring Rubric

Use this rubric to make the six scores more consistent. Score fast, but do not score loosely.

## Scale

Use this interpretation unless a dimension says otherwise:

- `0-2`: very weak
- `3-4`: weak
- `5-6`: acceptable but not strong
- `7-8`: strong
- `9-10`: exceptional

For `complexity` and `risk`, higher is worse.

## L0-L3 Scorecards

Use the same dimensions below, plus two readiness dimensions, to drive all levels:

- **L0 (Strategy Fit)**: decide whether to do the work at all.
- **L1 (Plan Quality)**: decide whether the plan is acceptable.
- **L2 (Execution Readiness)**: decide whether workstreams are ready to run.
- **L3 (Verification Readiness)**: decide whether validation is sufficient.

Minimum thresholds:

- L0: `value >= 7`, `leverage >= 6`, `unification >= 6`, `complexity <= 6`, `risk <= 6`.
- L1: `verifiability >= 7`, `complexity <= 6`, `risk <= 6`, `unification >= 6`.
- L2: `execution_readiness >= 7`, `dependencies <= 6`, `risk <= 6`.
- L3: `verification_strength >= 7`, `risk <= 6`.

If any level fails, adjust scope or plan until it passes.

## Value

- `0-2`: mostly cosmetic, low effect on the real problem.
- `3-4`: useful, but not tied to the main closure path.
- `5-6`: meaningful improvement, but not decisive.
- `7-8`: directly improves the main goal or removes a recurring problem.
- `9-10`: closes a critical loop or removes a systemic blocker.

Ask: does this materially help the main objective, or is it side work?

## Leverage

- `0-2`: one-off work with little reuse.
- `3-4`: helps a narrow area only.
- `5-6`: helps multiple nearby cases.
- `7-8`: one change benefits several modules, paths, or future tasks.
- `9-10`: removes repeated work at the system level.

Ask: will this reduce future manual effort, repeated fixes, or coordination?

## Complexity

- `0-2`: tiny change, obvious behavior, trivial rollback.
- `3-4`: small and understandable, limited moving parts.
- `5-6`: moderate change with some coordination or design cost.
- `7-8`: many moving parts, high understanding or maintenance burden.
- `9-10`: deep coupling, broad surface area, or hard rollback.

Ask: how much cost does this add to implementation, comprehension, maintenance, communication, and rollback?

## Risk

- `0-2`: highly contained, low blast radius, easy recovery.
- `3-4`: limited failure modes, low coupling.
- `5-6`: meaningful side-effect risk, but manageable.
- `7-8`: high uncertainty, broad impact, or difficult recovery.
- `9-10`: unacceptable blast radius, irreversible consequences, or hidden coupling.

Ask: if this is wrong, how expensive is the mistake?

## Verifiability

- `0-2`: unclear success condition, hard to observe.
- `3-4`: can be checked, but slowly or indirectly.
- `5-6`: moderate confidence with some manual effort.
- `7-8`: quick local and integration checks are clear.
- `9-10`: fast, direct, repeatable validation with strong signals.

Ask: can success and failure be proven quickly?

## Unification

- `0-2`: adds branches, exceptions, or new concepts.
- `3-4`: mostly local improvement, little systemic cleanup.
- `5-6`: some reduction in duplication or inconsistency.
- `7-8`: meaningfully reduces divergence across the system.
- `9-10`: creates one clear path and removes multiple branches or special cases.

Ask: does this make the system more uniform, or does it create more variance?

## Execution Readiness

- `0-2`: no clear scope, ownership, or acceptance.
- `3-4`: partial scope, missing dependencies or blockers.
- `5-6`: workstreams defined but gaps remain.
- `7-8`: clear scope, ownership, dependencies, and acceptance.
- `9-10`: fully specified workstreams with low coordination risk.

Ask: can the work be started immediately without hidden blockers?

## Verification Strength

- `0-2`: no clear validation path.
- `3-4`: weak or indirect validation.
- `5-6`: partial tests or manual checks.
- `7-8`: clear local + integration validation.
- `9-10`: fast, repeatable, high-signal validation with rollback confidence.

Ask: can success/failure be proven quickly and safely?

## Fast Decision Heuristic

Prefer options that are:

- `value >= 7`
- `leverage >= 6`
- `verifiability >= 7`
- `unification >= 6`
- `complexity <= 6`
- `risk <= 6`

If an option fails more than two thresholds, do not pick it without an explicit reason.

## Tie-Breakers

When two options look close, prefer:

1. lower `complexity`
2. lower `risk`
3. higher `unification`
4. higher `verifiability`
5. higher `leverage`

Do not let minor speed gains beat structural simplicity.
