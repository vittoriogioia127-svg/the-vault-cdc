# The Vault - Decision & Progress Log

Newest at top. Log every structuring decision. Template at bottom.

## 2026-08-18 - P3.0.1 green and pushed; render architecture defect isolated, P3.0.2 chartered
Vittorio's physical pass on P3.0.1: green on all items, pushed. Two refinements surfaced on check 4, both
symptoms of one cause: the app re-renders the full pane on state change. Opening a dropdown flashes and
resets the view; clicking gap to gap remounts the whole body instead of updating the side panel. Ruled as
micro-corrective P3.0.2 before P3.1, because the extraction journey is architecturally impossible on
full-pane re-renders (ticking counters and staggered rows need surgical DOM updates). P3.0.2, two items,
one commit: dropdowns operate on their own DOM only with targeted dependent-region updates (proofs box);
the gap panel becomes a targeted region with a 150ms fade-in on first open, content crossfade on gap-to-gap
with the central DOM and scroll verifiably preserved, fade-out on close, instant under reduced-motion. The
targeted-update pattern becomes binding app-wide: full-pane re-renders on interaction are now forbidden.
P3.1 prompt amended with one line making the pattern binding for the journey. Check 6 of the P3.0.1 pass
(console across six roles) rides along in the P3.0.2 smoke.

## 2026-08-18 - P3.0.1 delivered (commit bbff1fb); P3.1 extraction journey chartered
The four-item corrective landed as one additive commit on the app file: full-width shell (pane max-widths
removed, reading measure kept on seven prose spans only), contained matrix month headers (40px, 10px mono
secondaries, ellipsis), the period-scoped gap panel (month cells pass ref:month, the panel renders and
derives from the clicked month, non-month contexts default to the current period, amount logic untouched),
and DA dropdowns replacing both native selects (token popover, keyboard complete with wrap-around, refs
and dates in mono). Sanctioned beyond-scope improvement: the attach form's proofs box now follows the
element selection, the config-over-spec principle made visible. Five-item acceptance PASS through the
real-listener harness; the one visually unverifiable point (hover and focus states on the popover) is in
Vittorio's physical pass. Working-tree note from the build: the repo copy of this log sat uncommitted;
rule going forward, the log ships as a separate docs commit alongside each code push, KB and repo carry
the same version.
P3.1 chartered without waiting: VAULT_P3_1_EXTRACTION_JOURNEY.md issued. One thread, drop to muted: the
scripted deterministic scenario (2606_CRPH_Payroll_Local.xlsx, the real file never read), S03 progress and
S04 staggered per-staff filing as states of Home, gate reaction through the validator, the matrix cell
turning complete, gaps 23 to 22. Memory-only journey state, reload resets, sealed periods guarded,
reduced-motion instant. Phase A must propose the exact delta map with every moving tally.

## 2026-08-18 - P3.0 closed green and pushed; four smoke defects triaged into corrective sprint P3.0.1
P3.0 Phase B landed as commit 1d99df0 (one file, +1257/-67): VAULT_CONFIG embedded verbatim with derived
lookups, S20 read-only at #/admin/rules, every ref renumbered to the validated taxonomy, the cockpit
matrix at 39 active rows with the recomputed gap total (23, correct by construction after ruling 3), the
gap panel parameterized by element, owed list, attach form, validator checklist and export reasoning all
config-driven, periods recomputed to /39 preserving story states, real names as config facts only. Build
validated through a Node harness executing the real render path per role after headless Chrome dump-dom
proved unreliable on the build machine. Vittorio's 16-gesture physical pass: green across the board,
pushed.
Four defects surfaced in the smoke, triaged: (1) the main pane carried a max-width centering content on
large screens, a P2.1 inheritance; ruled full-width, The Vault is a data tool, tables and matrix take the
viewport, prose blocks alone keep a reading measure. (2) The enriched sealed month header overflows its
cell; ruled containment, fixed header height, 10px mono secondary line, ellipsis, text-flow only. (3) The
one functional P3.0 bug: the gap panel header always renders the current period regardless of the clicked
month while the amount is month-correct; ruled period pass-through everywhere the panel shows a period.
(4) Native OS selects on S05 break the DA, a pre-existing gap; ruled a token-styled dropdown component
(popover list on surface, hairline, keyboard complete), fixed now rather than P3.2 because P3.1 animates
the drop journey through these controls. Corrective sprint P3.0.1 issued as one targeted prompt, four
items, one additive commit, per the P2 recovery precedent.
Sequencing: P3.1 (living extraction journey) charters immediately after P3.0.1 lands green.
Sharizal thread still open: the one-line relaunch is ready from yesterday if the call never happened.

## 2026-08-17 - the-vault-pitch.html delivered (commit 85bc455): the deck is presentable
Phase B of the pitch build completed on main, one additive file, 626 insertions, tree clean. All eight
acceptance items PASS: navigation with clamping and click zones, 78 i18n keys at exact three-way parity
(markup, EN, FR) so no string can fall back, exactly two black pills in slide content (05, 12), full mono
discipline including inline spans in prose, dark theme value-identical to the frozen tokens with observed
persistence, ASK_VARIANT single-reference, offline file:// with silent font fallback, reduced-motion cuts.
Build quality: four-agent adversarial verification (EN copy, FR copy, mechanics, hygiene) plus headless
renders; one visual defect caught and fixed pre-commit (slide 11 amber dot breaking numeral alignment,
now hanging in the margin) and three hardenings shipped (stage overflow clip, modifier-key guard on
navigation, dead CSS removed). Honest caveat carried: live keyboard and click interaction verified by
code review only; Vittorio's five-gesture physical pass is the closing verification before push via
GitHub Desktop. Two advisories adjudicated with no action: the tokens header comment and the variant-B
ask string are visible in source (contract-sanctioned, no stack or method exposure, the deck is presented
on screen, not distributed as source); LF to CRLF on checkout is cosmetic.
Repo note for traceability: the private internal repository was renamed from eot-7f3a9c to the-vault by
Vittorio; GitHub redirects the old remote, first push to confirm the remote points at the new name.
Awaiting: the physical pass and push, the P3.0 Phase A report, the Sharizal call outcome.

## 2026-08-17 - Pitch deck delivered and validated (12 pages, bilingual); portable build chartered to Code
Design completed the 12-page deck with the v1.1 amendment applied. Audit against the contract: the three
checkpoint fixes verified (slide 10 mandatory closing line verbatim, slide 05 pill whole inside the frame,
slide 01 footer), FR | EN toggle on every page, all numbers from the allowed list, no demo amounts, two
black pills total (05 and 12), never two on one slide. Four derived elements endorsed: the slide 02 triad
and its process-not-people line, the slide 03 amber MANUAL EFFORT tag (label kept over a bare dot: the one
exception of the slide deserves its name), the slide 10 FLAG and REPORT mono tags, the slide 12 askVariant
control. Slide 12 stands on variant A (mandate ask) until said otherwise; switching is one constant.
Rebuild routed to Claude Code per the July precedent (design runtimes are not portable): contract
VAULT_PITCH_BUILD.md issued for the-vault-pitch.html, a single self-contained file at the repo root. Fixed
16:9 stage scaled to viewport, ArrowRight and ArrowLeft plus click zones, mono counter, FR | EN toggle
persisted (EN default), dark toggle token-for-token, ASK_VARIANT constant, 150ms fades with reduced-motion
cuts, offline file://, no design-tool HTML imported, screenshots not fed to the builder. Sequencing rule
restated: one Phase B in flight at a time; the pitch build may commit before P3.0 Phase B since P3.0 sits
at read-only Phase A on a different file.
Awaiting: pitch build Phase A, P3.0 Phase A report, the Sharizal call outcome.

## 2026-08-17 - Pitch deck chartered (Design); in-app guided assistance chartered (D-21, P3.3)
Two workstreams opened after the config gate return, both artifact-first.
1. Stakeholder pitch deck routed to Claude Design (the app stays single-builder with Code per the 14/07
decision; a full page redo in Design was considered and rejected as a fork). Contract VAULT_PITCH_DECK.md:
12 slides on the frozen DA, shareable layer only, structural numbers only. New content: slide 10, the data
horizon, the register as a cost control data foundation (utility invoice variance, duplicate invoices, cost
per staff outliers, evidence aging, cross-project comparison), framed strictly as future capability enabled
by the register with a mandatory closing line, never a pilot deliverable; analytics on HR data explicitly
behind the CDS gate. Candidate D-20: anchor the data horizon in the CDC as a vision section once the slide
is validated. Handoff prompt issued with a 3-slide checkpoint (01, 05, 10) before the full run.
2. D-21: in-app guidance is configuration, not hardcoded copy. Three quiet mechanisms on the frozen DA:
first-run spotlight tour per role (4 to 6 steps, skippable, resumable), an on-demand screen guide panel
behind a "?" affordance (Where you are, What this shows, What you do here, What happens next, role-scoped),
and the existing empty-state doctrine. Tour and guide content live in guideConfig, per project, so another
project onboards its own guidance like its own taxonomy. Contract VAULT_GUIDED_ASSIST.md written with the
full T1 copy seeded (17 screens) and the sprint scope; sequenced as P3.3 after P3.2 because anchors point
at final states and motion. Screen map gains checklist items 12 to 14.
The user-facing requests behind both: a design that respects the rules everywhere, and a tool that explains
itself page by page. The first is P3.0 to P3.2 on the-vault-app.html; the second is P3.3.
Awaiting: Design 3-slide checkpoint, P3.0 Phase A output, the Sharizal call outcome.

## 2026-08-17 - Sharizal returned the substantiation matrix: config gate substantially closed; P3 chartered
Turnaround 48h again (matrix sent 11/08, returned 13/08, Damien in CC on the reply). 40/40 rows verdicted:
32 corrected, 6 OK as is, 2 to discuss (1.1.2 13th Month, 1.1.3 Performance Bonus: monthly internal
provision, only justified in the submission letter, contract-team defensibility to confirm, O-9 dependency).
The Open points tab came back empty, third confirmation of the pattern: pre-filled artifacts return fast,
open questions return blank. Taxonomy gap closed: 1.3.15 Fringe Benefit Tax, 1.3.17 Transport Taxi; Visa,
Training, HDMF evidence and the Pension TODO all resolved in the matrix itself.
Structural findings: D-18 sources are origin-scoped per element with format and multiplicity (1.1.1: Excel
payroll for Local 2 files per month, COrigin, HBased, plus PDF invoices for Mainby quarterly, VIE, Remote),
and element applicability is origin-scoped down to named individuals; D-19 cost recognition frequency
differs from document frequency (accommodation bi-annual invoice costed monthly via subscription form,
Mainby quarterly, insurance annual), so the completeness engine evaluates evidence coverage over a period,
not one document per month. Ownership rewritten: Donnarica Dela Paz (Account) primary source depositor,
Donna Dalida (HR) primary evidence provider, Sharizal owns the computed elements, Jeanette reduced to three
manual elements. Known evidence hole: 1.3.14 IT software requires a notarised CDS invoice that CDS does not
issue; the gate will show it blocked by design. 1.1.1 payslip vs payroll record acceptance pending client
confirmation via the contract team.
KB: 07_VAULT_SUBSTANTIATION_MATRIX.md created (validated config, verbatim, with D-18, D-19 and the residual
call points), 06_VAULT_TAXONOMY.md rewritten (18 Fringe named, ownership map, origins and applicability).
Call with Sharizal set for this afternoon; thank-you mail sent with availability. Working hypotheses H1-H8
logged to proceed without waiting, all reversible config values: H1 six origins with VIE and Remote invoice
substantiated; H2 Colasway ID universal and stable with a temp-ID fallback; H3 FX at the incurrence-month
rate, one canonical source, rate and source stamped per cost; H4 computed elements modeled as returned with
a defensibility flag; H5 IT software rule kept, gap visible; H6 notarisation limited to 1.1.1 and 1.3.14;
H7 1.1.1 evidence as returned with payroll record optional pending client; H8 completeness rules are the
element-level Required sets, no category defaults.
P3 (living mockup) chartered on the-vault-app.html in three sprints: P3.0 real config seed, P3.1 extraction
journey alive (simulated engine, honest phasing unchanged), P3.2 states and motion. P3.0 handoff issued
(VAULT_P3_0_CONFIG_SEED.md, config serialized from the validated return); Phase A includes verifying the
P2.1 merge state before touching anything, since the P2.1 outcome was never logged.
Impacts: config gate ~90% closed, the tool's rulebook is authored by the process referent. Gated: Colasway
ID, FX, origins formalization, notarisation list, provision defensibility (this afternoon's call).

## 2026-08-11 - Substantiation matrix issued to Sharizal; config gate relaunched
Config mail v2 (9 points, 15/07) went unanswered for four weeks. Diagnosis carried over from the July
workbook: Sharizal corrects a pre-filled artifact fast (35/40 in 48h) and stalls on open questions (the 8
open decisions came back empty). An open-question mail was the wrong instrument, twice.
Deliverable: the-vault-substantiation-matrix-staff-cost.xlsx, 3 tabs. Read me (comes from vs proven by, the
three proof attributes, colour code, example row); A - Substantiation matrix (40 rows, one per cost element,
pre-filled with our hypothesis: acquisition mode, source document, depositor, frequency, three proof blocks
each carrying document, required or optional, per staff or per batch, provider, notarisation, plus his
verdict and notes columns, dropdown-constrained); Open points (the 8 non-element questions, the two blank
rows, and three per-category default rules).
Sent with a relance mail proposing a 30 min call, one subject only: what makes a cost complete. Escalation
set: direct contact 17/08, sponsor-level mention to Damien 24/08 if still silent.
Known gap carried: refs 1.3.12 to 1.3.18 were our ordering assumption, two Fringe elements (1.3.15, 1.3.17)
unnamed in our reference, 06_VAULT_TAXONOMY listing only 10 Fringe against the 18 declared in the CDC. To
close against the price file.
Impacts: config gate had a concrete artifact again. Gated at issue time: completeness rules, origins, FX,
per-staff key.

## 2026-07-14 - Substantiation matrix chartered (D-15); Sharizal mail reissued as v2
Clarification forced by Vittorio's own read: source vs evidence was ambiguous. Settled wording: the source is the document the number comes from (feeds the register), the evidence is the document that defends the number (feeds the gate); the same document can play both roles (invoice-based elements), and the two roles can have different owners (Contributions). CDC section 9 rewritten around this.
D-15: substantiation rules live in one per-project matrix, one row per cost element: acquisition mode, source (types and depositor), evidence list with requirement levels (mandatory, alternative group, bonus), granularity (per staff or per batch), provider, attributes (notarization), optional weights, frequency. The gate derives from the mandatory set; bonus evidence feeds a substantiation strength indicator. Editable in admin, Excel-seedable; every downstream surface (owed list, attach form, validator checklist, gap panel, export block) reads from it. S20 (T2) re-specced as the matrix editor. Nothing is hardcoded: taxonomy, owners, modes, evidence rules, frequencies, notice periods and disclosure profiles are all config.
Sharizal mail reissued as v2: question 1 reframed as filling the matrix (required vs optional proofs, per-staff vs per-batch, provider), question 4 aligned, question 8 stripped of the full-names ask (responsibilities only, names retrieved by Vittorio directly).
P2 build decision: Claude Code prompt UNCHANGED. The matrix is a spec and T2 concern; T1 scope is untouched and the sprint in flight is not destabilized. One sprint, one subject.

## 2026-07-14 - Category scheme decided (D-14); config mail issued; process-map screen added; P2 build launched
D-14: the MMSP pilot runs the three price-file categories (Salary, Contribution, Fringe Benefit); category schemes are per-project configuration, extensible without code; the FolderLink nine-way grouping is retained as an ownership view, absorbed by the two owner fields per element.
Precise config mail drafted to Sharizal covering the nine remaining points, each with the options we envision spelled out: completeness rules per category first (with the per-staff vs per-batch question), origins 4 or 6 (VIE, Remote), Colasway ID stability and fallback, the nine manual elements pre-filled (entered from, proven by, entered by), the 1.2.5 HDMF evidence, his two file TODOs (Pension evidence, IT notarization, widened to a per-element notarization attribute), the FX rule (contract-fixed vs incurrence-month vs submission-date), the three names with the source-side vs evidence-side split, and the two blank rows.
S23 process map added to the P2 tier 1 inventory: one screen, both pipelines (register and claim), nodes carrying their owning role, role-highlight tied to the role switcher. Serves department onboarding, the Nicolas presentation, and the contract-team session.
Claude Code prompt issued for the-vault-app.html (T1 scope), same Phase A / Phase B discipline as the demo.

## 2026-07-14 - App mockup P2 chartered; contract-team integration workstream opened
Two additions following the meeting.
1. New workstream: interface with the contract team (Nicolas, Julien, Racim) to explain the process and integrate The Vault with what already runs or deploys on Monday.com. Logged as O-9; Julien added to stakeholders, exact role to confirm. Principle: the claim lifecycle (notice clock, versions, submissions) must land INTO their existing practice, not beside it. This session should happen before the claims screens are frozen in detail.
2. The Nicolas gate needs a complete coherent app mockup: navigation, buttons and icons, views per role, role management, empty loading and success states, motion, one thread. Chartered as P2 via VAULT_APP_SCREEN_MAP.md: global shell (topbar, rail, role switcher), six-role visibility matrix, five journeys, 22-screen inventory in two tiers (T1 for the Nicolas presentation, T2 pre-pilot), states doctrine (empty, loading, success, blocked, sealed, barred, superseded) and motion spec, all on the frozen DA. Numbers and taxonomy reuse the demo contract for cross-artifact consistency.
Routing decision: Claude Code builds P2 (assembly on frozen tokens, portability required for the presentation, one builder avoids forks). Claude Design re-engaged only if a screen family needs fresh visual exploration; none identified.
Sharizal config agenda re-issued in its post-workbook state: category scheme and completeness rules first, origins, per-staff key, source types for the nine manual elements, the 1.2.5 evidence, the file TODOs, the FX candidate, plus role confirmations (Donnarica, Janelle Tumblod, Donna Velo) and the two blank rows (Visa, Training).

## 2026-07-14 - Damien and Sharizal meeting: claim lifecycle upgraded (versioning, notice clock, disclosure profiles)
Session with Damien Prost and Sharizal went well. Three structural requirements came out, integrated into the CDC as D-10 to D-13.
1. Seals supersede, never break. "Unseal" creates the next version of the claim by full duplication (Damien's word: duplicate, "version 2 of claim X"); the sealed version stays immutable and archived. Mandatory reason, author, timestamp, line-level diff between versions. The contemporaneous-record value survives every adjustment; Damien gets the flexibility through the version chain.
2. The notice clock. On the projects here, 28 days from event identification to client notification, or the claim is barred. The Vault tracks the countdown per event, escalates alerts, stores the proof of notice as evidence. The notice period is a per-contract config value. After notice, construction is open-ended per Damien, iterated through versions. Open point O-7: confirm whether contracts impose post-notice deadlines (detailed particulars, interim updates for continuing events), to be checked with Nicolas contract in hand.
3. Disclosure profiles on outputs. Client submissions choose the information level: amounts shown or masked, per-staff detail included or aggregated, evidence attached or referenced. Profiles are config objects; every export traced (who, when, version, profile). Also serves as the HR-data protection mechanism outward.
Product consequence: the claim side gains its own pipeline (Identify, Notify, Build, Submit, Seal or Supersede) alongside the register pipeline. The cockpit gains the notice countdown as a first-class KPI: a missing document costs a line, a missed notice costs the whole claim.
CDC updated: D-10 to D-13, sections 4, 5, 7, 8, 13, 14, P6 scope and exit, O-7 and O-8 added, I-9 snapshot. Demo step 11 already aligned ("corrections create versions, never overwrites"), no demo change required.

## 2026-07-10 - Pitch pivots to a single guided demo flow (16 steps, one key)
Problem raised by Vittorio with the current P1 pages: seven screens exist in Claude Design but there is no journey. No first page, no navigation story, no way to present. Decision: fuse deck and demo into ONE desktop HTML, 16 numbered steps, ArrowRight as the only control, permanent context header (act, role, moment) and step counter. Narrative steps (opening, reframe, pipeline, traction, platform, road, ask, close) interleaved with 7 interface steps re-sequenced from the existing pages (Contributor Home, drop result, validation gate, cockpit, gap drill, claim assembly with blocking hole, seal). DA stays frozen; this is a re-sequencing plus re-seeding, not a redesign.
Critical correction: the mockup screens showed an invented taxonomy (5.2.1.x). The demo is re-seeded with the real Staff Cost structure (A, 1.1 Salary, 1.2 Contribution, 1.3 Fringe Benefit, real element names) so the Cost Controller recognizes his own file in the room. Demo numbers locked for consistency across steps (24 gaps, PHP 38.2M blocked, 1/6 sealed, PHP 421.9M assembled, the Accomodation Rental hole blocking the export).
Deliverables produced: VAULT_DEMO_PITCH_FLOW.md (Design contract, 16 steps fully specified, acceptance checklist), VAULT_PITCH_SCRIPT_FR_EN.md (spoken script, both languages, timing guide). Handoff prompt issued to Claude Design.
Impacts: one artifact to build before Tuesday instead of two; presenter risk collapses (no page choice, no button hunting, no live manipulation). Next: Design build over the weekend, Sharizal call plus dry run Monday, pitch Tuesday.

## 2026-07-10 - Sharizal returned the config workbook: 35/40 confirmed, 3 acquisition modes surfaced
Sharizal filled the reconciliation workbook within 48h. Rows: 35 confirmed; 3 rejected (1.1.2 13th Month and 1.1.3 Performance Bonus are computed in Power Query, not extracted; 1.3.16 IT hardware not applicable, excluded, MMSP config runs 39 active of 40 mapped); 2 blank with notes (1.3.11 Visa, 1.3.18 Training, to close on the call).
Product finding, spec level: three acquisition modes, not one. Extracted (payroll files, bulk of Salary and Contribution), Computed (13th Month, Performance Bonus, formula on extracted base data), Manual entry with evidence attach (9 invoice or claim-based Fringe elements: Phone Bill, Furnitures, Utility, School Fees, Visa, Flight, Expenses Claim, IT software, Training). CDC section 8 gains the three modes. Strengthens the honest phasing: the manual mode is palier A by construction.
Ownership: source owner and evidence owner can differ (Contributions: source Jeannette/Donnarica, evidence Donna Dalida). Config model moves to two owner fields. New contributors surfaced: Donnarica, Janelle Tumblod (Withholding Tax), Donna Velo (Accommodation), exact roles to confirm. Frequency attribute surfaced: monthly, quarterly (School Fees), one-off (Furnitures new joiner).
The 8 open decisions came back empty: they need the live session, not a form. Follow-up mail sent proposing a Monday call with the 8 decisions as the agenda, category scheme and completeness rules first.
Context: GO-gate pitch scheduled Tuesday 2026-07-14. Plan: pitch skeleton validated Friday, Claude Design handoff for the deck over the weekend, Sharizal call plus dry run Monday, pitch Tuesday (deck for the story, P1 mockup live for the feel, shareable CDC HTML as leave-behind).
Impacts: taxonomy 06 to update post-call (modes, dual owners, frequency, 1.3.16 inactive); pitch gains a traction proof point (35/40 validated by the process referent in 48h). Gated: category scheme and completeness rules pending the Monday call.

## 2026-07-07 - Price file ingested, taxonomy A validated to 40 elements, reconciliation sheet issued
Read Sharizal's real price file (PH_MMSP_EOT001 Rev 2, 2026-06-10). Key finding: the 'Cost Structure' sheet already encodes the full A-G taxonomy plus the accepted-source, working-file and evidence mapping per element; 'FolderLink' encodes the department ownership; 'PQMap' and 'Cost Status' encode the extraction plumbing and the per-staff data model (Colasway ID, Origin, Currency, Year, Month). So the config validation is a reconciliation of his own file, not a data re-entry.
Correction: Staff Cost has 40 cost elements (16 Salary + 6 Contribution + 18 Fringe Benefit), not 32. The prior 32 was an over-count on Fringe. Propagated the fix into the two HTML deliverables and added the count to the CDC. Aligned the CDC substantiation examples to the exact file values.
Open points surfaced for the config gate: (1) category scheme mismatch, Cost Structure has 3 categories vs FolderLink 9; (2) 12 elements with no accepted source, 4 with no evidence; (3) embedded TODOs (Pension evidence, IT software notarized, Vehicle Repair with Rafaela); (4) completeness rules per category defined nowhere; (5) 4 vs 6 origins (VIE, Remote appear as manual); (6) canonical FX source among 4 candidates; (7) Colasway ID as the per-staff key.
Deliverable: a pre-filled reconciliation workbook (the-vault-config-validation-staff-cost.xlsx), 3 tabs (Read me, A - Staff Cost with 40 rows to confirm or correct, Open decisions with 8 questions). This is gate 1, ready for the Sharizal session.
Impacts: CDC and HTML corrected, a concrete config-gate artifact exists. Gated: completeness rules and FX source pending Sharizal input.

## 2026-07-07 - CDC v0.3 rendered as deliverables and consolidated into one spec file
Took the detailed CDC and produced two DA-locked (Showroom) HTML deliverables on the frozen tokens. Shareable (bilingual FR/EN, no build secrets): hero stat band (7 cost heads, 40 cost elements, 3-condition gate, 1 engine and N projects), cost-model cascade, completeness-gate visual (black pill = complete), one-engine-many-claims visual, restrained animation (count-up, scroll-reveal, pipeline and gate sequencing, safe under reduced-motion and no-JS). Internal (EN master): all of the above plus the private layer (build approach, extraction paliers A/B/C, 3-layer document pipeline, political framing, confidentiality strategy, effort, operating loop, the two gates, decision-log snapshot) with a permanent INTERNAL do-not-distribute band.
Then consolidated the full specification into a single markdown file, 03_VAULT_CDC.md, that holds Part I (shareable spec) plus Part II (private layer).
KB restructure. Rule set: one file one job. 01 Master = the map, 03 CDC = the spec, 05 Roadmap = the plan and status, 06 Taxonomy = the data, 02 Log = the journal. 03_VAULT_CDC.md supersedes and replaces the former 03_VAULT_CDC_SHAREABLE.md and 04_VAULT_CDC_INTERNAL.md, both removed. The two HTML files live in the repo as distribution artifacts, not as KB context.
Numbers used are structural and defensible only. The cost-element figure was corrected to 40 against the price file (see entry above). No financial hero number was invented.
Impacts: spec consolidated, KB leaner, design unchanged (DA frozen). Unblocked: a clean KB. Next: the config gate (Sharizal validates the A-G taxonomy and the accepted sources) and the GO demo.

## 2026-07-07 - Pivot to extraction engine + group platform
Sharizal shared the real EOT001 price file. Major reframe: The Vault must REPLACE his manual files and Power Query, auto-extracting costs on drop, down to per-staff. Confirmed: completeness gate = Source + Evidence + department validator sign-off. Substantiation sources are configurable and shown. Built as a group tool, config per project. Taxonomy re-based on A-G. CDC bumped to v0.3, roadmap to v2 (extraction becomes a central phased track, config is the critical path, a group-platform phase added). Memory updated.

## 2026-07-04 - Design language frozen (Showroom)
After a 4-family contest (Paper Ledger, Private Vault, trading-floor cockpits, newspaper), Showroom validated: premium minimal, muted = complete, thin numerals, one black pill, light + dark. Foundations page produced, tokens frozen (vault-tokens.css), design language book v1.1. Logo M4 Checksum locked. Five core screens designed (cockpit, ledger + capture, monthly close, claim assembly, seal). Desktop shell mockup P1 built with role switcher (fixed the isolated-screens and missing-switcher gaps, enforced desktop-only).

## Earlier - Discovery and design exploration
CDC v0.2 written (bilingual). Stakeholder alignment email drafted for Nicolas and Damien. Shareable spec published on GitHub Pages with noindex. Direction exploration run in Claude Design across four families before Showroom won.

---

## Log entry template
### DATE - Title
What changed, why, what it impacts (spec, roadmap, design, build), what is now unblocked or gated.
