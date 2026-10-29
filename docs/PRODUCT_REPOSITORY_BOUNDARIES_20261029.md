# BZZY product repository boundaries and source audit

**Audit date:** October 29, 2026
**Change class:** documentation-only / non-destructive
**Review state:** DRAFT; no repository merge, renaming, default-branch change or deployment

## Product repositories and intended authority

| Product boundary | Current repository | What belongs here |
|---|---|---|
| BZZY Solutions (parent business software) | `ForMySumchins/BzzySolutions` | Cross-vertical business capabilities, authenticated shared API boundaries, UCD/CallShield contracts, Mantis/MantisEye/Spider/Honeycombs/Threadline integration points. No claim that all source is already present. |
| BZZY Ants | `ForMySumchins/BzzyAnts` | Lead acquisition, verification, scoring, opportunity explanations, geospatial/Field Operator UX, safe outbox, Ants-to-Bees handoff. |
| BZZY Bees | `ForMySumchins/BzzyBees` | Creative/brand operations and BZZY Bees field-service-facing experience. Contractor UX modules must have explicit ownership; do not infer from repository name. |
| BZZY legacy namespace | `ForMySumchins/Bzzy` | Historical branch and context recovery only; not a second canonical source of rewritten parent modules. |
| Grok staging | `ForMySumchins/bzzy-grok` | Restricted pre-implementation fixtures, not an authorized source of live production code. |

**Other domains** such as Sacred Fool, OTM Community and Afterhours stay outside BZZY product repositories. Integrations must use documented, versioned contracts, not shared private databases or implicit permissions.

## Observed GitHub source evidence

These are repository observations, not a claim that all unexamined branches are empty:

1. `BzzySolutions` default branch `Bzzy`: one placeholder `README.md`. Other named branches exist, but their complete source has not been audited in this packet.
2. `BzzyAnts` default `main`: one placeholder `README.md`. `develop` and `BzzyFieldOperator` appeared similarly minimal. Several feature/agent branches exist and require source-level enumeration before migration.
3. `BzzyBees` default `jules-11031760528795552868-147185b2`: actual Vite/TypeScript/React application with `src/components/ConciergeView.tsx`, `src/components/ContractorDashboard.tsx`, adapters, fixtures and tests. Its `package.json` identifies the application as `bzzy-bees-callshield-ux`. **This is an ownership warning**: do not silently treat CallShield/UCD source as a Bees-branded creative application.
4. `Bzzy` default `main`: placeholder `README.md`, but other legacy feature branches exist.
5. `bzzy-grok` default `main`: placeholder `README.md`; preserve as staging until reviewed.
6. Some branch names and prior audit documents claim planned modules. **A planned branch is not proof of a finished implementation**.

## Proposed interfaces (not yet coded here)

- `bzzy.intake.v0.1`: normalized job/client events with provenance, consent, idempotency and durable outbox.
- `bzzy.leads.v0.1`: Ants lead evidence, certainty, reviewed opportunity score, chosen offer lane and owner/worker routing.
- `bzzy.services.v0.1`: cross-vertical intake/dispatch, approved data fields and customer permissions.
- `bzzy.creative.v0.1`: optional Ants-to-Bees export with explicit asset rights and outbound marketing approval.
- `bzzy.memory.v0.1`: Threadline metadata and provenance API, without writing personal memory directly into shared business data.

None of the above interfaces is claimed as deployed. Name/version conflicts must be reconciled against existing source before adoption.

## Source-first consolidation sequence

1. Inventory every active default and named working branch; record `owner/repo@SHA:path`, language, tests, artifact hashes, status, producer and destination owner.
2. Compare duplicate functionality across Bzzy/BzzySolutions/BzzyAnts/BzzyBees before deciding whether to move it. Do not copy code with unclear license, origin or existing writer.
3. Resolve CallShield/UCD ownership from the existing `BzzyBees` TypeScript package, preserving the current working application until tested in its intended product.
4. Reconcile `BzzyAnts` pipeline, adapters, maps, field-operator and offline outbox branches; report what contains executable code versus placeholders.
5. Promote one verified source tree at a time via review branch + tests + draft PR. Avoid duplicate divergent implementations.
6. Require owner approval before archive/delete, changing a default branch, publicizing private source, production integration or deployment.

## Explicit safeguards

No cross-product monorepo merge was performed by this document. No existing branch, commit, secret, asset, CI workflow or protected configuration was altered. Ownership is an **organizational proposal** pending the source inventory and owner review. The public repo must not contain private inventory, personal records, client secrets or private source URLs.
