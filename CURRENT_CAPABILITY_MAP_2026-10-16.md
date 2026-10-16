# Current Capability Map — 16 October 2026

This map distinguishes **problem fit** from **source status** and **qualification**. The recorded facts are a documentation/source review, not execution of all proprietary suites.

| Asset | Buyer pain and capability | Evidence class | Current caveat |
| --- | --- | --- | --- |
| [Compliance Drift Detector](https://github.com/RazorglintLabs/ComplianceDriftDetector) | Policy/evidence divergence across dated checkpoints; recovered history and separately listed undeclared observations | **Current public CI + owner acceptance**, source `662f84caa2ed372abde6a83245c58b466e52ce94`, 76 tests, 16 Oct 2026 | Windows x64 portable v0.2 controlled preview **unsigned**; operator supplies compliant flags; SHA-256 self-consistency not signatures |
| Prestige-Reforged | Versioned evidence, claim evaluation, drift/history, proof handoff | **Private staged engineering / review** | Windows search, product shell and customer delivery not declared final; public cannot independently reproduce its private suites |
| SAR | Deterministic governance / receipted decisions | **Historical tests / private source** | No blanket production integration assumption |
| Viventia | Scoped local-first incident/evidence cockpit | **Private product work / qualification documents** | Not yet a finished enterprise SIEM/EDR or service |
| VEAC | Independent adversarial challenge | **Private system with campaign-scoped tests** | No global pass or product certification |
| GCA Stack | Candidate architecture bringing governance, execution constraints, evidence and challenge together | **Phase 0 component admission and source/IP reconciliation** | Integration, ownership and reproducible buyer acceptance remain gated |
| Command Guardian | Command guardrails, receipts, adversarial test fixes | **26 Apr 2026 historical 131-test snapshot** | Hardened prototype; signing and SAR integration not represented |
| FleetSim | Fleet trust-plane simulation | **26 Apr 2026 historical 103-test snapshot** | Simulation only |
| EU AI Act Evidence Readiness | Read-only evidence mapping | **26 Apr 2026 historical 194-pass snapshot with environment caveats** | Six articles; no legal conclusion |
| OpenClaw / Voidlock / Blackiron / ProofChain / SealVault | Specialized agent, containment and evidence mechanisms | **Historical or local/private engineering record** | No current finished integrated release or third-party IP clearance implied |
| ReasonForge | Data validation/evaluation workflows | **Private or source-available product documentation, not re-executed here** | Commercial availability and test state require per-repo confirmation |

## How to use the historical files

The numbered `painpoints/` files describe *scenarios*, not buyer references or externally confirmed incidents. A historical `PASS` in [the 12 May review](PRESTIGE_FORGE_VERIFICATION_STATUS.md) was a **pattern-based text scan of that version**. It is not an external audit and says nothing about newly rewritten public text unless re-run.

The old license/tier tables are candidate product packaging discussions. They are not proof that every integration, permission, price or customer path exists. Proprietary asset ownership and transfer exclusions must be handled separately; in particular, **Prestige-Reforged ownership is retained by Razorglint** under the current product separation posture.

## Recommended public proof hierarchy

1. Current public repository + exact source commit + linked successful CI receipt.
2. Date-scoped reported local test with platform/skip/failure caveat.
3. Private-source documentation (described, but not public-reproducible).
4. Candidate integration / proposed commercial packaging.
5. Future capability, concept or commercial hypothesis.

Never promote a lower tier of evidence to a higher one just because the architecture diagram looks tidy.

**External source:** [CDD current release status](https://github.com/RazorglintLabs/ComplianceDriftDetector/blob/main/docs/RELEASE_STATUS.md).  
**Historical source:** [Portfolio proof audit](https://github.com/RazorglintLabs/systems-architecture/blob/main/assets/proof/PROOF_AUDIT_2026-04-26.md).

**Review needed after merge:** Run a new, exact-source claim review of this October text and record its result here; the May PASS remains a historical artifact.
