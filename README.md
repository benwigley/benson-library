# Benson Library

Portable skills and workflows for Benson.

## Skills

| Skill | Use it to |
| --- | --- |
| [`exploration`](skills/exploration/SKILL.md) | Investigate a broad problem space, test hypotheses, and, when the current run is explicitly authorized to edit, prepare isolated candidate changes without integrating them. |
| [`independent-assessment`](skills/independent-assessment/SKILL.md) | Independently decide which explored candidates are worth keeping, simplifying, deferring, or rejecting against an exact current base. |

The skills can be used separately. When paired, exploration supplies evidence
and isolated candidates; independent assessment makes the retention decision.
Neither skill grants implementation, integration, merge, publication, or
destructive-action authority.

## Deliberate installation

These examples are instructions for a deliberate future installation. They have
not been run by this repository.

Before copying, inspect the destination and run `/skills list`. Stop if a
same-named skill already exists; do not overwrite an existing global or
working-directory definition.

Install globally, for use across projects:

```sh
mkdir -p ~/.benson/skills
cp -R skills/exploration ~/.benson/skills/exploration
cp -R skills/independent-assessment ~/.benson/skills/independent-assessment
```

Install for one repository instead:

```sh
mkdir -p .benson/skills
cp -R skills/exploration .benson/skills/exploration
cp -R skills/independent-assessment .benson/skills/independent-assessment
```

After choosing one destination, run `/skills reload`. If the installation adds
new Discord skill choices, run `/commands sync-discord` as a separate deliberate
operation.

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
