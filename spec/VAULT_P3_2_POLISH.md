# VAULT P3.2 - Polish and Consistency Contract

Sprint P3.2 of the P3 track, the polish pass. One subject: finish and unify the app's presentation so it
holds a stakeholder demo end to end. Eight items, all in `the-vault-app.html`, one additive commit. DA
frozen, tokens only. The pitch file and every other file stay untouched. Polish means finishing what
exists: no new features, no new screens beyond the read-only sealed sheet in item 3.

## Items

1. Smooth role and route transitions. The rail and topbar become persistent chrome: they are never
   re-rendered on role or route change, only their active states patch. Every main-view swap (role
   change, route change) crossfades at 150ms instead of hard-swapping. Special case S23: a role change
   while on the process map patches only the chips and highlight states, no view swap at all.
   prefers-reduced-motion renders instant swaps.
2. Role glyphs in the switcher. VIEW AS becomes a vertical list, one row per role: glyph plus label,
   active row in medium weight with the accent treatment consistent with the rail. Six 16px glyphs,
   1.5px stroke, the rail icon language, drawn inline as SVG: Contributor a tray with an entering arrow,
   Validator a check in a frame, Consolidator a 2x2 grid, Auditor a magnifier, Reader an eye, Admin two
   sliders. No filled shapes, no decoration.
3. Sealed periods are consultable. On S09, a sealed period card becomes clickable and opens a read-only
   sealed sheet: the seal banner (sealed date, fingerprint, countersigner), the period's category totals,
   the 39/39 ratio, and a quiet write-once line. No action of any kind on the sheet. Esc or back returns
   to Periods.
4. Favicon. An inline data-URI SVG favicon carrying the M4 mark so the tab is branded and the 404 dies.
5. Seal-history filename. The S10 seal history string moves to the scripted filename
   2606_CRPH_Payroll_Local.xlsx, closing the seam flagged in P3.1 Phase A.
6. Matrix name overflow. Truncated element names in the matrix (Performance Bonus) carry the full name
   on hover via a title attribute. Text-flow only.
7. States completion. Sweep every T1 screen against the states doctrine of the screen map: each screen
   has its empty state (one quiet line, one action where relevant) and its loading skeleton where content
   arrives. No screen may render a blank pane in any reachable state. List in the report which states
   were added.
8. Motion audit. Sweep all transitions against the motion rules: fades are 150ms, holds are allowed,
   nothing exceeds 150ms of animated opacity, nothing slides or springs. Tune the gate-flip schedule if
   its fade exceeds the rule. Report the final timing table.

## Phase A (read-only, STOP and report)

Map each of the eight items to its current code, flag any conflict (especially item 1's interaction with
the render doctrine primitives and the journey timers), propose the crossfade mechanism, and list the
screens missing states for item 7. STOP and wait for GO.

## Phase B (one additive commit, after GO)

Build all eight items, then report an eight-point acceptance mirroring them, including: a role-switch
walk across all six roles with no rail re-render (probe attribute surviving), a route walk with
crossfades, the sealed sheet opened and closed, the favicon visible, the S10 string check, the title
attribute check, the added states list, and the final motion timing table. No console errors across the
six roles, one file in the diff, the new HEAD announced.
