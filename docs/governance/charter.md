# Data Governance Charter

_Fil Rouge — single-premium deferred annuity project. The authoritative
statement of who owns this project's data, what its terms mean, and the
controls that keep it trustworthy._

## 1. Scope
Governs the two datasets produced by `filrouge.data.generate`: `policies`
and `mortality_table`. All data is **synthetic** — no real or confidential
personal data is used at any point.

## 2. Ownership and roles
In a production insurer these roles belong to different people; here they
are held by one practitioner but named separately so accountability is explicit.

- **Data owner** — accountable for definitions, quality standards, and
  approving schema changes.
- **Data steward** — maintains the generator, schema, and data dictionary;
  runs and records validations.
- **Consumers** — the provisioning engine, the AI studies, and the dashboard.
  They read the governed data; they do not alter it.

Schema changes are the data owner's decision, made through a pull request
(Section 5), never an ad-hoc edit.

## 3. Definitions
The field-level data dictionary (`docs/data.md`) is the **authoritative**
definition of every column; consumers must not redefine terms locally.
Key business terms:

- **Valuation date** — the single "as of" date all calculations anchor to
  (2025-12-31). Ages and durations are derived relative to it, never stored.
- **Status** — `active` (in force, carries a reserve), `lapsed` (terminated,
  no future obligation), `deceased` (no future obligation).
- **qx** — probability that a life aged *x* dies within one year; the
  mortality basis for the reserve.
- **Provision / reserve** — the expected present value of future obligations
  the insurer must hold today (built in Week 5).

## 4. Controls
Trustworthiness rests on four controls, enforced automatically rather than
by good intentions:

- **Reproducibility** — data is regenerated from a fixed seed under a pinned
  environment (Python 3.13; numpy 2.1.3, pandas 2.2.3, pyarrow 18.1.0). The
  same seed yields identical data.
- **Provenance** — raw data is not committed; the generator and seed are the
  artifact, so every dataset is traceable to the code that produced it.
  `_generation_metadata.json` records seed, row count, valuation date, and
  library versions for each run.
- **Version control** — changes reach `main` only through a pull request that
  passes CI; the merge history is the audit trail.
- **Validation** — automated data-quality checks gate the pipeline
  (introduced Week 3); bad data fails the build.

## 5. Change process
To change a definition or the schema: branch, update the generator and
`docs/data.md` together, pass `mkdocs build --strict` and CI, and merge via a
pull request approved by the data owner. Definitions and code never drift
apart because they change in the same commit.
