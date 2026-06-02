# Project Brief — Fil Rouge (locked in Week 1)

## Mission
Using a synthetic life & retirement insurance dataset, build a governed
data layer, an actuarial provisioning engine, two AI-driven innovation
studies, a domain AI agent, and an automated decision dashboard — all
reproducible, documented, and audit-ready.

## What gets built (the dependency chain)
1. Governed data layer — validated, clearly-defined data with an audit trail.
2. Provisioning engine — computes the *provision* (reserve): the money the
   insurer must hold today to cover its future obligations to policyholders.
3. Innovation study 1 — absenteeism, framed as a management decision.
4. Innovation study 2 — health & climate, on differently-shaped data.
5. Domain AI agent — an LLM assistant that queries the engine and data
   under explicit guardrails.
6. Decision dashboard + continuous reporting — regenerated automatically.

## Data
- Synthetic, generated programmatically: policies, claims, mortality
  experience. No real or confidential data, at any point.
- Supplemented by open data: published mortality tables (engine);
  open climate/health datasets (study 2).

## Modelling target (in scope)
- Single line of business: a deferred annuity — a retirement product where
  the policyholder pays in, then receives income for life from retirement age.
- Currency: EUR. Portfolio: ~200,000 synthetic policies.

## Regulatory frame (named now; specifics verified in Week 10)
Solvency II, IFRS 17, EU AI Act, GDPR. European life & retirement context.

## Non-negotiable, cross-cutting
Reproducibility, traceability, explainability, documented assumptions,
audit-readiness — enforced via Git, CI, and the docs site every week.

## Out of scope (explicit, to stop scope creep)
- Actuarial completeness — the engine must be correct, documented, and
  testable, not exhaustive.
- Multiple products, riders, reinsurance.
- Real data; production deployment.

## Definition of done (Week 14)
An independent auditor and a line manager can each rely on the system
without re-doing the work: the auditor follows assumptions → controls →
lineage; the manager reads decisions off the dashboard.
