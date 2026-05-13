# Benchmark Claims Are Hard to Trust

## The pain in one sentence

Benchmark results are often cherry-picked, unverifiable, or impossible to reproduce — making performance claims unreliable.

## Who feels this pain

- Buyer — making decisions based on unverifiable benchmarks
- CTO — comparing vendors with incomparable metrics
- Investor — evaluating capability based on curated numbers
- Developer team — cannot reproduce claimed results

## What this pain impacts

- **Trust:** Cherry-picked benchmarks destroy credibility when discovered
- **Buyer confidence:** Skeptical buyers dismiss benchmark claims
- **Money:** Wrong purchasing decisions from misleading benchmarks

## What usually goes wrong

A vendor publishes benchmark results showing excellent performance. The methodology is unclear. The test data is not available. The results cannot be reproduced by the buyer. The vendor selected the best run from twenty attempts and published that one. When a buyer tries to replicate, they get different (usually worse) results.

## Which Razorglint systems help

- [CTLM Engine](../systems/005-ctlm-engine.md) — reproducible benchmarks with raw results
- [Prestige-Forge](../systems/006-prestige-forge.md) — evidence capture for any test run

## How those systems solve it

Benchmarks are run with documented methodology. Raw results are captured and available — not curated summaries. The buyer can re-run the same benchmark suite on the same test data and compare. Results are hashed and timestamped. No cherry-picking — all runs are recorded.

## How someone would use this

1. Request benchmark methodology and raw results
2. Review the test data used
3. Re-run the benchmark suite independently
4. Compare raw results against claimed results
5. Check that results are timestamped and hashed

## License/tier fit

- Starter — access to benchmark results and methodology
- Professional — reproducible benchmark suite

## How it saves reputation, data, and money

- **Reputation:** Honest, reproducible benchmarks build long-term trust
- **Data:** Raw results available for independent verification
- **Money:** Better purchasing decisions from reliable performance data

## Buyer-safe claim

"Benchmarks are run with documented methodology and raw results are available for independent reproduction."

## What this does NOT prove

This does not prove the system is the best performer. It proves the results are honest and reproducible. Comparative benchmarks against competitors have not been independently verified.

## Simple explanation for a 12-year-old

"Imagine a student says they scored 95% on a test. But they will not show you the test paper or let you see the questions. This system shows you the test, the answers, and the score — so you can check if the 95% is real."

## Where proof lives

This repo does not store proof. It maps pain to system.

Proof artifacts for this painpoint live in:
- `systems-architecture/EVIDENCE_MAP/` — CTLM benchmark evidence
- `systems-architecture/EVIDENCE_MAP/CTLM_BENCHMARK_EVIDENCE_BUYER_SAFE.md` — buyer-safe benchmark summary
- CTLM repos — benchmark suite and raw results

---

## Non-claim boundary

This does not prove certification, compliance, external audit, universal coverage, production deployment, or that all possible paths are governed. It maps the painpoint to systems and proof locations within the documented scope.
