# VAULT_DEMO_PITCH_FLOW.md
## Contract for Claude Design - The Vault GO-gate guided demo

**What this is.** One single HTML file that carries the entire Tuesday pitch: narrative screens and product interface screens fused into one linear, numbered, keyboard-driven flow. The presenter never chooses a page and never hunts for a button. Right arrow is the only control.

**What this is not.** Not a redesign. The design language is frozen (Showroom). The existing pages (Contributor Home, Ledger, Cockpit Proposals, Claim Assembly, Seal Ceremony) are the DNA: reuse their layouts and components, adapt their states and data as specified below.

---

## 1. Hard rules

- One HTML file. Desktop only. Fixed stage designed for 1440 x 900, centered, `overflow hidden`. No responsive work.
- Design language: Showroom, frozen. Use the attached `vault-tokens.css` as the only source of colors, type, spacing. Geist + Geist Mono. Light mode is the default (projector-safe). No gradients, no glow, no shadows beyond existing tokens.
- Law of the interface: muted = complete. Colour marks only the exception. One black pill maximum per screen.
- All UI copy in English. No French on screens (the spoken script handles languages).
- Never show or mention: AI, the build stack, effort estimates, the word "simulate", internal vocabulary ("palier").
- No live interactions required to progress. Every step is a pre-baked state. Drag-and-drop, clicks, uploads are all represented as already-happened states. Zero manipulation risk during the pitch.
- Fictional people only (A. Cruz, M. Reyes, R. Santos, R. Dizon). Fictional amounts. Real taxonomy (see section 3).

## 2. The demo shell (present on every step)

- Top-left, one line, Geist Mono 11px, ink-2: `ACT II - THE GATE` then a dot then the moment label, e.g. `Day 6 - Staff Cost validator`. On narrative steps, only the act label.
- Bottom-right, Geist Mono 11px, ink-2: step counter `07 / 16`.
- Navigation: ArrowRight / ArrowLeft move forward and back. Click on right third of the screen also advances (for a clicker). No visible next button.
- Transition between steps: instant or 150ms opacity fade. Nothing animated beyond that. Respect prefers-reduced-motion.
- A hidden index: pressing `0` returns to step 01. Nothing else.

## 3. Real taxonomy seeding (critical for credibility)

The interface screens must use the real MMSP Staff Cost structure. The Cost Controller will be in the room; the data must read as his file.

- Cost Head: `A - Staff Cost`. Categories: `1.1 Salary`, `1.2 Contribution`, `1.3 Fringe Benefit`.
- Elements to display (subset, exact names): 1.1.1 Basic Salary, 1.1.2 13th Month, 1.1.4 Per Diem Allowance, 1.1.10 Phone Allowance, 1.2.1 SSS, 1.2.3 PHIC, 1.2.5 HDMF, 1.2.6 Withholding Tax, 1.3.1 Phone Bill, 1.3.4 Medical Insurance, 1.3.6 Accomodation Rental, 1.3.10 School Fees, 1.3.13 Flight, 1.3.14 Expenses Claim, 1.3.17 IT Cost (softwares), 1.3.18 Training.
- Origins where relevant: Local, HBased, COrigin, Mainby. Currencies: PHP, EUR, USD. Periods: 2026-01 to 2026-06.
- Consistent numbers across all steps (do not improvise new ones):
  - Open gaps: 24, PHP 38.2M blocked, oldest 52 days.
  - Pending validations: 14, PHP 18.9M awaiting countersign.
  - Periods sealed: 1 of 6 (2026-01, sealed 30 Jun 2026).
  - The drop (step 06): file `CRPH_Payroll_Local_2026-06.xlsx`, 612 cost lines, 58 staff, PHP 11,842,300.14, June 2026.
  - Claim event: `EOT001 - ROW-7 access restriction - 148 days`, window 2026-01 to 2026-06, assembled total PHP 421,947,223.90.
  - The blocking hole (step 10): 1.3.6 Accomodation Rental, 2026-03, missing Lease Agreement, blocks PHP 4,918,220.13.

## 4. The 16 steps

Narrative steps: one strong line set large (Geist, weight 200, 44 to 56px), a short sub-line in ink-2, generous whitespace, at most one visual element. No bullets on screen; the spoken script carries the argument.

### Step 01 - Cold open (narrative)
Act label: `OPENING`.
Main line: `A claim worth hundreds of millions of pesos.`
Sub-line: `Substantiated by hand, across scattered files.`
Visual: The Vault mark (M4 Checksum), small, centered above the line.

### Step 02 - Today (narrative)
Main line: `Today, the evidence is chased after the fact.`
Sub-line: `Each department keeps its own register. One person consolidates everything by hand. Gaps surface when it is too late.`
Visual: three faded file icons drifting apart (static, hairline style).

### Step 03 - The reframe (narrative)
Main line: `The Vault does not track evidence. It produces the outcome.`
Sub-line: `Departments drop their sources. The engine extracts, files and substantiates every cost.`

### Step 04 - The pipeline (narrative visual)
Main line: `Four steps. One gate.`
Visual: the pipeline `Drop -> Extract -> Substantiate -> Validate`, four nodes, hairline arrows, the fourth node carries a small black pill `gate`. Reuse the CDC pipe styling.

### Step 05 - Contributor Home, period open (interface)
Act label: `ACT I - THE DROP`, moment `Day 5 - Account contributor`.
Reuse: Vault Contributor Home.
State: user chip `A. Cruz - Contributor - Account`. Period `2026-06` open. Her owed categories listed with due state: `1.1 Salary - audited payroll file - owed`, `1.2 Contribution - owed`, plus two quiet rows already complete from last period. A calm drop zone: `Drop source files - registered, hashed and filed automatically`.
Everything muted except the two owed rows (partial amber dot).

### Step 06 - The drop happened (interface)
Same screen, post-drop state.
State: file card `CRPH_Payroll_Local_2026-06.xlsx - registered - fingerprint 8f3a...c41d`. Result strip: `612 cost lines filed - 58 staff - PHP 11,842,300.14 - June 2026`. The two owed rows now show `extracted - awaiting validation` (quiet). A per-staff preview table, 5 rows: staff (fictional initials), element (1.1.1 Basic Salary, 1.1.2 13th Month, 1.2.1 SSS), origin, PHP amount, status `extracted`.
Nothing celebratory. The magic is that the screen is calm.

### Step 07 - The gate (interface)
Act label: `ACT II - THE GATE`, moment `Day 6 - Staff Cost validator`.
Reuse: Ledger or a validation queue layout.
State: user chip `R. Santos - Department validator`. Split view: left, extracted cost `1.1.1 Basic Salary - E. Ramos - Local - 2026-06 - PHP 84,120.00`; right, the evidence `payslip_ramos_2026-06.pdf` preview placeholder with fingerprint line. One black pill `Validate against evidence`. Queue indicator: `14 pending - PHP 18.9M`.
One row below already validated (quiet, timestamped) to show the trace.

### Step 08 - The cockpit (interface)
Act label: `ACT III - THE COCKPIT`, moment `Consolidator - month close`.
Reuse: Vault Cockpit Proposals (the matrix page), reseeded with the real taxonomy.
State: user chip `M. Reyes - Consolidator`. KPI band: `Open gaps 24 - PHP 38.2M blocked`, `Pending validations 14`, `Periods sealed 1/6`. The matrix: rows grouped `1.1 Salary`, `1.2 Contribution`, `1.3 Fringe Benefit` with the elements from section 3; columns 2026-01 to 2026-06 plus Total PHP; cells as `filed/required` counts. Complete cells muted ink-3. Partial cells amber dot. Two critical cells red dot (1.3.6 Accomodation Rental 2026-03, 1.3.13 Flight 2026-05).
Footer line, mono: `Last ledger sync 14:32 - 31,204 entries - entered once, never copied`.

### Step 09 - The gap (interface)
Same cockpit, right panel focused (dim the matrix slightly).
State: gap card `GAP-118 - Critical - 1.3.6 Accomodation Rental - 2026-03 - blocks PHP 4,918,220.13 - open 52 days`. Checklist: `Lease Agreement - missing (red)`, `Proof of payment - missing (red)`, `Invoice INV-7741 - on file (quiet)`. Owner row: `R. Dizon - Admin - since 12 May 2026`. One black pill `Request documents`.

### Step 10 - The claim (interface)
Act label: `ACT IV - THE CLAIM`, moment `Contract Management defines the event`.
Reuse: Vault Claim Assembly.
State: event header `EOT001 - ROW-7 access restriction - 148 days - window 2026-01 to 2026-06`. Selected eligible lines table (6 rows from real elements, each with eligibility basis tag). Assembled total `PHP 421,947,223.90`. One line highlighted critical: `1.3.6 Accomodation Rental - 2026-03 - evidence missing`. The export control is disabled with the message `Export blocked - 1 line without proof. A claim cannot ship with a hole.`
The disabled state IS the message. Do not soften it.

### Step 11 - The seal (interface)
Reuse: Vault Seal Ceremony.
State: `Period 2026-01 - sealed 30 Jun 2026`. Seal card: fingerprint hash, `write-once - corrections create versions, never overwrites`, countersign line `M. Reyes - Consolidator`. Quiet history list: 3 entries (deposit, validation, seal) with timestamps.
Main line above the card: `Sealed. Contemporaneous. Court-ready.`

### Step 12 - Traction (narrative)
Act label: `PROOF`.
Main line: `This is not a concept. It is mapped on the real price file.`
Three stats, the CDC stat-band style: `40 cost elements mapped`, `35 confirmed by the process referent in 48 hours`, `3 acquisition modes identified`.
Sub-line: `Extracted from payroll files. Computed, like 13th Month. Manual with evidence, like invoices. The engine handles all three.`

### Step 13 - The platform (narrative visual)
Main line: `Not an MMSP tool. A Colas group platform.`
Visual: the one-engine hub with orbiting project cards (reuse the CDC engine figure): `MMSP EOT001 - first project loaded`, three dashed `Project - config`.
Sub-line: `Any project onboards by loading its configuration. Same engine. Zero new code.`

### Step 14 - The road (narrative)
Main line: `Three honest horizons.`
Three quiet cards: `H1 - The workflow, proven. Drop, validate, roll up, assemble.` / `H2 - Structured extraction. Payroll Excel, template-based.` / `H3 - Documents. Invoices and payslips, PDF grade.`
Sub-line: `Security runs in parallel: role-based access, HR isolation, evidence integrity, cyber sign-off before real data.`

### Step 15 - The ask (narrative)
Main line: `What this needs to become real.`
Three lines, one per stakeholder, quiet layout: `Contract Management - own the claim strategy and the contractual events.` / `Finance - sponsor the group platform path and open the cyber lane.` / `Cost Control and departments - the pilot: one cost head, one period, test data.`

### Step 16 - Close (narrative)
The Vault mark, centered.
One line: `The evidence should be ready before we need it.`
Nothing else on screen.

## 5. Acceptance checklist (Design output must pass all)

1. One file, opens full-screen, ArrowRight walks 01 to 16 without any other input.
2. Every screen shows the act label and the step counter.
3. All interface screens read as the frozen DA: muted completeness, one black pill max, hairlines, Geist.
4. The taxonomy on screens is the real one (A - Staff Cost, 1.1/1.2/1.3, real element names).
5. The numbers match section 3 exactly and are consistent across steps.
6. No AI, stack, effort, or internal vocabulary anywhere.
7. Light mode default, projector-safe contrast.
8. No step requires a live manipulation to make its point.
