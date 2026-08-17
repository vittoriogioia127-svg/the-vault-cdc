# VAULT PITCH BUILD - Code Contract

Deliverable: `the-vault-pitch.html`, a single self-contained presentation file at the repo root. 12 slides,
bilingual, keyboard driven, on the frozen Showroom tokens. The visual draft was produced and validated in
design exploration; this build is the portable runtime that will actually be presented.

## Sources of truth

- Copy and slide structure: `spec/VAULT_PITCH_DECK.md` (v1.1). The English and French copy in that file is
  the copy, word for word, both languages, including the mandatory closing line of slide 10 in both.
- Palette and type: `spec/vault-tokens.css`, inlined into the file. Geist for text, Geist Mono for every
  number, ref, date, tag and counter. Google Fonts load with silent system fallback; the file must work
  offline from file:// and on Live Server.
- Do NOT import or adapt any design-tool HTML export. Rebuild from the contract on the tokens.

## Validated composition notes (match these, they were approved on the draft)

- 01 Cover: mark top left, The Vault massive, subline below, footer bottom left in mono (Colas Rail, MMSP
  EOT001 pilot).
- 02 Problem: headline, body, three quiet cards (Slow, Hard to trace, Financially exposed), footer line
  "The process is the problem, never the people." (FR: "Le probleme est le process, jamais les personnes.").
- 03 Pipeline: three stacked layer cards 01 Source files, 02 Working files, 03 Evidences; the Working files
  card carries the single accent of the slide: an amber dot plus mono tag MANUAL EFFORT (FR: EFFORT
  MANUEL). Footer: "The working layer is human today."
- 04 The Vault: four stage cards with thin arrows (Drop, Extract, Substantiate, Validate), then a Claim
  dossiers band sitting above a Permanent cost register band, footer line per contract.
- 05 Gate: three full-width condition cards, arrow, the single black pill "Complete" fully inside the
  stage, caption line under.
- 06 Granularity: cascade of four stepped chips left (Cost Head A, Category, Cost Element, Staff x Origin
  x Currency x Month), stat block right: 40 large mono with its caption, the 16 / 6 / 18 split line, 39
  large mono with "active on the pilot".
- 07 Traction: headline and body left (40 and 48 inline in mono), a hairline-separated stat rail right
  (40 cost elements, 48 hours).
- 08 Lifecycle: three cards Notice (28 days mono), Versions, Seal, each with its contract line.
- 09 One engine: headline, mono kicker CONFIGURATION OBJECTS PER PROJECT, six chips (taxonomy, owners,
  sources, proof rules, notice periods, disclosure profiles), line "Any Colas project onboards by loading
  its configuration.", MMSP band "first configuration loaded, not a bespoke tool".
- 10 Data horizon: headline and byproduct paragraph left; right list WHAT IT UNLOCKS, six numbered rows,
  each with a right-aligned mono tag (rows 01 to 04: FLAG, rows 05 and 06: REPORT); the mandatory closing
  line spans the bottom, both languages per the contract.
- 11 Governance: headline, three numbered statement rows, the single accent is an amber dot on row 03
  (the cyber gate row).
- 12 Roadmap: two gate cards (Configuration gate: "Substantially closed with the process referent.";
  Mandate gate with amber dot: "This room."), mono kicker THEN THE PHASED BUILD, four phase cards (Core
  workflow, Extraction deepening by stages, Pilot on one cost head, Group onboarding), and the single
  black pill carrying the ask.

## Runtime requirements

- Stage: fixed 16:9 composition (1440 x 810 design space), scaled to fit the viewport, centered, page
  background outside the stage in the bg token. No scrolling inside a slide.
- Navigation: ArrowRight and ArrowLeft; click zones (right third advances, left third goes back); Home and
  End jump to first and last. Current slide counter NN / 12 in mono, top right.
- Language: FR | EN segmented toggle top right, mono, EN default, persisted (localStorage), swaps all copy
  on the current slide set instantly. Numbers, refs, proper nouns identical in both languages.
- Theme: light default, dark toggle token-for-token, persisted. Place the theme control quietly next to
  the language toggle.
- ask variant: a single constant `const ASK_VARIANT = 'A'` near the top of the script; 'B' switches slide
  12's pill and nothing else. Both texts come from the contract.
- Motion: 150ms opacity fade between slides, nothing else moves. prefers-reduced-motion renders cuts with
  no fade.
- No HTML comments inside slide templates. No console errors. No external dependency beyond the fonts.

## Confidentiality

Same rules as the contract: no stack, no AI mention, no effort estimates, no extraction promises beyond
the phased wording, no demo amounts, no dashes other than hyphens in any copy.

## Phase A (read-only, STOP and report)

1. Confirm the repo state: `the-vault-app.html` has no uncommitted changes in the working tree (the P3.0
   sprint must not be mid-Phase-B). This build touches one new file only.
2. Read `spec/VAULT_PITCH_DECK.md` v1.1 fully and confirm both language sets are present for all 12
   slides; flag any slide where FR copy is missing.
3. Present the build plan: slide data structure, render approach, toggle and persistence approach. Flag
   any foreseen collision. STOP and wait for GO.

## Phase B (one additive commit, after GO)

Build `the-vault-pitch.html` exactly per this contract, then run the acceptance checklist and report each
item.

## Acceptance checklist

1. 12 slides navigate forward and backward by keys and click zones; counter correct on every slide;
   Home and End work.
2. FR toggle swaps the full copy on all 12 slides; slide 10 shows its closing line in both languages;
   slide 03's tag reads EFFORT MANUEL in FR.
3. Exactly two black pills exist in the whole deck (slides 05 and 12), never two on one slide.
4. Every number, tag, counter and ref renders in Geist Mono; no gradients, no shadows, no imagery.
5. Dark toggle is token-for-token and persists; light is default.
6. ASK_VARIANT flipped to 'B' changes only the slide 12 pill.
7. Works offline from file:// with system-font fallback; no console errors; reduced-motion shows cuts.
8. `git status` shows exactly one new file; the commit is announced with the new HEAD.
