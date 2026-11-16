# Check whether findings deserve action

Give a fresh child Session or Workspace a bounded verification assignment using
Benson's existing dispatch and return tools. It must not be the original finder
checking its own work. Resolve runtime and placement through current delegation
guidance. Do not hardcode a provider, model or claim that switching models alone
proves independence. Keep the parent responsible for final synthesis.

Pass the exact source, candidate reports and evidence, the user goal and scope,
permitted checks and remaining limits. Ask for an independent verdict, not
confirmation of the proposed fix. Preserve the original reports as evidence.

For each important finding:

- Trace the actual path in the current code. Look for safeguards elsewhere,
  unreachable paths, existing equivalent fixes and inappropriate assumptions.
- Reproduce or run focused checks where feasible. For performance, inspect the
  dataset, query frequency and measurement conditions. Do not claim a rerun when
  only historical output was read.
- Explain whether a real user or operational problem exists. Distinguish a
  measured failure from an architectural preference or a future scaling risk.
- Compare the suggested response with a smaller fix, existing tools, or no change.
  Include ongoing maintenance cost and possible regressions.
- Return confirmed, needs more evidence, or rejected, with reasons and sources.
  Separately recommend fix now, defer, or no change. A real defect may still be
  low priority; a suspected serious issue must remain visible as uncertain.

Disagreement is not decided by a vote. The parent compares evidence and keeps
unresolved uncertainty explicit. Do not repeat reviews until one agrees with the
finder. Missing verifier access means independent verification is incomplete;
report that limitation rather than silently treating the finding as verified.
The verifier reports only and does not implement or create follow-up tasks.
