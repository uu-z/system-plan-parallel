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
