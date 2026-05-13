# Fleet Nodes Can Be Spoofed or Impersonated

## The pain in one sentence

In distributed fleets — unmanned vehicles, edge nodes, mesh sensors — there is no simulation-grade trust model showing how node identity, software-state comparison, credential rotation, and authority state can be governed without relying on node self-report.

## Who feels this pain

- Fleet operator — managing nodes that could be spoofed or compromised
- Security officer — responsible for node authentication in contested environments
- Mission planner — depends on trust status of fleet nodes for mission decisions
- System architect — designing zero-trust fleet architectures
- Incident responder — must identify compromised or impersonated nodes

## What this pain impacts

- **Mission safety:** A spoofed node reporting false status can cause incorrect mission decisions
- **Trust degradation:** Without attestation, trust is asserted by the node itself — self-reported trust is not trust
- **Operational security:** Adversaries can impersonate fleet nodes to inject false data
- **Credential compromise:** Static credentials shared across fleet nodes mean one compromise = fleet compromise
- **Compliance:** NIST 800-53 IA-3 (device identification and authentication) describes cryptographic device identity requirements

Framework references are relevance mappings only. They do not claim compliance, certification, accreditation, legal sufficiency, or acceptance by any authority.

## What usually goes wrong

A fleet of autonomous nodes operates across a network. Each node reports its identity and status. But identity is self-asserted — the node says "I am Node-7" and the fleet trusts it. Credentials are static shared secrets or certificates with long validity periods. A compromised node can impersonate another node, report false health status, or relay poisoned data. Software integrity is self-reported — a compromised node can report "running approved firmware" while actually running modified code. When credentials are rotated, all nodes share the same rotation schedule with no per-node cryptographic binding.

## Which Razorglint systems help

- [FleetSim Trust Plane](../systems/007-fleetsim-trust-plane.md) — attestation-based identity lifecycle, HMAC-SHA256 per-node credential derivation, software-state verification
- [Blackiron](../SUPPORTING_SYSTEMS_MAP.md) — hash chains and Merkle trees for identity state evidence
- [SAR Guardian](../systems/001-sar-guardian.md) — fleet/unit registry with per-agent authentication

## How those systems solve it

FleetSim models a trust-plane authority that controls node identity through a lifecycle: UNREGISTERED → REGISTERED → KNOWN → ATTESTED → TRUSTED → SUSPENDED → REVOKED. Attestation is not self-reported — the trust-plane holds expected software baselines, nodes report their hash, and the plane verifies the match. Credential rotation uses HMAC-SHA256 per-node token derivation from a master secret + node_id + trust_epoch. Nodes verify tokens but never see the master secret. Every identity transition produces a receipt signed by the trust-plane authority. SAR provides fleet/unit registry infrastructure with per-agent authentication and API key fingerprinting (non-reversible SHA-256 hash).

## How someone would use this

1. Register fleet nodes with the trust-plane authority
2. Nodes submit software-state hashes for attestation verification
3. Trust-plane compares reported hash against known-good baseline
4. Attested nodes receive per-node derived credentials (HMAC-SHA256)
5. Every identity transition is receipted with trust-plane authority signature
6. Compromised or drifted nodes are automatically SUSPENDED with degradation timer
7. REVOKED nodes cannot re-enter the fleet without re-registration

## License/tier fit

Operator → Enterprise

## How it saves reputation, data, and money

- **Reputation:** "Software-state comparison and trust-plane receipts reduce reliance on self-report" replaces "nodes register themselves"
- **Data:** Per-node credential derivation means one compromised node does not compromise fleet credentials
- **Money:** Detecting a spoofed node before it poisons fleet data helps reduce cascade failure and mission abort risk

## Buyer-safe claim

"FleetSim models attestation-based node identity with trust-plane-verified software-state comparison. Credentials are HMAC-SHA256 derived per-node from a master secret the node never sees. Every identity transition produces a trust-plane-signed receipt. This is simulation-grade modeling of fleet trust behavior."

This claim follows Prestige-Forge discipline: mapped to FleetSim + Blackiron + SAR Guardian, proof in respective repos, non-claim boundary below.

## What this does NOT prove

FleetSim is simulation-grade — it models the trust-plane pattern but is not a production fleet management system. It does not prove hardware-level attestation (TPM, secure enclave). It does not prove all fleet nodes participate in the trust-plane protocol. Software-state comparison detects known-bad hashes but does not detect novel malware that produces the expected hash.

## Simple explanation for a 12-year-old

"Imagine a team of delivery robots. Right now, any robot can say 'I'm Robot 5' and everyone believes it. This system makes each robot prove its identity — show its software fingerprint, get checked against the known-good fingerprint, and receive a personal password that only works for that robot. If a fake robot shows up, it can't pass the fingerprint check."

## Where proof lives

- FleetSim repo — identity lifecycle tests, attestation verification, credential derivation, severity ladder
- Blackiron repo — hash chain and Merkle primitives underlying receipt infrastructure
- SAR repo — fleet registry, per-agent authentication, API key fingerprinting
