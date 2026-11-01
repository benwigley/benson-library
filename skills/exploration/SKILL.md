---
name: exploration
description: Investigate a broad problem space and prepare evidence or isolated candidate changes without integrating them.
context: all
promptName: campaign
promptDescription: Campaign goal, scope, sources, and permitted candidate work.
---

# Exploration

Treat the request below as the campaign contract:

<user-request>{campaign}</user-request>

Explore broadly enough to find the real failure or opportunity, not merely the
first plausible code change. Preserve the current request's authority limits,
the project's rules, and Benson's runtime and approval controls.

## Establish the campaign

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

## Consolidate the campaign

Keep findings together. Do not create one Inbox item, task, branch request, or
follow-up per finding.

When this exploration is the campaign's durable reporting stage, search the
relevant Inbox scope for the campaign identifier before writing. Update the one
clear existing campaign item; otherwise create one item. If matching remains
ambiguous, ask rather than creating a possible duplicate. Use one readable
Markdown report containing:

1. campaign goal, exact sources, and current comparison base;
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
