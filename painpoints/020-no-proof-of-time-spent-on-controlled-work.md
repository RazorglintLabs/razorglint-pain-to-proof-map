# No Proof of Time Spent on Controlled Work

## The pain in one sentence

When controlled or compartmented work requires time accounting — for export control, contract labor, or project segregation — there is no tamper-evident record proving who worked on what, when, and for how long.

## Who feels this pain

- Export control officer — must prove ITAR/EAR time segregation
- Contracting officer — needs DCAA-auditable time records
- Program manager — accountable for labor hour allocation across classified/unclassified work
- Compliance team — must demonstrate no time overlap between controlled programs
- Auditor — DCAA reviews demand reliable time evidence

## What this pain impacts

- **Export control relevance:** ITAR requires proof that controlled technical data work is segregated
- **Contract audit exposure:** DCAA audits flag unreliable time records as fraud indicators
- **Legal exposure:** Misallocated labor hours on government contracts create False Claims Act risk
- **Program integrity:** Time bleed between classified and unclassified work violates compartmentation
- **Financial accuracy:** Unreliable time data leads to incorrect contract billing

Framework references are relevance mappings only. They do not claim compliance, certification, accreditation, legal sufficiency, or acceptance by any authority.

## What usually goes wrong

An engineer works on two projects — one ITAR-controlled, one commercial. They log hours in a timesheet system with no integrity guarantee. The timesheet is editable, retroactively adjustable, and unsigned. During a DCAA audit or export control review, the auditor asks: "Prove this engineer did not work on controlled data during these commercial hours." The company cannot, because the time records are self-reported mutable text. When overlapping work occurs on the same machine, there is no machine-level evidence to corroborate or contradict the timesheet.

## Which Razorglint systems help

- [ChessClock](../SUPPORTING_SYSTEMS_MAP.md) — hash-chained temporal event log with project, actor, and machine attribution
- [Prestige-Forge](../systems/006-prestige-forge.md) — evidence packaging for audit-ready bundles
- [Truthpacks](../systems/003-truthpacks.md) — portable proof packages for external review

## How those systems solve it

ChessClock produces an append-only, SHA-256 hash-chained JSONL event log. Every event records: `event_id`, `timestamp`, `session_id`, `task_id`, `task_name`, `project`, `tags`, `actor`, `machine_id`, `duration_ms`, `artifact_path`, and `artifact_hash`. Chain integrity is verifiable — any modification breaks the hash chain from that point forward. The `project` and `machine_id` fields enable project segregation verification. The `artifact_attach` event type links work products to time records with hash integrity. Prestige-Forge and Truthpacks package this evidence for external auditors.

## How someone would use this

1. Start ChessClock sessions per project with explicit project tags
2. Log task start/stop events with project and machine attribution
3. Attach work artifacts to time records using `artifact_attach` events
4. For audit: export the hash-chained event log
5. Verify chain integrity to prove no retroactive modification
6. Cross-reference project tags and machine_id to demonstrate time segregation
7. Package evidence into Truthpacks for external review

## License/tier fit

Professional → Enterprise

## How it saves reputation, data, and money

- **Reputation:** "Here is the hash-chained time record with machine attribution" replaces "check the timesheet spreadsheet"
- **Data:** Append-only chain with per-event hashing helps detect retroactive time record manipulation
- **Money:** Reliable time evidence reduces DCAA-related dispute exposure of labor costs and export control penalties

## Buyer-safe claim

"ChessClock produces append-only, SHA-256 hash-chained time event logs with project, actor, and machine attribution. Chain integrity is independently verifiable. Artifact attachment links work products to time records with hash integrity."

This claim follows Prestige-Forge discipline: mapped to ChessClock + Prestige-Forge + Truthpacks, proof in respective repos, non-claim boundary below.

## What this does NOT prove

This does not prove that all work time is logged through ChessClock. It proves that time events recorded through ChessClock are tamper-evident and attributable. Self-reported time data is only as accurate as the reporter — ChessClock makes it tamper-evident, not omniscient. Machine_id proves which machine was used, not what the engineer was looking at.

## Simple explanation for a 12-year-old

"Imagine a school attendance book where every entry is written in special ink that changes color if anyone tries to erase or change it. It also records which classroom you were in and what project you were working on. If someone asks 'were you really in science class during that hour?' the book proves it, and no one can change the answer after the fact."

## Where proof lives

- ChessClock repo — hash-chained event log, chain verification, event schema with project/actor/machine fields
- Prestige-Forge repo — evidence packaging pipeline
- Truthpacks — portable proof bundle format
