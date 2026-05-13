# Privileged Terminal Commands Leave No Proof

## The pain in one sentence

System administrators execute destructive, privileged, and sensitive terminal commands on critical infrastructure with no tamper-evident record of what was run, what was denied, or what authorization existed.

## Who feels this pain

- Security officer — responsible for privileged access monitoring
- System administrator — needs to prove authorized actions were authorized
- Inspector general — investigating potential insider threat
- Compliance team — NIST 800-53 AC-2/AU-12 require privileged activity logging
- Incident responder — reconstructing what happened on a compromised host

## What this pain impacts

- **Insider threat:** Privileged users can execute destructive commands with no evidence trail
- **Compliance:** CMMC Level 2+ and NIST 800-53 describe audit requirements for privileged access
- **Incident response:** Without command-level receipts, forensic reconstruction is guesswork
- **Legal exposure:** Cannot prove what an administrator did or did not do during an incident
- **Data loss:** Destructive commands (`rm -rf`, `format`, `dd`) leave no pre-execution proof of authorization

Framework references are relevance mappings only. They do not claim compliance, certification, accreditation, legal sufficiency, or acceptance by any authority.

## What usually goes wrong

An administrator connects to a production server. Over the next hour they run dozens of commands — some routine, some destructive. Shell history captures some of it, but history files are editable text with no integrity guarantee. When an incident occurs — data deleted, config changed, exfiltration attempted — the investigation depends on mutable, unsigned, easily purged logs. The administrator can clear history, and no mechanism distinguishes between authorized destructive actions and unauthorized ones.

## Which Razorglint systems help

- [Command Guardian](../SUPPORTING_SYSTEMS_MAP.md) — deny-by-default terminal enforcement with hash-chained receipts
- [SAR Guardian](../systems/001-sar-guardian.md) — signed receipt chains for governance evidence

## How those systems solve it

Command Guardian classifies every terminal command into intent categories: `safe_echo`, `shell_run`, `file_delete`, `network_exec`, `privilege_escalation`, `disk_format`, `process_kill`, `system_config`. Always-block rules hard-deny the most dangerous patterns (`rm -rf /`, `curl | bash`, `mkfs`, PowerShell download-and-execute) with no override. Risky intents require explicit, time-bounded allow tokens (`guardian allow <intent> --ttl <sec>`). Every ALLOW and DENY produces a SHA-256 hash-chained receipt in an append-only JSONL ledger. DENY receipts sanitize the command text (store SHA-256 hash) to prevent AV false positives. The chain is verifiable with `guardian verify`.

## How someone would use this

1. Install Command Guardian on administered systems
2. Terminal commands pass through the 4-gate enforcement pipeline
3. Destructive patterns are hard-blocked regardless of user privilege
4. Risky operations require time-bounded pre-authorization tokens
5. After an incident, replay the receipt chain to see every command attempted, allowed, or denied
6. Verify chain integrity with `guardian verify`

## License/tier fit

Professional → Enterprise

## How it saves reputation, data, and money

- **Reputation:** "Here is the hash-chained record of every privileged command" replaces "we checked the bash history"
- **Data:** Hard-block rules prevent the most destructive commands from executing, period
- **Money:** Provable command-level audit trail reduces incident investigation time and compliance audit costs

## Buyer-safe claim

"Command Guardian classifies terminal commands by intent and enforces deny-by-default for destructive operations. Always-block rules cannot be overridden. Every ALLOW and DENY produces a SHA-256 hash-chained receipt. Risky intents require time-bounded authorization tokens."

This claim follows Prestige-Forge discipline: mapped to Command Guardian + SAR Guardian, proof in respective repos, non-claim boundary below.

## What this does NOT prove

This does not prove Command Guardian intercepts all command execution paths. It governs commands routed through the guardian interface. Users who bypass the terminal wrapper are not governed. This is a seatbelt, not a cage — it prevents accidental and opportunistic harm on the governed path, not all possible command execution.

## Simple explanation for a 12-year-old

"Imagine every time a janitor uses a master key, the lock writes down what door was opened, when, and whether the key was authorized for that door. If the janitor tries to open a door they shouldn't, the lock says no and writes that down too. That's what this does for computer commands."

## Where proof lives

- Command Guardian repo — receipt chains, intent classification tests, always-block verification
- SAR repo — complementary receipt infrastructure
