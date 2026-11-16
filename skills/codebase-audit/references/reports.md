# Investigation and report contract

## What each investigator returns

Name the assigned question, source revision and relevant dirty files, environment,
checks performed and checks not performed. Return a report even when there are
no findings or the topic does not apply. Explain the reason rather than calling
an unavailable check a pass. Stored child output is a valid report artifact.

For each candidate finding, include:

- A stable topic-local identifier and a plain-English description.
- The affected user action or operating cost, and when the problem occurs.
- Exact code locations and symbols, or a reproducible interface location.
- Supporting evidence: observations, commands/results, measurements or a traced
  code path. Redact secrets and personal data. Label historical evidence.
- Evidence that might disprove the claim, including existing safeguards checked.
- Whether it is confirmed, suspected, or blocked on missing evidence. A located
  suspicion stays a lead; do not inflate it into a confirmed defect.
- The smallest useful response, simpler alternatives and likely effort/risk.
- How a later fix would be checked, including before/after measurements when useful.

Do not invent benchmarks, savings, severity, or user impact. A missing pattern
is not automatically a defect: explain why it is needed in this product. Prefer
clear findings to a long list. Do not limit reporting of serious confirmed issues
to meet a shortlist quota. Include meaningful rejected hypotheses and limits.

Investigate only. Report unrelated leads to the parent rather than opening new
work, adding tasks or fixing them.

## What the parent delivers

Open with what was checked and what, if anything, is worth changing.
Then provide:

1. **Recommended fixes:** a short ranked list explaining user benefit or cost
   reduction, evidence strength, likely effort, risk and the smallest response.
2. **Supporting findings:** detail and source references for the recommendations.
3. **Uncertain or rejected findings:** what was not established or not worth doing,
   why, and the bounded next check if one would help.
4. **Coverage and limits:** each selected topic's outcome, unavailable tools/data,
   failed checks, source drift and unfinished work. Distinguish job execution
   failure from a product problem.
5. **Next choice:** what the user can choose to fix or investigate further.

Keep confirmed problems separate from opportunities and unmeasured hypotheses.
Rank by benefit, urgency, effort and maintenance cost, not by how easy a change
is for an agent to write. Cite full child reports with usable references. A
single-topic audit still uses this shape, shortened to fit. Omit empty sections.
