# Glossary — Simple Definitions

Plain-language definitions for terms used in this repo.

---

**Painpoint** — A specific problem that causes real damage to a person, team, or organization. Not a feature request. Not a wish. A thing that hurts.

**Proof artifact** — A file produced by a system that proves something happened. Examples: a test result, a receipt, a hash, a signed document. It exists on disk and can be independently checked.

**Receipt** — A record that proves a decision was made. Like a receipt from a store — it says what happened, when, and what the result was. In Razorglint systems, receipts are hash-chained so tampering is detectable.

**Truthpack** — A portable package of proof artifacts that a buyer can take away and verify without trusting the vendor. Contains evidence, proofs, a manifest listing all files with hashes, and verification instructions.

**Persistent operational memory** — The ability of a system to remember context, decisions, and reasoning across sessions. Without it, every session starts from scratch. With it, sessions build on prior knowledge.

**Governance** — The rules, checks, and enforcement that control what a system is allowed to do. Good governance produces proof. Bad governance produces policy documents that nobody checks.

**Deny-by-default** — Nothing is allowed unless explicitly permitted. The opposite of "allow everything unless blocked." If there is no rule granting permission, the action is denied and a receipt is produced.

**Claim boundary** — The line between what you can safely say and what would be overclaiming. Example: "tamper-evident" (detectable) is within boundary. "Tamper-proof" (impossible) is not.

**Buyer-safe language** — Words and phrases that are defensible if challenged by a skeptical engineer, a lawyer, a security reviewer, or a hostile public critic. No exaggeration. No ambiguity.

**License tier** — A level of access to the technology. Higher tiers include more systems and more capabilities. Each tier has a clear boundary of what is and is not included.

**White-label** — Embedding someone else's technology into your own product under your own brand. The end user sees your brand, not the original maker's.

**Strategic license** — An exclusive or semi-exclusive right to use the technology in a specific industry, region, or use case. More than a regular license, less than an acquisition.

**Due diligence** — The process a buyer goes through to verify that something is real before committing money. In this context: checking that governance claims are backed by proof, that tests actually pass, and that the technology works as described.

**Reputation risk** — The chance that your public image is damaged because something you said turns out to be wrong, exaggerated, or unsupported. In governance: claiming compliance without evidence, or claiming security without proof.

**Operational continuity** — The ability to keep running without interruption. When governance context is lost, when memory resets, when fleet nodes drift — operational continuity breaks.
