---
name: codebase-audit
title: Find worthwhile code improvements
description: Investigate a codebase through focused child audits, verify findings, and report worthwhile improvements before the user chooses what to fix.
context: coding
promptName: audit
promptDescription: Project, areas to check, investigation limits, and available evidence.
---

# Find worthwhile code improvements

Use the user's request as the audit brief:

<user-request>{audit}</user-request>

Find improvements that matter to users or reduce operating cost. Coordinate
focused investigations and return one checked report. This skill stands alone;
it does not invoke other audit, exploration, assessment or implementation skills.

## Agree what to check

Identify the project, requested areas and important user actions. Inspect the
project's own instructions and existing work before choosing checks. For a broad
audit, select applicable checks from [the topic guides](references/checks.md)
and explain the selection briefly. For a narrow request, keep that scope.

Use the selected, finite topic list as the stopping point. Honour any supplied
time or investigation limits across the whole audit, including descendants.
If the user asks to spend remaining credits without a usable limit, ask for an
observable boundary; do not claim to know their remaining allowance. Stop early
if no worthwhile work remains. Do not add more investigations merely to spend.

Record the working directory, branch and commit, plus relevant uncommitted
changes, without changing them. Name the environment and evidence sources.
Recheck relevant source changes before final conclusions; revalidate affected
findings or mark them as stale. A commit alone does not identify a dirty tree.

The audit investigates and reports. Do not implement fixes, alter application
or database configuration, install dependencies, deploy, or start remediation.
Respect the current mode: CHAT children inspect and return reports through their
stored output. Checks that need to write fixtures or benchmark artifacts require
scoped EDIT authority and suitable isolation; otherwise report that limit.

## Give each check an owner

Keep this Workspace as the parent. Create an agent-managed child Workspace for
each selected topic using Benson's available dispatch tools. Follow the current
delegation guidance for placement, requester provenance, runtime selection,
branch/checkout verification, and queue rules. Workspaces do not guarantee
parallel execution. Do not bypass locks or switch the shared checkout.

Read [the investigation and report contract](references/reports.md). Each child
receives that contract, only its relevant topic section, the exact target and
scope, evidence sources, permitted checks, limits and return expectations. Give
it enough context to work without reconstructing this conversation. Children
must not launch further children or expand the selected checks on their own.

Keep a compact ledger in the parent's saved notes or output: topic, child
Workspace/Session, source job or dispatch, return wait, state and report reference.
Use queued, running, complete, blocked, incomplete or not applicable accurately.
Do not create a separate database, scheduler or polling script for this ledger.

Arrange supported asynchronous returns for the parent's collection and review
role, normally the dispatch's bundled return. Keep exactly one continuation per
dispatch; do not add another wait for the same outcome. Return control while
children work rather than waiting synchronously inside a Benson job.

On return, inspect the exact child outcome and full report, not just its summary.
A completed job or an existing report does not prove the check was completed.
Reconcile failed or uncertain dispatches before retrying; follow current runtime
recovery rules. Mark unavailable checks honestly and continue independent checks
when useful. If dispatch or continuations are unavailable, explain the gap and
do not silently claim a multi-agent audit or automatic continuation.

## Check the findings

Collect topic reports before synthesis. Follow [verification guidance](references/verification.md)
to give important findings a fresh independent check. Select findings by impact
and uncertainty, not by a quota. Verification is part of the audit's finite plan,
not permission to open new topic investigations indefinitely.

Keep verified problems, unconfirmed leads and rejected claims distinct. Remove
duplicates by underlying problem, retaining all useful evidence and affected
paths. Judge both whether a problem is real and whether a proposed fix is worth
its effort and ongoing maintenance. Finding nothing worth changing is success.

## Bring the user one report

Use the final report structure in [reports.md](references/reports.md). Rank the
most worthwhile fixes, keep supporting evidence available, and disclose all
blocked or unfinished checks. Do not average topic scores into a claim that the
whole product is safe or production-ready.

Deliver the report in the parent Workspace using stored reports and useful child
links. Save a supplementary file only when requested or required by the project;
identify the actual destination and respect its write permissions. Do not create
one Inbox item or implementation task per finding. No personal-note or Inbox
write is implied by an audit request.

Before declaring completion, reconcile all selected checks and owned returns.
If work remains, name it and say whether continuation is actually arranged.
Do not close children before their evidence has been collected; use ordinary
closure rules afterwards. Present the recommended next choices to the user.
Do not start fixes merely because the report recommends them.
