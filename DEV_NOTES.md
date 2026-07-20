# DRAW LAB — Dev Notes

Drawing-fundamentals practice app. Single-file `index.html`, no build step.
Live at https://michaelnocito.github.io/draw-lab/. Commits: `DL-#NNN`.

## What it is
Per-lesson photo uploads of the user's own drawings, with AI review against the
lesson's fundamentals (user supplies their own API key — no backend, no server costs).

## Known state
- Core loop (lesson → draw → upload photo → AI review) is live and working.
- No local dev copy exists yet — all edits happen via this repo directly.

## Playtest triage — 2026-07-20 (tracker "Drawlab", 3 inbox notes)

Mike's mobile playtest, triaged one at a time:

1. **Result card pop-up instead of bottom-of-screen — SHIPPED (this build).** Mike: when there's a
   success/failure, pop a card with a close button instead of sending the result to the bottom of the
   screen, so mobile users don't scroll down then back up. Built `showResultCard(lesson, text)` +
   `.rcard*` CSS: when an AI Review completes (both the own-key `aiReview` and coach `aiReviewViaCoach`
   paths) the verdict pops as a centered, dismissible in-viewport card (✕ / Esc / backdrop-tap / "Got it",
   plus "See it with my drawing ↓" to jump to the gallery). `detectVerdict()` adds a ✓ Passes / Keep-going
   chip when the text clearly says so, and returns null when unsure so it never shows a wrong badge. The
   inline gallery copy stays as history. Reduced-motion safe, theme-token styled.
2. **Mobile no-scroll task flow — ROADMAP (research first, high priority, next).** Broader than #1: Mike gets
   bounced to the bottom when starting a challenge and getting it wrong, then has to scroll back up to reach
   the help. Rule he wants: you should be able to complete a task without scrolling; scrolling is only for
   *extra* info. He explicitly asked for research — how do polished mobile learning apps keep the primary
   action + its feedback + help in-viewport (sticky action bar? bottom sheet? single-card step flow?). #1 is
   the first slice (result no longer requires a scroll); the full flow rework is the next build once the
   research is done. (Web-search tool was down at triage time — research is owed before building.)
3. **"Town scene to the basics" drawing exercise — BACKLOG (content).** Mike wants a town-scene basics
   drawing added to Draw Lab (ties to SQL Trail's frontier town art in Module 7). New lesson/exercise —
   scope with the Module 7 "Applied" tier. Parked as a content add, not urgent.

Cross-app note: these are Draw-Lab-only (its own single-file app); no cross-kit/cross-game applicability.

## ROADMAP

Status as of 2026-07-06. No formal roadmap yet — this is the starting structure.

### Done
- [x] Core lesson flow with photo upload + AI review (user's own API key)
- [x] Deployed to GitHub Pages

### Next up (triaged 2026-07-20)
- [ ] **Mobile no-scroll task flow** (HIGH — research first; see Playtest triage 2026-07-20 #2)
- [ ] Town-scene "to the basics" drawing exercise (content; ties to SQL Trail Module 7)

### Backlog (untriaged)
- [ ] Local dev environment / clone workflow
- [ ] Broader lesson library (currently unknown scope — audit existing lessons)
- [ ] Progress tracking / history of past submissions
- [ ] Polish pass on UI/UX

### Ideas / parking lot
- (nothing parked yet)
