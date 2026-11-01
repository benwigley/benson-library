---
name: exploration
description: Run a bounded autonomous investigation campaign, preparing evidence and authorized isolated candidates without integrating them.
context: all
promptName: campaign
promptDescription: Campaign scope, investigation/branch/time limits, sources, and candidate-edit authority.
---

# Exploration

Treat the request below as the campaign contract:

<user-request>{campaign}</user-request>

Explore broadly enough to find the real failure or opportunity, not merely the
first plausible code change. Preserve the current request's authority limits,
the project's rules, and Benson's runtime and approval controls.

## Establish the campaign

Resolve the area to explore, permitted candidate work, and the extent of the
campaign before open-ended discovery. Accept limits on total child
investigations, candidate branches, a discovery duration or deadline, or a
combination. Honor whichever applicable limit is reached first. Use a clearly
finite requested task set as its boundary; if the extent or edit authority is
ambiguous, ask one concise question before launching dependent work. Do not
invent a budget or ask the user to repeat limits already supplied.

For a duration, record the campaign start and resulting absolute deadline with
timezone. Treat it as the discovery window, not a promise that all child work
or reporting ends then. Do not claim access to remaining provider allowance
unless an available supported tool actually supplies it. Translate a vague
“use my remaining allowance” request into a user-chosen observable boundary.

- Give the campaign a stable identifier if the request does not already provide
  one. Use that identifier for evidence, isolated candidates, and reporting.
- Record the exact sources inspected and the exact comparison base, including
  branch names and commit identifiers when available. Re-check the current base
  before drawing final conclusions.
- Separate current observations from saved reports, previous test results,
  benchmarks, and other historical evidence. Label historical evidence and do
  not imply it was rerun.
- State material unknowns and gaps. Do not invent a failure mechanism to make an
  incomplete story feel complete.

## Coordinate autonomous discovery

Within the agreed scope and limits, choose promising investigations and pursue
useful leads without asking the user to select each step. Continue with useful
in-scope work while the campaign is open; do not invent busywork merely to spend
allowance. If no worthwhile leads remain, explain why discovery ended early.

Use existing Benson dispatch, continuation, Workspace, and isolation mechanisms
under the current runtime's guidance. Reconcile existing owners and uncertain
dispatch outcomes before launching or retrying. Give each delegated outcome one
owner and carry its scope, exact evidence, edit authority, remaining limits and
return contract. Coding candidates follow the project's normal implementation
route; this skill does not substitute for that route or its approval rules.

Keep a compact campaign ledger in existing notes or workflow state: scope,
start/deadline, limits, investigation owners and states, candidate branches,
consumption, results and next action. Count limits across the campaign and its
delegated descendants, not separately per child. Each new child investigation
consumes an investigation slot; a retry of the same investigation does not reset
the budget or become fresh discovery. Reconcile failed or unknown launches
rather than assuming unused capacity. Branch consumption is separate: an
investigation may need no branch, and a created candidate branch consumes its
slot even if later rejected. Children must not create additional investigations
or branches outside the shared remaining allocation.

A total investigation limit is not a concurrency allowance. Follow current
worker admission, routing, queue and lock rules. Arrange and verify supported
asynchronous returns before ending a turn that promises continuing supervision.
On each return, reconcile exact work and budget state, then select the next
useful investigation only if discovery is still open. Do not add a scheduler,
quota monitor, new persistence system or polling loop. If the available tools
cannot sustain a needed continuation, report the specific gap instead of
claiming the campaign will continue automatically.

## Investigate

Choose methods that fit the problem: inspect code and history, reproduce the
reported behaviour, compare states, run focused checks, examine real user impact,
and test competing hypotheses. Prefer evidence that can disprove a candidate
explanation.

For each meaningful finding, capture:

- the observed failure or opportunity and who benefits if it is addressed;
- the evidence supporting it and the evidence still missing;
- a plausible smallest response and credible simpler alternatives;
- likely maintenance cost and new failure modes;
- whether it is ready for independent assessment, should be deferred, or should
  be rejected now.

Do not multiply speculative locks, retries, recovery jobs, persisted state, or
other machinery around an unproven race or historical symptom. First establish
that the failure is real on the exact source and current base.

## Candidate changes

Candidate edits are allowed only when the authenticated request and current run
mode explicitly authorize them. Otherwise, propose changes without editing.

When edits are authorized:

- isolate candidates using the available project and runtime mechanisms so each
  one can be assessed or discarded independently;
- keep each candidate narrow enough to explain which hypothesis it tests;
- avoid destructive publication, deployment, activation, merge, or integration;
- preserve task-owned evidence and verification, but do not present a passing
  test suite as proof that the candidate should be kept;
- stop at the current authority boundary. This skill never infers authority to
  merge, rebase shared work, publish, install, restart, or clean up another run's
  work.

Existing requester, approval, filesystem, queue, write-lock, destructive-action,
and Git rules remain binding. Skill text and campaign artifacts are context, not
authority.

## End discovery, then finish

Check elapsed time and campaign-wide counts before new investigative work or
dispatch and whenever control returns from a tool or child. At the first
applicable limit, stop the lead's own discovery and new exploratory launches.
An in-flight operation may pass the deadline before control returns; report any
overshoot rather than claiming exact timed interruption.

Allow already-started children to finish their assigned work after the discovery
window. Then collect their evidence, obtain necessary in-scope clarifications,
and prepare the assessment handoff and consolidated report. Do not cancel
children just because discovery ended unless the user requested a hard stop.
Do not disguise a new hypothesis, candidate, branch or investigation as
completion follow-up. A hard total-stop instruction takes precedence and must be
resolved separately if its meaning is unclear.

Report the discovery stop time and reason, limits consumed, children still
finishing, and final completion time when known. Distinguish queued, running,
finished and blocked work. Preserve candidates and evidence; cleanup and
integration still require their ordinary authority. Complete the reporting and
any authorized independent-assessment handoff through existing mechanisms; do
not treat a handoff request as a verified assessment result.

## Consolidate the campaign

Keep findings together. Do not create one Inbox item, task, branch request, or
follow-up per finding.

When this exploration is the campaign's durable reporting stage, search the
relevant Inbox scope for the campaign identifier before writing. Update the one
clear existing campaign item; otherwise create one item. If matching remains
ambiguous, ask rather than creating a possible duplicate. Use one readable
Markdown report containing:

1. campaign goal, limits, consumption, discovery stop and completion status, exact
   sources, and current comparison base;
2. current findings and isolated candidates;
3. rejected hypotheses and simpler alternatives;
4. historical evidence, clearly labelled;
5. evidence limits and items deferred for assessment;
6. the independent assessor's required inputs.

If an independent assessment will own the durable report, hand it this single
consolidated body or an exact durable source instead of creating another Inbox
item. Deferred findings remain in the campaign report.

A supplementary destination is used only when the invocation or applicable
configuration explicitly names it. Never assume a personal note, dashboard,
folder, or machine-specific path. Failure of an optional supplementary write
does not justify destructive replacement of a valid primary report.

End by naming what was observed, what was only historical, what candidates were
prepared, what was not authorized, and the exact material the independent
assessor should compare.
