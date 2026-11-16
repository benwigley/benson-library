# Benson Library

Portable skills and workflows for Benson.

## Choose a tool

| Tool | Use it to |
| --- | --- |
| [Codebase Improvement Audit](skills/codebase-audit/SKILL.md) — skill | Check eight defined areas, verify findings, and report worthwhile fixes before choosing implementation. |
| [Discover and Evaluate Codebase Improvements](workflows/discover-codebase-improvements.yaml) — workflow | Explore promising ideas, prepare isolated trial changes when permitted, then independently judge what is worth keeping. |

Choose the audit for structured checks. Choose the workflow for broader discovery
and experiments. Both can conclude that nothing is worth changing. Neither
adopts, merges or deploys proposed changes automatically.

## Install the audit skill

These commands are for a deliberate future installation; they have not been run
by this repository. Inspect the destination and `/skills list` first. Stop if a
same-named definition already exists; do not overwrite it.

For all projects:

```sh
mkdir -p ~/.benson/skills
cp -R skills/codebase-audit ~/.benson/skills/codebase-audit
```

For one project, run from that project's directory, using the actual library
checkout path in place of `<library>`:

```sh
mkdir -p .benson/skills
cp -R <library>/skills/codebase-audit .benson/skills/codebase-audit
```

Copy the entire skill folder, including references. Then run `/skills reload`;
follow any reported `/commands sync-discord` requirement. The readable title
requires a Benson version with skill-title support. The command remains
`codebase-audit`.

Example after installation:

```text
/skill run name:codebase-audit prompt:"Check database speed and failure recovery in this project. Investigate only those two topics, verify important findings, and bring me one report. Do not implement fixes."
```

## Install the discovery workflow

The identifier is `discover-codebase-improvements`. It is a self-contained YAML
workflow using Benson's compact workflow schema, workflow-bound child dispatch
and asynchronous returns, including dispatch continuation renewal. Use a Benson
version supporting those capabilities. No separate skills, custom policies,
third-party services or orchestration scripts are required.

Inspect `/workflow list` and the destination before copying. Refuse an existing
same-named file rather than replacing a custom workflow. For all projects:

```sh
mkdir -p ~/.benson/workflows
cp workflows/discover-codebase-improvements.yaml ~/.benson/workflows/discover-codebase-improvements.yaml
```

For one project, run from that project's directory with the actual library path:

```sh
mkdir -p .benson/workflows
cp <library>/workflows/discover-codebase-improvements.yaml .benson/workflows/discover-codebase-improvements.yaml
```

Use `/workflow list` and `/workflow show` to verify that Benson sees the definition
and its expected name/version. Follow the running Benson version's command-sync
instructions if its Discord choices need refreshing. Cloning or copying this
library does not start a workflow or authorise application changes.

Example after installation:

```text
/workflow start name:discover-codebase-improvements prompt:"Find worthwhile improvements in this project. Explore for two hours, with at most six child investigations and three trial branches. You may prepare isolated trial changes, but do not merge or deploy them. Have a fresh agent assess the results and bring me one report."
```

The discovery window limits new exploration. Started children and independent
assessment may finish afterwards. The workflow asks if limits or edit permission
are unclear; it does not know remaining provider quota. Trial code work follows
the target project's normal implementation and Git rules. Evidence-only runs
are also supported by specifying that trial edits are not permitted.

The parent keeps progress and one report at the declared workflow output:
`.benson/workflow-runs/discover-codebase-improvements-<runId>.md` in the target
project. The report records candidates, evidence, keep/simplify/defer/reject
recommendations and unresolved checks. The user chooses adoption separately.

## Existing exploration and assessment users

The discovery workflow replaces this library's former `exploration` and
`independent-assessment` skills. Their investigation and assessment instructions
now live together in the workflow. Earlier versions remain in Git history.

This repository change does not remove installed copies, alter scheduled skills,
retarget shortcuts or change running work. Let existing work finish under its
captured instructions. Before deliberately retiring an installed copy, inspect
its local customisations, schedules and pins and use the current Benson management
routes. Do not overwrite or delete it merely to install the new workflow.

## Verification status

Definition parsing and output-path checks validate compatibility, not the quality
of an agent's decisions. A full live multi-agent discovery run has not yet been
trialled. The audit skill likewise has format/reference validation but no full
live audit trial. Report practical limits honestly when using either tool.
