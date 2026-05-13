# Policy Changes Happen Without Proof of Authorization

## The pain in one sentence

Security and governance policies are modified — loosened, overridden, or replaced — with no tamper-evident proof of what changed, who authorized it, or whether the new policy was integrity-verified before deployment.

## Who feels this pain

- Security officer — responsible for policy integrity across classified systems
- Compliance team — NIST 800-53 CM-3 describes configuration change control with evidence
- Auditor — asks "prove this policy was authorized and integrity-verified before deployment"
- Accreditation reviewer — continuous ATO depends on provable policy baseline
- System administrator — needs to prove policy changes were not unauthorized

Framework references are relevance mappings only. They do not claim compliance, certification, accreditation, legal sufficiency, or acceptance by any authority.

## What this pain impacts

- **Accreditation support:** Unauthorized policy changes can invalidate Authority to Operate
- **Compliance:** CMMC CM-3 and NIST 800-53 CM-3 describe auditable configuration management
- **Trust:** Policy drift without evidence erodes trust in governance infrastructure
- **Legal exposure:** Loosened policy after an incident suggests negligence if no authorization trail exists
- **Operational integrity:** Silent policy changes create gaps between documented and actual security posture

## What usually goes wrong

A governance policy is deployed: "deny network access to AI agents." Six weeks later, the policy is modified to "allow network access for research agents." The modification may have been authorized or may have been an unauthorized convenience change. Either way, there is no cryptographic proof of what the policy said before the change, what it says now, whether the new version was integrity-verified, or who authorized the transition. When an incident occurs through the newly permitted path, the investigation finds no evidence of the policy change decision.

## Which Razorglint systems help

- [PolicySourceEngine](../SUPPORTING_SYSTEMS_MAP.md) — SHA-256 verified policy pack loading with per-document integrity
- [ChessClock](../SUPPORTING_SYSTEMS_MAP.md) — hash-chained temporal record of policy evaluation events
- [SAR Guardian](../systems/001-sar-guardian.md) — enforcement receipts showing which policy was active during each decision

## How those systems solve it

PolicySourceEngine loads policy packs from local folders and verifies integrity via SHA-256 manifest hashes. Every document in the pack is individually hashed. The `/evaluate` endpoint runs a deterministic checklist (TECH-001/002, POL-001, LEG-001/002) and returns PASS/FAIL/DEGRADED — no LLM, no external calls, fully deterministic. The `/reload` endpoint re-scans policy packs and detects changes. ChessClock records policy evaluation events in a hash-chained log with timestamps, actor, and machine attribution. SAR Guardian's enforcement receipts reference the active policy state at decision time, creating a linkage between policy version and enforcement decisions.

## How someone would use this

1. Load policy packs into PolicySourceEngine with SHA-256 manifests
2. Run `/evaluate` to establish baseline PASS
3. Schedule periodic `/evaluate` calls to produce timestamped governance evidence
4. On policy changes: `/reload` detects modifications, `/evaluate` verifies new integrity
5. ChessClock records each evaluation event in the hash-chained log
6. After an incident: cross-reference SAR receipts with policy evaluation timeline to prove which policy was active

## License/tier fit

Professional → Enterprise

## How it saves reputation, data, and money

- **Reputation:** "Here is the hash-chained policy evaluation history and per-document integrity verification" replaces "we think the policy was approved"
- **Data:** SHA-256 per-document verification catches any unauthorized modification
- **Money:** Provable policy change control supports accreditation readiness and reduces re-assessment risk and re-assessment costs

## Buyer-safe claim

"PolicySourceEngine verifies policy pack integrity via SHA-256 per-document hashing with deterministic PASS/FAIL/DEGRADED verdicts. ChessClock records evaluation events in an append-only hash-chained log. No LLM, no external calls — fully deterministic evaluation."

This claim follows Prestige-Forge discipline: mapped to PolicySourceEngine + ChessClock + SAR Guardian, proof in respective repos, non-claim boundary below.

## What this does NOT prove

This does not prove policies are good — it proves they are integrity-verified and that changes are detectable. PolicySourceEngine does not evaluate policy quality or effectiveness. It proves structural integrity and version provenance. Not all policy storage systems are monitored — only packs loaded into PolicySourceEngine are verified.

## Simple explanation for a 12-year-old

"Imagine the school rules are posted on a bulletin board. Right now, someone can change a rule overnight and nobody can prove what it said before. This system takes a fingerprint of every rule document. If someone changes even one word, the fingerprint changes, and the system records exactly when it noticed the difference."

## Where proof lives

- PolicySourceEngine repo — policy pack verification, checklist evaluation, hash manifest validation
- ChessClock repo — hash-chained event log for temporal evidence
- SAR repo — enforcement receipts linked to active policy state
