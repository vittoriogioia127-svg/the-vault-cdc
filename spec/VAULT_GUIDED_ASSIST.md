# VAULT GUIDED ASSIST - Contract (D-21)

In-app guidance layer for the-vault-app.html: on every screen, the user can know where they are, what the
screen shows, what they must do, and what happens next. Chartered as sprint P3.3, built after P3.2 because
tour anchors point at final states and motion. This file is both the spec and the future sprint contract.

## Decision D-21

Guidance is configuration, not hardcoded copy. Tour sequences and screen guides live in one config object
(guideConfig), keyed by screen and role, per project. Another Colas project onboards with its own guidance
the same way it loads its own taxonomy. The assist layer amends the global shell of VAULT_APP_SCREEN_MAP.md
with one affordance and adds checklist items 12 to 14 (below).

## The three mechanisms

1. First-run guided tour, per role. On a role's first landing, a short spotlight sequence (4 to 6 steps)
   walks the role's home and primary gesture. Skippable at every step, resumable from the help menu,
   never auto-repeats. Progress in Geist Mono (step 2 / 5).
2. Screen guide panel, on demand. A "?" affordance in the topbar (right of the bell) opens a quiet right
   panel with four fields: Where you are, What this screen shows, What you do here (role-scoped), What
   happens next. Closes on Esc or outside click. Never opens by itself except as the last tour step,
   which points at the "?" so the user knows help persists.
3. Empty-state guidance. Unchanged from the states doctrine: one quiet line, one action.

## DA constraints (binding)

- Spotlight: page under a scrim (ink at 40 percent opacity token), the highlighted element keeps full
  strength with a 1.5px accent ring, radius matching the element. No glow, no pulse.
- Tour card: fill surface, hairline border, max 320px wide, title in Geist 13 medium, body ink-2, two
  quiet text buttons (Skip, Next). The tour CTA is never a black pill: the pill law stays reserved for
  the gate.
- Motion: 150ms opacity fades between steps, nothing slides or springs. prefers-reduced-motion renders
  the ring and card statically with no scrim fade.
- Keyboard: ArrowRight or Enter advances, ArrowLeft goes back, Esc skips. Focus trapped in the card.
- Copy register: UI English, short declaratives, no exclamation marks, no emoji, never "please", never
  marketing tone. The copy below is the copy.

## guideConfig shape

guideConfig = {
  screens: {
    S02: {
      where: "Home / Contributor",
      shows: "...",
      roles: {
        contributor: {
          do: "...",
          next: "...",
          tour: [ { anchor: "css-selector-or-data-guide-id", title: "...", body: "..." } ]
        }
      }
    }
  },
  firstRun: { contributor: ["S02"], validator: ["S06"], consolidator: ["S01"], admin: ["S16"] }
}

Anchors use data-guide attributes added to the DOM, never brittle selectors. State persistence: seen flags
per role in the same local persistence as theme and role.

## Seeded content, T1 screens

The four fields per screen; the "do" line is role-scoped where roles differ. Tour steps marked T.

### S23 Process map
Where: Process. Shows: the whole pipeline on one screen, the register side (Drop, Extract, Substantiate,
Validate) feeding the completeness engine, then the claim side (Identify, Notify, Build, Submit, Seal).
Do: find your role's nodes, they carry your chip; switching role highlights your part. Next: every gesture
you make elsewhere in the app lands on one of these nodes.

### S01 Cockpit (Consolidator)
Where: Cockpit. Shows: the state of the whole period, open gaps, pending validations, sealed periods, and
the nearest notice deadline, over the completeness matrix on the real taxonomy. Do: scan the matrix, colour
marks the exceptions, open a gap to see exactly which document is missing and who owes it. Next: a request
from the gap panel lands with the owner; when the last gap closes, the period can seal.
T1 tour: 1 KPI band (the four numbers that matter today), 2 the matrix (muted is complete, colour is a
gap), 3 the gap panel (from gap to request in one step), 4 the "?" (help stays here).

### S02 Contributor Home
Where: Home. Shows: the open period and what your department owes it, category by category, with due
states. Do: drop your source files on the zone, the tool extracts and files the costs; invoice-based
elements go through Manual entry. Next: extracted costs wait for your department validator; anything still
owed stays listed here.
T1 tour: 1 period selector (you always work inside a period), 2 owed list (what the period expects from
you), 3 drop zone (one gesture, the tool does the filing), 4 manual entry (invoice-based elements enter
here), 5 the "?" (help stays here).

### S03 Extraction progress (state of Home)
Where: Home. Shows: the deposited file being read, fingerprinted, and its lines counted in real time.
Do: nothing, this runs alone. Next: a result strip with the filed lines, per staff.

### S04 Extraction result (state of Home)
Where: Home. Shows: what was just filed, lines, staff, amount, with a per-staff preview. Do: check the
counts feel right; open the ledger for the detail. Next: the rows sit with your validator; your owed list
just shrank.

### S05 Manual entry
Where: Home / Manual entry. Shows: the form for an invoice-based element, with the accepted sources and
required proofs for that element, read from the configuration. Do: fill the fields, attach the evidence
listed as required, submit. Next: the entry joins the validation queue like any extracted cost.

### S06 Validation queue (Dept validator)
Where: Queue. Shows: every extracted or entered cost of your department waiting for your check, newest
first. Do: open an item to compare the cost against its evidence. Next: validated items lock and leave the
queue; the consolidator sees your department turn quiet.
T1 tour: 1 the pending list (your department's gate), 2 one row expanded (amount, element, staff, source),
3 open item (the side-by-side check), 4 the "?" (help stays here).

### S07 Validate side-by-side
Where: Queue / Item. Shows: the extracted cost on the left, its evidence on the right, fingerprint line
under both. Do: confirm the number against the proof, then Validate; reject with a reason if it does not
match. Next: your sign-off is the third gate condition; the cost turns complete and quiet.

### S08 Ledger
Where: Ledger. Shows: every cost in the register, filterable by element, period, origin, currency, status.
Do (contributor): follow your own deposits. Do (validator): audit your department. Do (consolidator,
auditor): trace any cost to its evidence chain in the drawer. Next: this is the source of truth every
claim draws from.

### S09 Periods
Where: Periods. Shows: the monthly cycle, one card per period, the close checklist on the open one, the
sealed ones quiet. Do (consolidator): run the checklist, then seal. Next: a sealed period is write-once;
corrections happen as new versions, never edits.

### S10 Seal ceremony
Where: Periods / Seal. Shows: the fingerprint of the period, the countersign line, the write-once
statement. Do (consolidator): countersign and seal. Next: the period joins history; the register moves to
the next month.

### S11 Claims list
Where: Claims. Shows: every contractual event with its notice clock, counting in amber, notified quiet,
barred critical. Do (consolidator): identify a new event the moment it appears on site, the clock starts
at identification. Next: from here each event runs its lifecycle, notify, build, submit, seal.

### S12 Event detail and notify
Where: Claims / Event. Shows: the identification date, the countdown, the notify composer, the proof of
notice. Do (consolidator): notify the client inside the window and attach the proof. Next: a notified
event unlocks the claim build; a lapsed clock bars it, and barred is final.

### S13 Claim workspace
Where: Claims / Build. Shows: the eligible lines from the register, each with its eligibility basis, the
assembled total, and any blocking hole. Do (consolidator): select lines; a line without proof blocks the
export, resolve it or drop it. Next: a complete dossier moves to submission.

### S14 Version chain and diff
Where: Claims / Versions. Shows: the version rail, sealed versions immutable, the line-level diff between
versions. Do (consolidator): to change a sealed claim, create the next version with a mandatory reason.
Next: the chain is the audit story; nothing sealed ever changes.

### S15 Submission composer
Where: Claims / Submit. Shows: the disclosure profiles, Notice only, Interim, Full detail, with a live
preview masking or showing amounts. Do (consolidator): pick the profile agreed for this submission, check
the preview, export. Next: every export is traced, version, profile, author, time.

### S16 Users and roles (Admin)
Where: Admin / Users. Shows: who holds which of the six roles, and the HR isolation badge on nominative
access. Do (admin): assign roles; least privilege by default. Next: role visibility drives everything
each person sees, screen by screen.
T1 tour: 1 the role column (six roles, one door each), 2 HR isolation badge (nominative data stays behind
it), 3 the "?" (help stays here).

### S17 Request documents
Where: Cockpit / Request. Shows: the request composer, owner pre-filled from the gap. Do (consolidator):
send; the wording stays factual, the gap does the arguing. Next: the owner sees it land on their Home as
owed.

## Sprint P3.3 scope

IN: the guideConfig object with the content above; the "?" affordance and panel; the first-run tours for
the four roles listed; data-guide anchors on the referenced elements; persistence of seen flags; keyboard
and reduced-motion behavior; checklist below.
OUT: T2 screens content (S18 to S22, written at T2), any copy invention beyond this file, any visual token
work, any change to the pitch demo file.

## Acceptance checklist (appends to the screen map as items 12 to 14)

12. The "?" opens the guide panel on every T1 screen, with the four fields, role-scoped, Esc closes.
13. Each of the four first-run tours plays once per role, skippable, resumable, keyboard-complete, and
    never replays uninvited; reduced-motion renders static.
14. Every guide string renders from guideConfig; deleting a screen's entry removes its guidance without
    breaking the screen.
