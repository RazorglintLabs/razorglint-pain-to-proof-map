# License Tier Map

Which systems belong in which tier, what the buyer gets, and what they do not get.

See [PAINPOINT_TIER_MATRIX.md](PAINPOINT_TIER_MATRIX.md) for painpoint-level minimum tier gating.
See [TIER_GATING_RULES.md](TIER_GATING_RULES.md) for tier boundary enforcement rules.

---

## 1. Free / Public Proof Reference

### Who it is for

Anyone evaluating the stack. Developers, security researchers, curious engineers.

### What pain it solves

- Cannot verify claims without access (PP-006)
- Technical proof does not automatically sell (PP-014)

### Included systems

- This repo (painpoint-to-system map)
- Public README files and claim boundaries
- Published test counts and methodology descriptions

### What buyer gets

- Clear understanding of what each system does
- Claim boundary awareness (what is and is not claimed)
- Pointers to where proof artifacts live

### What buyer does NOT get

- Source code
- Proof bundles
- Receipts or evidence files
- Operational access

### Why this tier saves money/reputation/data

- **Money:** Free evaluation saves wasted sales cycles
- **Reputation:** Honest claim boundaries build trust before any purchase
- **Data:** No data exchanged at this tier

---

## 2. Starter

### Who it is for

Small teams, solo founders, early-stage operators who need basic governance proof.

### What pain it solves

- Operational memory gets lost (PP-004)
- Operators cannot debug the system (PP-011)
- Benchmark claims are hard to trust (PP-007)

### Included systems

- Persistent Operational Memory (basic)
- Truthpacks (read-only verification)
- CTLM Engine (basic retrieval)

### What buyer gets

- Persistent memory across sessions
- Basic proof verification capability
- Reproducible benchmark results

### What buyer does NOT get

- Enforcement receipts
- Hash-chained audit trails
- Claims Safety Engine
- Fleet governance
- Custom policy evaluation

### Why this tier saves money/reputation/data

- **Money:** Reduced rework from lost context
- **Reputation:** Consistent decisions across sessions
- **Data:** No context loss between sessions

---

## 3. Professional

### Who it is for

Teams that need to prove their governance to buyers, auditors, or internal stakeholders.

### What pain it solves

- We cannot prove what the AI did (PP-001)
- Governance is only policy theater (PP-003)
- Buyer cannot verify claims (PP-006)
- Runtime failure gets hidden (PP-005)
- Compliance language can create legal risk (PP-012)

### Included systems

- SAR Guardian (enforcement + receipts)
- Prestige-Forge (proof engine)
- Truthpacks (full bundle generation)
- Claims Safety Engine
- ChessClock (event spine)

### What buyer gets

- Hash-chained enforcement receipts
- Proof bundles with SHA-256 manifests
- Claims safety verdicts (SAFE_TO_SAY / AT_RISK)
- Temporal event logging
- Buyer-verifiable evidence packs

### What buyer does NOT get

- Fleet governance
- Custom policy engine
- OEM/white-label rights
- Source code access

### Why this tier saves money/reputation/data

- **Money:** Faster audit prep, fewer compliance failures
- **Reputation:** Provable governance replaces promises
- **Data:** Tamper-evident evidence chain

---

## 4. Operator

### Who it is for

Teams running controlled deployments that need continuous governance and fleet awareness.

### What pain it solves

- Fleet nodes can drift or go rogue (PP-009)
- Policy drift can destroy trust (PP-010)
- Operational memory gets lost (PP-004)
- Runtime failure gets hidden (PP-005)

### Included systems

- Everything in Professional
- FleetSim Trust Plane
- PolicySourceEngine
- CTLM Engine (full)
- Persistent Operational Memory (full)

### What buyer gets

- Fleet heartbeat monitoring and drift detection
- Policy pack integrity verification
- Full operational memory with retrieval
- Severity ladder and distress pulse handling

### What buyer does NOT get

- OEM/white-label rights
- Source code access
- Custom module development

### Why this tier saves money/reputation/data

- **Money:** Early drift detection in controlled deployments helps reduce expensive incident risk
- **Reputation:** Rogue nodes caught before damage in governed scope
- **Data:** Receipt-backed fleet state visibility inside simulation scope

---

## 5. Enterprise

### Who it is for

Organizations with regulatory-readiness requirements, external auditors, or buyer due-diligence obligations.

### What pain it solves

- All painpoints above
- Security work is hard to package safely (PP-008)
- Compliance language can create legal risk (PP-012)
- A good system still needs a clear buying path (PP-013)

### Included systems

- Everything in Operator
- BountyPipeline Sidecar
- EU AI Act Readiness (article mapping)
- OpenClaw Governed Agents
- Voidlock (execution cages)

### What buyer gets

- Full stack governance review
- Regulatory-readiness article-to-evidence mapping
- Agent execution cages with capability attenuation
- Security evidence packaging with chain-of-custody
- Shareable proof reports for third parties

### What buyer does NOT get

- OEM/white-label rights
- Source code ownership
- Exclusive licensing

### Why this tier saves money/reputation/data

- **Money:** Reduced regulatory penalty risk, faster governance review cycles
- **Reputation:** Evidence-mapped regulatory-readiness (not compliance certification)
- **Data:** Receipt-backed governance trail from agent to audit for covered paths

---

## 6. OEM / White-label

### Who it is for

Platform vendors who want to embed Razorglint governance into their own products.

### What pain it solves

- Their customers need governance proof and they cannot build it themselves
- Platform trust requires embedded proof infrastructure

### Included systems

- Selected modules from the stack, embedded under the buyer's brand
- Integration support for the buyer's existing systems

### What buyer gets

- Embeddable governance modules
- Integration guidance
- Co-branding rights for selected components

### What buyer does NOT get

- Full source code ownership
- Right to resell as standalone product
- Modification rights without agreement

### Why this tier saves money/reputation/data

- **Money:** Build-vs-buy savings — years of R&D avoided
- **Reputation:** Embedded proof infrastructure enhances platform trust
- **Data:** Governance layer protects platform and end-user data

---

## 7. Strategic License

### Who it is for

Organizations that need exclusive or semi-exclusive rights in a specific vertical or geography.

### What pain it solves

- Competitive differentiation through governance infrastructure
- Regulatory compliance in regulated industries (finance, healthcare, defense)

### Included systems

- Negotiated subset or full stack
- Exclusive deployment rights within defined scope

### What buyer gets

- Defined exclusivity window
- Priority support and roadmap input
- Custom integration engineering

### What buyer does NOT get

- Ownership of IP
- Rights outside agreed scope
- Modification rights without agreement

### Why this tier saves money/reputation/data

- **Money:** First-mover advantage in governed AI within their vertical
- **Reputation:** Exclusive governance capability as market differentiator
- **Data:** Strongest governance evidence density available

---

## 8. Private IP Sale / Acquisition

### Who it is for

Acquirers who want to own the technology outright.

### What pain it solves

- Need to own, not license, governance infrastructure
- Strategic acquisition of proof-producing capability

### Included systems

- Full source code and IP transfer for negotiated assets
- All documentation, test suites, and proof artifacts

### What buyer gets

- IP ownership
- Full source code
- Right to modify, deploy, and sublicense

### What buyer does NOT get

- Anything excluded from the acquisition agreement
- Ongoing development commitment (unless separately contracted)

### Why this tier saves money/reputation/data

- **Money:** Own the asset instead of paying recurring license
- **Reputation:** Full control over governance claims
- **Data:** Complete sovereignty over the technology
