# Benson Library

Portable skills and workflows for Benson.

## Skills

| Skill | Use it to |
| --- | --- |
| [`codebase-audit`](skills/codebase-audit/SKILL.md) — **Find worthwhile code improvements** | Send focused checks to separate agents, verify the findings, and return one report before choosing fixes. |
| [`exploration`](skills/exploration/SKILL.md) | Investigate a broad problem space, test hypotheses, and, when the current run is explicitly authorized to edit, prepare isolated candidate changes without integrating them. |
| [`independent-assessment`](skills/independent-assessment/SKILL.md) | Independently decide which explored candidates are worth keeping, simplifying, deferring, or rejecting against an exact current base. |

`codebase-audit` stands alone and does not depend on the other skills.
It checks database speed, page speed, permissions/security, failure recovery,
tests, running costs, ease of use/accessibility and documentation accuracy.
The parent reports what was checked, what remains uncertain and which fixes
are worth doing. It does not implement them.

The exploration and assessment skills can be used separately. When paired,
exploration supplies evidence and isolated candidates; independent assessment
makes the retention decision.
Neither skill grants implementation, integration, merge, publication, or
destructive-action authority.

## Deliberate installation

These examples are instructions for a deliberate future installation. They have
not been run by this repository.

Before copying, inspect the destination and run `/skills list`. Stop if a
same-named skill already exists; do not overwrite an existing global or
working-directory definition.

Copy only the skills you want, including their supporting files. The commands
below show all available skills; check each destination before copying.

Install globally, for use across projects:

```sh
mkdir -p ~/.benson/skills
cp -R skills/codebase-audit ~/.benson/skills/codebase-audit
cp -R skills/exploration ~/.benson/skills/exploration
cp -R skills/independent-assessment ~/.benson/skills/independent-assessment
```

Install for one repository instead:

```sh
mkdir -p .benson/skills
cp -R skills/codebase-audit .benson/skills/codebase-audit
cp -R skills/exploration .benson/skills/exploration
cp -R skills/independent-assessment .benson/skills/independent-assessment
```

After choosing one destination, run `/skills reload`. If the installation adds
new Discord skill choices, run `/commands sync-discord` as a separate deliberate
operation.

## Example codebase audit

After deliberately installing the skill:

```text
/skill run name:codebase-audit prompt:"Check database speed and failure recovery in this project. Investigate only those two topics, verify important findings, and bring me one report. Do not implement fixes."
```

A broad request can ask the parent to choose relevant checks from the eight
available topics. The selected finite list bounds the audit; supplied limits
still apply. Benson's existing child Workspaces and asynchronous returns handle
the work. Missing tools or data are reported as limits, not successful checks.
No additional skills or third-party services are required by this skill.
It needs Benson's supported child dispatch and return tools for coordination.

The readable title requires a Benson version with skill-title support. The
command identifier remains `codebase-audit`. Nothing in this library is installed,
reloaded or run merely by cloning it.

## Example campaign

Start exploration with one campaign identifier, explicit scope and limits:

```text
/skill run name:exploration prompt:"Campaign checkout-reliability-2026-11: investigate reported checkout data loss against origin/main for two hours, with at most six child investigations and three candidate branches. Let started children finish after discovery stops. Candidate edits are allowed only in isolated branches; do not merge or publish."
```

Exploration chooses investigations autonomously within those limits. It stops
new discovery at the first applicable limit, then collects already-started work.
The report may finish after the discovery window. If the extent is ambiguous,
it asks before starting. It does not measure remaining provider allowance.

Then invoke assessment independently with the exact exploration sources and
current comparison base:

```text
/skill run name:independent-assessment prompt:"Assess campaign checkout-reliability-2026-11. Compare the supplied candidate commits and exploration report with origin/main at <sha>. Produce or update the campaign's single Inbox report; do not integrate candidates."
```

The assessor may keep nothing. Passing tests alone do not make a candidate worth
retaining.
