# The Vault - Cahier des Charges (v0.3)

Internal master specification. The single detailed spec for The Vault.

Contains a shareable layer (Part I, the what and why, safe for stakeholders) and an internal layer (Part II, private, never shared). The distribution artifacts are the two HTML files in the repo (shareable, internal). This file supersedes the former `03_VAULT_CDC_SHAREABLE.md` and `04_VAULT_CDC_INTERNAL.md`, which can be deleted.

## How this file relates to the rest of the KB

One file, one job. No duplication by design.

| File | Job | Holds |
|---|---|---|
| 01_VAULT_MASTER | The map | Orientation, principles in short, current state, index. Read first. |
| 03_VAULT_CDC (this) | The spec | The full functional specification, plus the private build layer. |
| 05_VAULT_ROADMAP | The plan | Live phase status and the two gates. |
| 06_VAULT_TAXONOMY | The data | Cost heads, elements, ownership map, dimensions. |
| 02_VAULT_LOG | The journal | Dated structuring decisions. |

This file references the taxonomy and the roadmap rather than copying them. The Master stays the short map; this file is the long spec. Different resolution, not a duplicate.

---

# PART I - Shareable specification

The problem, the idea, and how The Vault works. Contains no build method, no stack, no politics. This is the layer that can be shown to stakeholders.

## 1. Assumptions and decisions

Every structuring choice is traced here. Validated items are confirmed. Proposed items remain to be validated before build.

| Ref | Decision | Status |
|---|---|---|
| D-1 | Source of truth is an extraction engine. The Vault replaces the working files and the manual queries. Departments drop their sources, the tool extracts and files the costs. | Valid |
| D-2 | The unit of tracking is the cost element, down to per-staff. Each payslip files itself to the right person and element. | Valid |
| D-3 | The taxonomy is the real price file structure: Cost Head A-G, category, cost element (A > 1.1 Salary > 1.1.1 Basic Salary). | Valid |
| D-4 | The green gate = Source deposited AND Evidence on file AND department validator sign-off against the proof. Two levels: department validator, then consolidator. | Valid |
| D-5 | Multi-currency (PHP, EUR, USD) with FX rate and source documented, all amounts also stored in PHP. | Valid |
| D-6 | Accepted sources per cost element are configurable and editable. A cost can be proven by several sources. The Vault shows what each cost is proven by. | Valid |
| D-7 | The Vault is a group platform, configurable per project. Configuration over specification. A-G is the first project loaded, not a hardcode. | Valid |
| D-8 | Visual direction frozen: premium minimal, muted = complete, light and dark. | Valid |
| D-9 | Desktop only, optimized for a wide screen and high volume. | Valid |
| D-10 | A seal is never broken, it is superseded. Reopening a sealed claim creates the next version by full duplication; the sealed version stays immutable and archived. Every unseal carries a mandatory reason, its author, its timestamp and a line-level diff. | Valid |
| D-11 | Claims are versioned objects. Duplication creates version N+1 from any existing version (Damien: "version 2 of claim X"). | Valid |
| D-12 | Contractual events carry a notice deadline: 28 days from identification to client notification on the projects here, configurable per contract. The Vault tracks the countdown, escalates alerts, stores the proof of notice. A lapsed notice marks the event as barred. | Valid |
| D-13 | Client submissions use disclosure profiles: configurable output levels controlling amounts, per-staff detail and evidence inclusion. Every export is traced (who, when, which version, which profile). | Valid |
| D-14 | The category scheme is per-project configuration. The MMSP pilot runs the price file's three categories (Salary, Contribution, Fringe Benefit); a project can define a different scheme and add categories without code. The FolderLink nine-way grouping is an ownership view, absorbed by the two owner fields per element. | Valid |
| D-15 | Substantiation rules live in one per-project matrix, one row per cost element: acquisition mode, source (accepted types and depositor), evidence list with requirement levels (mandatory, alternative group, bonus), granularity (per staff or per batch), provider, attributes (e.g. notarization) and optional weights, frequency. The completeness gate derives from the mandatory set; bonus evidence feeds a substantiation strength indicator. Editable in admin, seedable by Excel import; every downstream surface reads from it. | Valid |

## 2. Context and problem

Colas Rail must substantiate the costs of EOT (Extension of Time) claims on its railway contracts. Recoverable cost heads are defined by the contract and organized as cost heads: A Staff Cost, B Site Establishment, C Transport, D Plant and Equipment, E Contractual Cost, F Warranty and Hedging, G Head Office Overhead.

Today the data is fragmented: each department keeps its own register, in its own format, and the controller extracts the costs by hand with working files and Power Query. When a contractual event occurs and a claim must be built, the costs and their evidence are reassembled in a rush, and gaps surface too late. The result is slow, untraceable work and a financial risk on claims worth hundreds of millions of PHP.

## 3. Objectives and success criteria

Objectives:
- Absorb the deposit of source files by department and extract their costs automatically, down to per-staff.
- File each cost under the right cost head, category and element.
- Tie each cost to its evidence and have the department validate it.
- Keep the register neutral, so any contractual event can be tested and its claimable lines isolated.
- Protect HR data behind strict role-based access.
- Make everything explorable, filterable and exportable, with a read-only access for reporting.

Pilot success criterion: one full period collected end to end on Staff Cost, with automatic extraction and filing, linked evidence, department validation, a completeness roll-up with no holes, and a claim dossier assembled then sealed.

## 4. Scope

| In scope | Deferred | Out of scope |
|---|---|---|
| Source deposit by department. Extraction and filing of costs (Staff Cost first), down to per-staff. Configurable substantiation. Department validation then consolidation. Completeness engine. Claim lifecycle: notice clock, assembly, versioning, disclosure profiles, sealing. Role-based access and HR isolation. Filtered export and BI access. Group configuration model. | Automatic PDF and OCR extraction (invoices, less structured payslips). Cost heads B to G beyond structure. Advanced BI dashboards. Natural-language query agent. | Replace accounting or the ERP. Build the planning variance analysis (provided by the claim team). Mobile use. Direct integration with the Engineer's systems. |

## 5. From tracker to engine

The previous version was a reconciliation layer over the registers. This one replaces them. The working files and the manual pipeline disappear into the tool. The system still separates two objects, but it now produces the content instead of only tracking it.

| Object | Role | Nature |
|---|---|---|
| Cost register | Records everything continuously, extracted from deposited sources, filed by cost head, category, element and person, with period, amount and evidence. | The exhaustive source of truth |
| Claim event | Selects from the register the claimable lines for a given contractual event, each with its eligibility basis. Carries its notice deadline and lives as a chain of versions. | A versioned dossier assembled on top |

This separation gives a permanent register and the per-event logic, without building a parallel accounting.

The claim side has its own lifecycle: Identify the event, Notify the client inside the contractual notice window, Build the claim (versioned), Submit (with a disclosure profile), Seal. A seal is never broken: reopening creates the next version by full duplication, the sealed version stays immutable and archived, and the unseal event is itself recorded with a mandatory reason and a line-level diff.

## 6. The cost model

The taxonomy is the real price file structure, not an assumption. Four levels, four dimensions on Staff Cost.

| Level | Example | Note |
|---|---|---|
| Cost Head | A Staff Cost | A to G. A fully modeled, B to G follow |
| Category | 1.1 Salary | Salary, Contribution, Fringe Benefit |
| Cost Element | 1.1.1 Basic Salary | The unit of completeness |
| Dimensions | Staff x Origin x Currency x Month | Local, HBased, COrigin, Mainby; PHP/EUR/USD; monthly |

The Vault descends to per-staff. The per-person detail that lives in Power Query files today lives in The Vault tomorrow.

Cost Head A (Staff Cost) holds 40 cost elements across three categories: 16 Salary, 6 Contribution, 18 Fringe Benefit. The full list of cost heads, categories, elements, the ownership map and the dimensions is the reference data. See `06_VAULT_TAXONOMY.md`. This section defines the model; the taxonomy file holds the exhaustive content.

## 7. What the solution captures

- Costs: each cost extracted from a source, with its cost head, category, element, period, currency and amount.
- Evidence: one or more documents that prove each cost, per the accepted-source list.
- People: staff tracked individually, to attribute costs per person and manage nominative eligibility.
- Periods: the monthly cycle. A period closes once reviewed, then seals.
- Contractual events: the events that select claimable lines from the register, each with its identification date, its notice deadline, its notification status and the proof of notice.
- Claim versions: the chain of versions per claim, each with its status (draft, sealed, superseded), its author trail and its diff against the parent version.
- Submissions: every export to the client, recording the claim version, the disclosure profile used, the author and the timestamp.
- History: an unalterable trace of every deposit, extraction, edit, validation, unseal and export.

## 8. Workflows

The central gesture is the drop. Around it, the pipeline reads in four stages: Drop, Extract, Substantiate, Validate (the gate).

- Deposit: a contributor opens the current period and drops its files in the categories it owns. The Vault extracts the costs, files them per element and per person, and flags what is still owed. Bulk import (Excel, CSV) is available.
- Validate: the department validator confirms the extracted costs against the evidence. This is the green gate. The consolidator reviews, validates or rejects with a reason. On validation the entry locks and the action is traced. The period locks after its monthly review.
- Notify: when a contractual event is identified, the clock starts. The Vault tracks the notice deadline (28 days on the projects here, configurable per contract), escalates alerts as it approaches, and stores the notification and its proof as evidence. A lapsed notice marks the event as barred.
- Assemble: the consolidator creates a claim on the notified event (window, impacted sections, planning references), selects the eligible lines each with its eligibility basis. A line without proof blocks the export: a claim cannot ship with a hole.
- Version and submit: a sealed claim reopens only by creating its next version, a full duplicate with a mandatory reason and a line-level diff. Each submission uses a disclosure profile controlling what leaves the system: amounts shown or masked, per-staff detail included or aggregated, evidence attached or referenced. Every export is traced.

## 9. The substantiation matrix

Two documents play two different roles around every cost, and the distinction drives the whole engine. The source is the document the number comes from: the engine extracts from it, or the contributor types from it; it feeds the register. The evidence is the document that defends the number in front of an auditor or the Engineer; it feeds the completeness gate. The same document can play both roles (a School Fees invoice is typed from and proves at once; the config then points both roles to the same document and one piece suffices). The two roles can also have different owners: on Contributions, the payroll file is deposited by one person and the BIR filing forms come from another. This is why every element carries two owner fields.

Each project defines its rules in one substantiation matrix, one row per cost element:

| Column | Content |
|---|---|
| Acquisition mode | Extracted, computed, or manual |
| Source | Accepted source document type(s), and who deposits them |
| Evidence list | Each evidence type with: requirement level (mandatory, alternative within a group, or bonus), granularity (per staff or per batch), provider, attributes (e.g. notarization required), and an optional weight |
| Frequency | Monthly, quarterly, one-off |

The completeness gate derives from the matrix: a cost is complete when its source is deposited, every mandatory evidence is on file (plus one option of each alternative group), and the department validation is signed. Bonus evidence never blocks; it feeds a quiet substantiation strength indicator that helps the claim review. The matrix is a per-project configuration object, editable in admin, seedable by Excel import, and every downstream surface reads from it: the contributor's owed list, the attach form, the validator checklist, the gap panel, the claim export block.

Example rows on MMSP, from the price file, to be completed with requirement levels:

| Cost element | Accepted sources (editable) | Typical proof |
|---|---|---|
| 1.1.1 Basic Salary | Audited payroll file (Local, Hbased, Corigin), invoices (Mainby) | Staff payslip, notarized payroll record |
| 1.2.6 Withholding Tax | Audited payroll file (Hbased, Corigin), Payroll summary (Mainby) | BIR Form No. 1601-C, BIR Filing Reference, BIR EFPS Payment System |
| 1.3.6 Accomodation Rental | Admin working file for Subscription Order | Lease Agreement, Invoice |

## 10. The completeness engine

This is the real product. The engine computes a category by period by owner matrix and applies rules. Readability follows a law: what is complete stays quiet, colour marks only the exception.

A cost is complete only when the three conditions are true: the source deposited, the evidence on file per the category rule, and the department validation signed. The engine raises an alert if a condition is missing, if a document fingerprint changed, or if an entry stays unvalidated past the deadline.

The gate, three conditions to one door:
1. Source deposited
2. Evidence on file
3. Validator sign-off
Then: Complete. Complete is a fact, not a document count.

| State | Meaning |
|---|---|
| Complete | Source, evidence and validation in place. Quiet. |
| Partial | A condition missing, an expected document absent. |
| Critical | No evidence, or integrity compromised. |

Completeness rules derive from the substantiation matrix (section 9): per category with element-level overrides, edited by the project admin, never code.

## 11. Stakeholders and roles

| Stakeholder | Responsibility |
|---|---|
| Nicolas Durame, Director Contract Management | Owns the EOT claim strategy, decides what is claimable, defines the contractual events. Business owner. |
| Damien Prost, CFO Asia | Finance sponsor, budget, data confidentiality, headquarters and cyber validation path. |
| Mohd Sharizal Isa, Cost Controller | Runs the EOT cost collection today. Referent for the subject, the completeness rules and the cost list. Moves from manual extractor to validator and assembler. |
| Contributor departments | Account, Human Resource, Cost Control, Admin. Deposit the sources in their scope. |
| Validators | Racim and Simon, validation of costs and resources. |
| Julien, Contract team | Works with Nicolas and Racim on the contract-management process. Exact role to confirm. Interface for the integration mapping with the team's existing tooling (Monday.com). |

## 12. Access and confidentiality

Role-based access. Nominative payroll and staff data are restricted to authorized roles, isolated at the data level and not only on the screen.

| Role | Sees | Can do |
|---|---|---|
| Admin | Everything, plus the project configuration | Manages users, categories, accepted sources, rules, periods. Does not edit the audit history. |
| Contributor | Its categories, its nominative detail if HR | Deposits sources, attaches evidence, submits. |
| Department validator | The extracted costs of its department and their evidence | Validates or rejects extracted costs against the proof. |
| Consolidator | All categories, all nominative detail | Validates, locks periods, assembles claims, seals. |
| Auditor | All entries and evidence, nominative detail | Read only. Monthly review. |
| Reader | Aggregates only, no nominative detail | Reads aggregates and dashboards. |

## 13. Evidence integrity

Each document receives a fingerprint on upload. Any later change is detectable. Retention is write-once: a correction adds a new version, it never overwrites. A recomputed fingerprint that no longer matches raises an integrity alert.

Why it matters: many contracts require contemporaneous records, sometimes kept in a form agreed with the Engineer. The full history proves, in a dispute, that no document was altered or backdated.

Sealing follows the same law. A sealed period or claim version is never edited in place and never unsealed destructively: reopening creates the next version, and the sealed one remains archived with its fingerprint. The unseal event is part of the record: author, timestamp, mandatory reason, and the line-level differences between versions. The contemporaneous value of every sealed snapshot survives every adjustment made after it.

## 14. Reporting, export and BI

- Operational dashboard: completeness by state, running totals by category and period, late owners, claim coverage.
- Filtered export: selection on any metadata (category, period, contributor, source, document type, amount range, status) then CSV or Excel export.
- BI access: a controlled read-only access feeds reporting, away from raw nominative data unless authorized, with pre-built views for frequent cuts.
- Client submissions: disclosure profiles control the level of information in every outbound document (amounts shown or masked, per-staff detail included or aggregated, evidence attached or referenced). Profiles are configuration objects; every export records who, when, which claim version, which profile.

## 15. Security and governance

Compliance runs as a parallel workstream so it does not block design. HR isolation by role, unalterable access history, least privilege. The hosting region is to be confirmed with cyber (a European region is the likely option).

Production with real HR data is gated on cyber sign-off. The pilot can run on test data until then. The cost and resource list is validated by the process referent and the validators.

## 16. A group platform

The Vault is not an MMSP tool. It is a Colas group tool. Any project in the world, with its own cost organization, onboards by loading its configuration and starts tracking. Same engine, same pipeline, same assembly. Only the configuration differs.

## 17. Constraints

- Desktop only, optimized for a wide screen. Thousands of lines: the tool stays performant at that volume.
- Bulk import: Excel or CSV for entries, with a validation preview before integration.
- Multi-currency with FX rate and source documented, all amounts also stored in PHP.
- Accessibility: keyboard accessible, visible focus, reduced motion respected.

## 18. Roadmap

The delivery arc, with the exit criterion that defines done for each phase. Live status and the two gates are tracked in `05_VAULT_ROADMAP.md`. This section defines what each phase must produce; the roadmap file tracks where we are.

| Phase | Content | Exit criterion |
|---|---|---|
| P0 | Lock the taxonomy, accepted sources, completeness rules and RACI. | Process referent plus stakeholders |
| P1 | Validated visual prototype, internal presentation support. | Vittorio validation |
| P2 | Drop, extraction and cost register. | One deposit filed end to end |
| P3 | Secure foundation and access control. | Integrity test |
| P4 | Department validation and consolidation, bulk import. | The three-condition gate |
| P5 | Completeness engine and dashboard. | One hole detected |
| P6 | Claim lifecycle: notice clock, assembly, versioning, disclosure profiles, sealing. | One claim notified, assembled, sealed, then superseded to v2 with full trace |
| P7 | Structured extraction (Excel), then assisted, then documents. | One source extracted with no intervention |
| P8 | Pilot on one cost head, test data. | Full loop validated |
| P9 | Group platform, onboard a second project by configuration. | A project added with no code |

## 19. Open points and dependencies

| Ref | Question | Owner |
|---|---|---|
| O-1 | Cyber validation timing and hosting region. Can the pilot run on real data or must it use test data first. | Damien, cyber |
| O-2 | Validate the full cost and resource list against the contract, confirm the A-G taxonomy. | Nicolas, Sharizal, Racim, Simon |
| O-3 | Confirm the completeness rules and the accepted sources per element. | Sharizal, Racim |
| O-4 | Single source of the FX rate and its documentation. | Finance |
| O-5 | Who is the dedicated monthly auditor. | Nicolas, Damien |
| O-6 | Source and format of the baseline vs impacted planning analysis that feeds the claim events. | Claim team, Racim |
| O-7 | Post-notice deadlines per contract: does a detailed-particulars window exist after the 28-day notice, and are interim updates required for continuing events. The notice clock must track them if they exist. | Nicolas, claim team |
| O-8 | The disclosure profile set: which profiles exist (notice only, interim, full detail), and who approves an outbound export at each level. | Nicolas, Damien |
| O-9 | Map the contract team's existing process and tooling (what runs or deploys on Monday.com) with Nicolas, Julien and Racim: what The Vault integrates with, what it replaces, what coexists. Feeds the claim-lifecycle screens and the Nicolas presentation. | Vittorio, Nicolas, Julien, Racim |

---

# PART II - Internal layer

Private. Never share as-is. How The Vault is built, the honest extraction phasing, the stakeholder politics, and how we work. None of this appears in any stakeholder-facing document or in the shareable HTML.

## I-1. Build approach

Built via Claude Code, prompt-and-paste, with Vittorio as architect-executor by proxy. Stack: React/Vite front, Supabase for auth and database. A standalone HTML mockup (P1) on the frozen tokens first, then a modular build.

Never named in any stakeholder-facing document. The Vault is presented as a tool, not as an AI-built artifact. The stack, the AI-built nature and the phasing strategy stay internal.

## I-2. Extraction, the honest phasing

Auto-extraction from heterogeneous payroll Excel and PDF, down to per-staff, is a real software problem, not magic. The demo and the mockup simulate the full vision (drop to auto-filed). The build earns it by paliers.

| Palier | Scope | Reading |
|---|---|---|
| A | Prove the workflow: structured drop, categorization, department validation, completeness roll-up. Assisted mapping. | The workflow, provable early |
| B | Auto-extract from structured payroll Excel, template-based. | Feasible |
| C | PDF and OCR: invoices, payslips, less structured evidence. | The hardest, a separate effort |

Rule: never promise a universal magic extractor at the GO. The demo shows the vision; the roadmap earns it. Structured Excel is achievable; PDF and OCR are a distinct workstream.

## I-3. The document pipeline, in full

Three real layers from the price file. The Vault absorbs all three. The working-file stage becomes a visible status (Deposited, Extracted, Substantiated), not a manual Excel step. This is the exact thing The Vault removes from Sharizal's daily load.

| Layer | Column | Content |
|---|---|---|
| Source files | col L | Audited payroll file (Local, HBased, COrigin). Excel or PDF. Deposited by departments. |
| Working files | col M | CRPH Payroll Local, queries q_StaffLocal_PHP. Power Query today. The Vault removes this step. |
| Evidences | col N | Payslip, notarized payroll record, BIR 1601-C, lease, invoice. Audit-grade proofs. |

The middle layer does not disappear from the work; it disappears from the person. It becomes a status the engine produces.

## I-4. Political framing

| Actor | Play |
|---|---|
| Nicolas Durame, business owner | Responsibilise him: he decides what is claimable. He owns the contractual events. |
| Damien Prost, finance sponsor | The platform argument is his slide. Reframe from "I built a tool" to "I am launching a group product" that saves manual work across every EOT claim. That needs a real mandate and real resourcing. Do not undersell it. |
| Mohd Sharizal Isa, process referent | Owns the price file, validates the config. Moves from manual extractor to validator and assembler. Frame The Vault as removing his grunt work, not replacing him. |

Keep the build private. Present vision and working flows in the demo; the onboarding and change-management story is a slide, built after the GO.

## I-5. Confidentiality strategy

- Two spec layers: shareable (stakeholders) and internal (this document, the master).
- Data sensitivity: The Vault handles financial and HR/payroll data. Production with real HR data is gated on CDS (cyber) sign-off, a parallel workstream. The pilot can run on test or anonymized data.
- Publishing: shareable docs can be published view-only (GitHub Pages with noindex, or M365 controlled link).
- Never expose: the stack, the AI-built nature, the simulate-while-building strategy, effort estimates, or the politics above.

## I-6. Effort and complexity

| Block | Reading |
|---|---|
| P1 mockup | Assembly on frozen tokens. Low risk, done incrementally. |
| Core build | Workflow, gate, completeness, assembly, seal. The bulk of the work. |
| Extraction engine | The real cost, phased. Structured Excel achievable; PDF/OCR a separate effort. |
| Group config layer | Designed from the start as config objects, industrialized later. |

## I-7. The operating loop

How we work. Vittorio is the architect-executor by proxy; Claude conceives, structures, challenges, and routes.

The cycle: bring a need or a return, decide with one recommendation plus justification, route to the right tool, execute, then loop the return in the order OK / what is wrong / what to verify / next action. Repeat.

Routing:
- Visual, screen, presentation goes to Claude Design. Output is an autonomous prompt plus the .md or .css to attach.
- Build, refactor, script goes to Claude Code, with sprint discipline.
- Doc, spec, analysis, taxonomy, mail goes direct.

Handoff discipline: each Design or Code handoff is an autonomous prompt plus an attached .md contract, in English. Two failed checks on an output means re-paste the prompt, do not patch.

Sprint discipline for Code: Phase A audit read-only (STOP or GO gate), Vittorio validates or corrects, then Phase B one additive commit, smoke test on local Live Server (HTTP 127.0.0.1), merge via GitHub Desktop after full green. One git operation is announced explicitly with a confirmed new HEAD. One sprint is one subject; never mix a text change with a logic change.

## I-8. The two gates that govern everything

- Config gate (critical path): Sharizal validates the taxonomy and the accepted sources from the price file. Nothing downstream is final until validated.
- GO gate (mandate): the stakeholder demo converts the prototype into a mandate. No dev before it.

## I-9. Decision log, snapshot

| Date | Decision |
|---|---|
| 2026-07-14 | Claim lifecycle upgraded with Damien and Sharizal: seals supersede instead of breaking (version chain, mandatory reason, diff trace), 28-day notice clock per event (configurable per contract), disclosure profiles on client submissions. D-10 to D-13. |
| 2026-07-07 | Pivot to extraction engine plus group platform. The Vault must replace Sharizal's manual files and Power Query, auto-extracting on drop down to per-staff. Gate = Source + Evidence + department validator sign-off. Taxonomy re-based on A-G. CDC to v0.3. |
| 2026-07-04 | Design language frozen (Showroom). Tokens frozen, mark M4 Checksum locked, five core screens plus desktop shell P1. |
| Earlier | Discovery, CDC v0.2, direction exploration across four families before Showroom won. |

The full running log lives in `02_VAULT_LOG.md`. This snapshot is a convenience copy.
