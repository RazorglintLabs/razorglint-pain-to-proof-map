# OpenClaw Governed Agents

## One-sentence explanation

OpenClaw runs AI agents under SAR governance so no agent defines its own rules — every action produces a receipt and every output is exportable as a Truthpack.

## What pain it solves

- PP-001: We cannot prove what the AI did
- PP-002: Denied actions disappear
- PP-005: Runtime failure gets hidden

## How it solves the pain

Agents execute within SAR’s enforcement layer. They do not get to decide what they are allowed to do — the policy does. Every governed action on the covered path produces a receipt through dual-write architecture (the action and its governance record are written together). When the agent finishes, its outputs can be packaged as a Truthpack that a buyer or auditor can locally verify using hashes, manifests, and instructions.

## What it protects

- **Trust:** Agents on the governed path cannot bypass governance
- **Safety:** The covered governed path requires receipts for accepted actions
- **Data:** Receipt-backed action trail for covered lanes is exportable
- **Buyer confidence:** Truthpack output is locally verifiable using hashes and manifests

## Who would use it

- AI governance team — governed agent operations
- CTO — oversight of agent behavior
- Operator — daily agent management
- Auditor — agent action review

## How to use it

- Deploy agents under OpenClaw governance
- Review dual-write receipts after agent runs
- Export outputs as Truthpacks for buyer or auditor consumption
- Trace any agent action back to its policy authorization

## License/tier fit

- Professional
- Enterprise

## Value created

- **Reputation:** No unaccountable agent behavior on governed paths
- **Data:** Receipt-backed action trail per agent run for covered lanes
- **Time:** Agent debugging uses receipt replay
- **Money:** Reduced risk from ungoverned agent actions

## Proof location

Proof artifacts live in the OpenClaw repo (`C:\OpenClaw\`).
Test evidence: 1,578 passing tests across 45 test modules.
See `systems-architecture/APPROVED_PUBLIC_CLAIMS.md` claims #14–16.

## Claim boundary

**Can say:**
- "OpenClaw agents run under SAR governance. No agent defines its own rules."
- "Every governed action on the covered path produces a receipt. Outputs are exportable as Truthpacks."
- "1,578 tests passing across 45 test modules."

**Must not say:**
- "Agents cannot be compromised" — governance prevents unauthorized actions, but does not claim immunity to all attack vectors
- "Complete test coverage" — 156 skipped tests documented in audit
