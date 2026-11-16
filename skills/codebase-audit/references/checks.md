# Checks to choose from

Read only the sections relevant to the user's request. These are investigation
prompts, not a demand to find defects or install every listed practice. Apply
the shared reporting contract to each selected check.

## Database speed

Question: which database operations slow important user actions or waste resources?

Trace important actions to their queries. Look for queries repeated inside loops,
excessive data reads, missing limits, expensive joins/filtering/sorting, long
transactions and connection pressure. Inspect existing indexes and the actual
query shape before proposing an index. Account for tenant filters and realistic
data sizes; a small development dataset can hide problems.

Use available timings, query counts, slow-query records and execution plans in
a suitable environment. Query execution for measurement can be costly or have
side effects; inspect the target and statement first and use an authorized test
environment for execution-based analysis. Do not change indexes, data or settings.

Tie findings to the affected action, workload and evidence. Separate measured
slowness from suspicious code. Suggest the smallest useful response and a
repeatable before/after check under comparable conditions. Explain possible
write/storage costs of an index or correctness costs of caching.

## Page speed

Question: where do users wait unnecessarily?

Choose important journeys and inspect loading, API waterfalls, transferred assets,
repeated requests, rendering work and cache behaviour. Measure with available
browser/profiling tools at relevant device sizes and realistic data. State device,
network and cold/warm conditions; distinguish laboratory results from real-user
data. Locate the cause before suggesting caching, splitting or a rewrite.
Report what would become faster and how to compare it later. If browser access
is unavailable, identify code-level leads without claiming measured page speed.

## Permissions and security

Question: can someone read or change something they should not?

Trace server-side access checks for representative roles, ownership boundaries,
share links and sensitive actions. Inspect input handling, uploads and webhook
validation where applicable. Check upstream protections before reporting a missing
local guard. Inspect declared dependencies using available evidence; do not
install scanners or silently expand into a live penetration test.

Use permitted local/test reproductions. Avoid exposing secrets or personal data,
changing real accounts or contacting third parties. Explain the exact boundary,
affected action and evidence; keep untested risks visible without presenting them
as demonstrated access. Do not reproduce secret values in the report.

## Failure recovery and repeated actions

Question: does work get lost, duplicated or stuck when something fails?

Trace dependency timeouts, interrupted jobs, retries, cancellation, repeated
submissions and duplicate webhook delivery. Inspect multi-step writes and how
concurrent workers avoid processing the same work twice. Reproduce controlled
failures only within the permitted environment; do not interrupt live services.

Establish the broken state transition and user consequence before recommending
retries, locks or new recovery processes. Existing database constraints or queue
semantics may already provide the protection. Report the smallest response and
how a test could prove no lost or duplicated effect.

## Useful tests

Question: which important failures would the current tests miss?

Map critical behaviour and known failure paths to actual assertions. Check
integration boundaries, error cases, mocks and whether tests can fail when the
behaviour breaks. Use focused existing checks within the assigned permissions.
Distinguish test, environment and product failures. Coverage percentages alone
are not proof of useful protection.

Propose tests tied to concrete failure scenarios, stating what broken behaviour
they would detect. Explain misleading or redundant tests only with evidence.
Do not write tests or run mutation tools that alter shared files in this audit.

## Resources and running costs

Question: where does the product waste money or accumulate resources?

Inspect repeated external/AI calls, token usage, storage growth, unbounded caches,
background polling, unused work and unclosed connections/listeners. Look for
limits, expiry and cleanup already provided elsewhere. Use available usage and
billing data only within authorized access; missing cost data is an evidence gap.

Separate measured spend from estimates and disclose estimate assumptions.
Explain tradeoffs: caching may serve stale data; smaller models may reduce
quality. Suggest the smallest saving that preserves required behaviour. Do not
change plans, providers, subscriptions or running infrastructure.

## Ease of use and accessibility

Question: what prevents people from completing common tasks?

Walk representative journeys at relevant screen sizes. Check keyboard use,
focus, accessible labels, readable feedback, loading/empty/error states and
whether forms preserve input. Inspect shared components before reporting the
same problem on every page. Use available browser or accessibility tools and
identify which checks require human judgement.

Report a reproducible difficulty, affected users and a concrete small response.
Keep preferences separate from task failures. Do not claim comprehensive
accessibility compliance from automated scans or code inspection alone.

## Accurate documentation

Question: can people follow the instructions and trust the product description?

Compare setup/use instructions and public feature claims with the current code.
Follow safe, authorized steps where feasible; distinguish steps actually run
from instructions only inspected. Check prerequisites, command names, examples,
important missing steps and outdated behaviour.

Do not execute destructive, deployment, install or external-account operations
merely because documentation says to. Report the exact misleading instruction,
what actually happens, who it affects and the smallest correction. Unavailable
credentials or environments limit verification; they do not prove the guide wrong.
