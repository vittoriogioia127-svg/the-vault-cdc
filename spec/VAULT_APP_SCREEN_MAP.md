# VAULT_APP_SCREEN_MAP.md
## Contract - The Vault desktop app mockup (P2)

**Purpose.** One navigable, self-contained desktop mockup of The Vault: real navigation, views per role, every screen of the thread, and the key states, on the frozen design language. It supersedes the P1 shell and becomes the visual reference for the Nicolas presentation and for the build.

**Tiers.**
- Tier 1 (T1): everything needed for the Nicolas gate. Built first.
- Tier 2 (T2): admin editors and the exhaustive state matrix. Built after T1 validation, before the pilot.

**Continuity rule.** Reuse the taxonomy, numbers and fictional people from spec/VAULT_DEMO_PITCH_FLOW.md section 3 (24 open gaps, PHP 38.2M blocked, 1/6 sealed, the Accomodation Rental hole PHP 4,918,220.13, claim total PHP 421,947,223.90, event EOT001 ROW-7 148 days). Every artifact tells the same story.

---

## 1. Global shell (every screen)

- **Topbar**: The Vault mark + name (left); project chip `MMSP EOT001` with a quiet chevron (hints the group platform, opens nothing in T1); period selector `2026-06`; global search field (⌘K affordance, static in T1); alerts bell with a badge when a notice clock is under 7 days; user chip (fictional name, role, initials).
- **Left rail**: sections below. Item = line icon (1.5px stroke, currentColor, 16px) + Geist Mono 11px label. Active = ink; inactive = ink-2. One hairline separator above Admin. Collapsible to icons only.
- **Role switcher (presentation device)**: quiet segmented control pinned at the rail bottom, cycling the six roles. Switching re-renders rail visibility and lands on that role's home. Styled like the CDC topbar segments, never prominent.
- **Routing**: hash routes. `#/process`, `#/cockpit`, `#/home`, `#/home/manual`, `#/queue`, `#/queue/item`, `#/ledger`, `#/periods`, `#/periods/seal`, `#/claims`, `#/claims/eot001`, `#/claims/eot001/build`, `#/claims/eot001/v2`, `#/claims/eot001/submit`, `#/evidence`, `#/reports`, `#/admin/users`, `#/admin/config`. Unknown hash redirects to the role landing. `#/evidence` resolves to a T1 evidence register on the ledger-table DNA; `#/admin/config` resolves to a read-only config summary stub (categories, element count, roles, notice period, FX status).
- **Never show**: AI, stack, effort, internal vocabulary. Fictional people, fictional amounts, real taxonomy.

## 2. Sections and role visibility

| Section | Contributor | Dept validator | Consolidator | Auditor | Reader | Admin |
|---|---|---|---|---|---|---|
| Process map | yes | yes | yes | yes | yes | yes |
| Home (role landing) | Contributor Home | Validation queue | Cockpit | Review home | Dashboard | Config summary |
| Ledger | own categories | own department | all | all (read) | aggregates | all |
| Periods | read own | read own | manage + seal | read | no | read |
| Claims | no | no | full | read | no | read |
| Evidence | own uploads | own department | all | all (read) | no | all |
| Reports | no | no | full | read | aggregates | full |
| Admin | no | no | no | no | no | full |

## 3. The thread: five journeys

- **J1 Contributor month**: Home (owed) -> drop -> extraction progress -> filed result -> manual entry with evidence attach (invoice-mode element) -> everything quiet.
- **J2 Validator gate**: Queue -> open item -> cost vs evidence side by side -> validate -> traced success -> queue shrinks.
- **J3 Consolidator close**: Cockpit -> matrix scan -> gap drill -> request documents -> period checklist -> seal ceremony -> sealed.
- **J4 Claim lifecycle (the Nicolas journey)**: Claims list with notice clocks -> new event identified -> countdown running -> notify flow with proof -> build claim (select lines, eligibility basis) -> export blocked by the hole -> hole resolved -> submission with disclosure profile -> seal -> unseal modal (mandatory reason) -> v2 with line diff -> resubmit.
- **J5 Roles and config**: Users and roles -> assign a role -> HR isolation flag visible -> (T2) taxonomy editor, completeness rules, project onboarding.

Every journey is also legible on one screen: S23, the process map. Each department sees its brick in the edifice and where its gesture feeds the whole.

## 4. Screen inventory

| ID | Screen | Route | Roles | Key content | States in scope | Tier |
|---|---|---|---|---|---|---|
| S23 | Process map | #/process | all | The full process as a flow diagram in the DA: the register pipeline (Drop, Extract, Substantiate, Validate) feeding the completeness engine, the periods and seal, then the claim lifecycle (Identify, Notify, Build, Submit, Seal or Supersede). Nodes carry the owning role as a quiet chip. Selecting a role, or arriving with the role switcher active, highlights that role's nodes and dims the rest. Hairline connectors, no arrows-and-boxes clipart: the CDC pipeline and gate figures are the visual grammar. | full view; role-highlight | T1 |
| S01 | Cockpit | #/cockpit | Consolidator | KPI band (open gaps, pending validations, periods sealed, **nearest notice deadline**), the completeness matrix on the real taxonomy, gap side panel | populated; gap panel open | T1 |
| S02 | Contributor Home, owed | #/home | Contributor | Period open, owed categories with due state, drop zone | owed; empty (first month) | T1 |
| S03 | Extraction progress | #/home (state) | Contributor | File card with fingerprint, mono progress line, counts ticking | loading | T1 |
| S04 | Extraction result | #/home (state) | Contributor | Result strip (612 lines, 58 staff, PHP 11,842,300.14), per-staff preview, rows now quiet | success | T1 |
| S05 | Manual entry | #/home/manual | Contributor | Form for an invoice-mode element (1.3.10 School Fees): fields, evidence attach, accepted-source hint from config | form; attached; submitted | T1 |
| S06 | Validation queue | #/queue | Dept validator | Pending list (14, PHP 18.9M), one row expanded | populated; empty | T1 |
| S07 | Validate side-by-side | #/queue/item | Dept validator | Extracted cost left, evidence right, fingerprint line, Validate pill, trace of a past validation | pending; validated success | T1 |
| S08 | Ledger | #/ledger | all (scoped) | Filterable table (element, period, origin, currency, status), cost drawer with the evidence chain | populated; drawer open | T1 |
| S09 | Periods | #/periods | Consolidator | Six period cards, close checklist on 2026-06, sealed state on 2026-01 | mixed states | T1 |
| S10 | Seal ceremony | #/periods/seal | Consolidator | Fingerprint, countersign, write-once statement, history entries | pre-seal; sealed | T1 |
| S11 | Claims list | #/claims | Consolidator | Events with **notice clocks**: one notified (quiet), one counting (14 days left, amber), one barred (critical, greyed) | mixed; empty (first event) | T1 |
| S12 | Event detail and notify | #/claims/eot001 | Consolidator | Identification date, deadline countdown, notify composer, proof-of-notice upload, status timeline Identify -> Notify -> Build | counting; notified | T1 |
| S13 | Claim workspace | #/claims/eot001/build | Consolidator | Line selection with eligibility basis, assembled total, the blocking hole, export disabled with the message | blocked; resolved | T1 |
| S14 | Version chain and diff | #/claims/eot001/v2 | Consolidator | Version rail (v1 sealed, v2 draft), unseal modal with mandatory reason, line-level diff (added, removed, changed) | modal; diff view | T1 |
| S15 | Submission composer | #/claims/eot001/submit | Consolidator | Disclosure profile picker (Notice only, Interim, Full detail), live preview with amounts masked or shown, export trace line | profile switch; exported | T1 |
| S16 | Users and roles | #/admin/users | Admin | User table, six roles, role assign control, HR-isolation badge on nominative access | populated | T1 |
| S17 | Request documents | #/cockpit (flow) | Consolidator | From the gap panel: compose request, owner pre-filled, sent state | compose; sent | T1 |
| S18 | Reports and export | #/reports | Consolidator, Reader | Filter builder, export formats, the export-trace footnote | populated | T2 (stub in T1) |
| S19 | Taxonomy editor | #/admin/config | Admin | Cost heads, categories, elements, acquisition modes, dual owners, frequency | read; edit | T2 |
| S20 | Substantiation matrix editor | #/admin/rules | Admin | One row per cost element: acquisition mode, source types and depositor, evidence types with requirement level (mandatory, alternative group, bonus), granularity (per staff or per batch), provider, attributes (notarization), optional weights, frequency. Excel import to seed. Every downstream surface reads from this matrix. | read; edit; import | T2 |
| S21 | Project onboarding | #/admin/project | Admin | Load-a-configuration flow, the group-platform screen | wizard | T2 |
| S22 | Audit trail | #/evidence/history | Auditor | The unalterable history: deposits, validations, unseals, exports | populated | T2 |

Landing per role via the switcher: Contributor -> S02, Dept validator -> S06, Consolidator -> S01, Auditor -> S22 stub (T1: read-only ledger), Reader -> aggregates dashboard stub, Admin -> S16.

## 5. States doctrine

- **Empty**: one quiet line (ink-2) + one action. Never an illustration. Example: "No contractual event yet. Identify the first one." with a single pill.
- **Loading**: static skeleton blocks in fill-2, no shimmer, no gradient. Extraction shows a Geist Mono progress line with live counts.
- **Success**: the state itself changes (row goes quiet, chip appears); a small inline check dissolves after 2s. No toasts stacking, no celebration.
- **Blocked**: critical hairline-left banner with the exact reason. The disabled control stays visible; the message explains the door. "Export blocked - 1 line without proof."
- **Sealed**: grey chip with lock glyph, ink-3. Quiet by law.
- **Barred**: critical chip on the event card, the card itself greyed. The strongest state in the app; it is the cost of a missed clock.
- **Superseded**: ink-3 version chip "v1 - superseded"; the version stays consultable, visibly archived.

## 6. Motion spec

- Route changes: 150ms opacity fade.
- Cockpit KPIs: single count-up on first render of the session.
- Validation and seal: 200ms check draw, then static.
- Notice countdown: static number, no ticking animation.
- Nothing springs, slides, bounces or parallaxes. prefers-reduced-motion kills everything.

## 7. Iconography

Line icons, 1.5px stroke, currentColor, 16px, drawn as inline SVG: process (branching flow), cockpit (grid), home (house), queue (check-stack), ledger (rows), periods (calendar), claims (document-clock), evidence (shield), reports (chart), admin (sliders), search (lens), bell (alert), user (circle). No filled icons, no emoji, no third-party icon font.

## 8. Build form

Single self-contained HTML file at the repo root: `the-vault-app.html`. All CSS and JS inline, hash routing, the same Google Fonts loading as the demo with silent system fallback, works from file:// and Live Server. Tokens from spec/vault-tokens.css are the only palette. Desktop 1440-wide composition, no responsive work.

## 9. Acceptance checklist

1. The rail navigates every T1 route; no dead link; active state correct.
2. The role switcher changes rail visibility and landing exactly per the section-2 matrix.
3. J4 walks end to end: list -> event -> notify -> build -> blocked -> resolved -> submit (profile switch visibly masks amounts) -> seal -> unseal modal with mandatory reason -> v2 diff.
4. The notice clocks show the three states (counting amber, notified quiet, barred critical).
5. Real taxonomy everywhere; numbers match the demo contract; no contradictions between screens.
6. Muted = complete on every screen; one black pill max per screen; hairlines only.
7. Empty, loading, success, blocked, sealed, barred, superseded each visible at least once in T1.
8. No AI, stack, effort or internal vocabulary anywhere.
9. Light default, dark toggle token-for-token, both persist.
10. Runs offline from file:// with system-font fallback.
11. The process map shows both pipelines on one screen without scrolling, and the role-highlight follows the role switcher.
