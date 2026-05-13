# AI Governance Evidence Does Not Map to Regulatory Frameworks

## The pain in one sentence

Organizations have AI systems in production but cannot produce structured, article-mapped evidence for regulatory frameworks — EU AI Act, DoD RAI principles, NIST AI RMF — because governance evidence exists as scattered artifacts with no framework alignment.

## Who feels this pain

- Compliance officer — must produce regulatory evidence packages on demand
- Legal team — exposure from unstructured governance claims
- Program manager — responsible for AI system governance readiness under emerging frameworks
- CTO — accountable for AI governance posture across the organization
- Procurement officer — needs AI governance evidence from vendors before contract award

Framework references are relevance mappings only. They do not claim compliance, certification, accreditation, legal sufficiency, or acceptance by any authority.

## What this pain impacts

- **Regulatory readiness:** EU AI Act enforcement begins with evidence requirements — no mapped evidence = not ready
- **Market access:** EU market requires AI governance evidence for high-risk systems
- **Coalition partnerships:** US-EU defense partnerships increasingly require AI governance alignment
- **Procurement decisions:** DoD CDAO responsible AI framework needs structured evidence from AI vendors
- **Legal exposure:** Unstructured AI governance claims create liability when regulators ask for evidence

## What usually goes wrong

An organization deploys AI systems with governance — receipts, policies, logs. When a regulatory body asks "show me your risk management evidence for Article 9" or "demonstrate human oversight per Article 14," the team scrambles. Evidence exists but is scattered across repos, logs, and documents. There is no mapping from evidence artifacts to regulatory articles. The gap between "we do governance" and "we can prove governance against this specific regulatory framework" creates compliance risk and delays procurement decisions.

## Which Razorglint systems help

- [EU AI Act Evidence Readiness](../SUPPORTING_SYSTEMS_MAP.md) — article-mapped evidence compiler for EU AI Act
- [Prestige-Forge](../systems/006-prestige-forge.md) — evidence-to-proof-to-bundle pipeline with claims safety
- [Truthpacks](../systems/003-truthpacks.md) — portable proof packages for regulatory review
- [SAR Guardian](../systems/001-sar-guardian.md) — governance receipts that feed evidence adapters

## How those systems solve it

EU AI Act Evidence Readiness is a read-only evidence compiler that consumes sealed outputs from SAR, Prestige-Forge, PolicySourceEngine, ChessClock, and oversight logs through 6 adapters. It maps evidence to 6 EU AI Act articles: Art. 9 (Risk Management), Art. 11 (Technical Documentation), Art. 12 (Record-Keeping), Art. 13 (Transparency), Art. 14 (Human Oversight), Art. 15 (Accuracy/Robustness/Cybersecurity). Output includes evidence readiness reports (MD + JSON), evidence index, gap register, and oversight summary. The gap register explicitly identifies what evidence is missing — not just what exists. 33/33 boundary anti-dilution checks PASS: adapters are read-only, no write-back.

## How someone would use this

1. Ensure source systems (SAR, Prestige-Forge, ChessClock, PolicySourceEngine) are producing governance artifacts
2. Run the evidence compiler to map existing artifacts to EU AI Act articles
3. Review the gap register for missing evidence
4. Package evidence readiness report into Truthpacks for regulatory or procurement review
5. Use the evidence index to respond to specific article queries
6. Repeat periodically for continuous compliance readiness

## License/tier fit

Enterprise

## How it saves reputation, data, and money

- **Reputation:** "Here is the article-mapped evidence readiness report with gap register" replaces "we have governance somewhere"
- **Data:** Structured article mapping makes evidence findable and auditable
- **Money:** Pre-mapped regulatory evidence reduces compliance assessment time and procurement delay

## Buyer-safe claim

"EU AI Act Evidence Readiness maps governance evidence to 6 EU AI Act articles through read-only adapters. The gap register identifies missing evidence explicitly. Evidence readiness does not equal compliance — it proves structured preparation. 33/33 anti-dilution boundary checks PASS."

This claim follows Prestige-Forge discipline: mapped to EU AI Act Readiness + Prestige-Forge + Truthpacks + SAR Guardian, proof in respective repos, non-claim boundary below.

## What this does NOT prove

This does not prove EU AI Act compliance. It proves evidence readiness — structured mapping of existing evidence to regulatory articles with explicit gap identification. It does not replace legal counsel, external assessment, or notified body review. Coverage is 6 articles (9, 11, 12, 13, 14, 15) — not the full Act. The tool maps evidence, not quality of governance.

## Simple explanation for a 12-year-old

"Imagine your teacher gives you a checklist for a science project: hypothesis, experiment, data, conclusion. You did the work, but your notes are scattered across 5 notebooks. This system reads all your notebooks and creates a checklist showing exactly which requirements you have evidence for and which ones are missing."

## Where proof lives

- EU AI Act Readiness repo — article-mapped evidence reports, gap register, adapter verification
- Prestige-Forge repo — evidence-to-bundle pipeline
- Truthpacks — portable evidence packages
- SAR repo — governance receipts consumed by adapters
