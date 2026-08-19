# VAULT P3.1 - Extraction Journey Contract

Sprint P3.1 of the P3 track. One subject: make the extraction journey alive in `the-vault-app.html`. A
contributor drops a source file, the tool visibly reads it, files costs per staff, and the gate reacts,
through to one element turning complete. The engine is simulated, scripted and deterministic: the demo
simulates the vision, the build earns it by stages. Nothing in this sprint parses a real file.

## The one thread

1. S02 Contributor home: the drop zone accepts a real drag-and-drop and a click-to-pick. Whatever file
   is given, the journey renders the scripted scenario; the UI always shows the scripted filename
   `2606_CRPH_Payroll_Local.xlsx`. The real file is never read.
2. S03 extraction progress (state of Home): upload progress on a hairline bar, then a parsing state with
   the fingerprint line and a live row counter ticking up.
3. S04 extraction result (state of Home): per-staff rows appear with a stagger (40 to 60ms apart, 8 to 12
   rows), filing under their elements; then a result strip: lines, staff, total amount, elements touched.
4. Gate reaction: the touched element-month satisfies its source condition. The owed list row updates,
   the validator queue gains the pending item.
5. S07 validator side-by-side: the new item is validatable; validating it flips the third condition.
6. Cockpit matrix: the element-month cell turns complete (muted), the open-gaps KPI decrements, tallies
   recompute. The thread is over when the room can see muted happen.

## Determinism and reset

- Same scenario, same numbers, every run. Journey state lives in memory only: a page reload resets the
  demo to the seeded state. Nothing about the journey persists to localStorage.
- The journey must be re-runnable within a session only by reloading; no reset button in the UI.

## Scenario delta map (Phase A proposes the exact one)

The journey must coherently move, at minimum: one owed list row (S02), one matrix cell (S01), the open
gaps KPI, the pending validations KPI and queue (S06), and end with one element-month complete. The
natural candidate given the seeded state: the 2026-06 payroll gap on 1.1.1 Basic Salary (currently 1/2)
filing to 2/2, gaps 23 to 22, one pending validation created then cleared. Phase A proposes the exact
delta map with every tally that moves; no tally may end contradicting another.

## Motion rules (binding)

Hairline progress, 150ms opacity fades, the row stagger above, counters that tick. Nothing slides,
springs, bounces or glows. prefers-reduced-motion renders every step as an instant state change with no
stagger and no ticking. DA frozen, tokens only.

## Scope OUT

No real parsing or file reading. No new screens beyond the S03 and S04 states of Home. No changes to
S20, the pitch file, the CDC files or any other file. No global skeleton or empty-state work (P3.2). No
guided assistance (P3.3).

## Phase A (read-only, STOP and report)

1. Map the current drop zone, the S03 and S04 state stubs if any, the validator queue structure and the
   matrix cell state model. List every surface the journey will touch.
2. Propose the exact scenario delta map: element, month, rows, staff names (simulated personas only,
   never real names acting), amounts, and every tally that moves from seeded state to thread end.
3. Flag collisions: tallies that could end inconsistent, the sealed period guard (the journey must be
   impossible on a sealed period), interactions with the period selector.
4. STOP and wait for GO.

## Phase B (one additive commit, after GO)

Build exactly per this contract and the approved delta map, then report the acceptance below.

## Acceptance checklist

1. Drop and click-to-pick both trigger the sequence; the scripted filename always renders; the real file
   is demonstrably never read.
2. The full thread runs: progress, parsing with ticking counter, staggered per-staff rows, result strip
   with internally consistent numbers, owed row updated, queue incremented, validation flips the gate,
   the matrix cell turns muted, gaps KPI decrements.
3. Two consecutive runs (reload between) produce identical numbers at every step.
4. Reload resets to the seeded state; nothing journey-related persists.
5. prefers-reduced-motion renders instant states, no stagger, no ticking.
6. No console errors across the six roles; the journey is unreachable on a sealed period.
7. git diff shows exactly one file; the commit is announced with the new HEAD.
