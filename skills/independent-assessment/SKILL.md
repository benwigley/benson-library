---
name: independent-assessment
description: Independently judge explored changes against real failures, user benefit, evidence, alternatives, and ongoing cost.
context: all
promptName: campaign
promptDescription: Campaign identifier, sources, candidates, and exact current base.
---

# Independent Assessment

Treat the request below as the assessment contract:

<user-request>{campaign}</user-request>

Judge whether the explored work deserves to survive. Independence means this
assessment must not inherit the explorer's intended answer: inspect the supplied
artifacts and the current system directly, challenge the stated conclusions,
and remain willing to keep nothing.

This skill is assessment, not integration. It never grants authority to edit a
candidate, merge, rebase shared work, publish, deploy, activate, restart, install,
or perform destructive cleanup. Existing requester, approval, runtime,
filesystem, queue, write-lock, destructive-action, and Git rules remain binding.

## Fix the comparison

- Identify the exact campaign, source branches or commits, report versions, and
  comparison base. Record commit identifiers when available.
- Refresh the current base before assessment. If the base moved, distinguish the
  historical candidate result from evidence verified on the refreshed base.
- Label saved test results, benchmarks, reports, and reproductions as historical
  unless they were rerun during this assessment.
- Treat explorer claims as leads, not facts. Report missing artifacts, ambiguous
  provenance, and evidence that cannot be reproduced.

## Assess each candidate

Reach one outcome: **keep**, **simplify**, **defer**, or **reject**. Judge the
candidate on all of these questions:

- Does a real failure or opportunity exist on the exact source and current base?
- Is there meaningful user benefit, and is the proposed behaviour the right
  outcome for the affected user?
- What correctness evidence exists beyond tests passing? Consider invariants,
  state transitions, failure handling, realistic data, and relevant boundaries.
- Is there a smaller response, an existing mechanism, or no change that achieves
  the same outcome more safely?
- What maintenance, operational, cognitive, and performance cost would remain?
- Which new failure modes, recovery obligations, or coupling would it introduce?

Tests are evidence about observed behaviour, not a reason to keep code. A
technically correct candidate may still be rejected because the failure is not
real, the benefit is weak, the design is too costly, or a simpler alternative is
better. Keeping nothing is a valid successful assessment.

Do not recommend speculative recovery state, background jobs, locks, retries,
or broad architecture changes for a race or symptom that has not been
reproduced. Defer uncertain cases with a bounded way to obtain the missing
evidence.

## Report one campaign outcome

Produce one readable consolidated Markdown report for the campaign. Search the
relevant Inbox scope using the stable campaign identifier before writing. Update
the one clear existing item; otherwise create one item. If matches are ambiguous,
ask rather than creating a duplicate. Never fan findings out into separate Inbox
items or tasks; keep deferred findings in the same report.

Prefer this report shape:

```markdown
# <campaign> independent assessment

Sources: <exact candidates and reports>
Current base: <branch and commit>

## Outcome
<What, if anything, is worth retaining and why.>

## Keep or simplify
- <candidate, decision, user benefit, correctness evidence, and smallest form>

## Defer or reject
- <candidate, decision, evidence gap or cost, and bounded next evidence if any>

## Evidence limits
<What was current, what was historical, and what was not rerun.>

## Next decision
<Any separate authority or product decision required before implementation or integration.>
```

Omit empty sections rather than manufacturing findings. Keep evidence close to
the decision it supports. State clearly that the report is assessment evidence,
not implementation, integration, merge, or release authority.

A supplementary destination is used only when the invocation or applicable
configuration explicitly names it. Never hardcode a personal note, dashboard,
folder, or machine-specific path. Do not destructively replace a valid report to
force publication elsewhere.

End with the decisions, verification performed during this assessment, evidence
that remains historical, and any exact user decision required next.
