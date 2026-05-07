# Chapter 11 — Animation, transitions, gestures

## Where we are

We've built static-feeling UIs through chapter 10. Now: motion and interaction. macOS conventions differ meaningfully from iOS — *restraint* is the default, hover states matter, and motion is sparing. This chapter is as much about taste as API.

## Goal

By the end of this session Danny should be able to:

- Specify motion and interaction in macOS-appropriate ways
- Pick between implicit and explicit animation
- Recognise when generated code has overdone motion or applied iOS-feeling animations
- Use hover states correctly (a macOS-specific concern Claude Code often misses)

## Concepts to cover

1. **Implicit animation**
   - `.animation(_:value:)` attached to a view
   - When implicit is the right call

2. **Explicit animation**
   - `withAnimation { ... }` wrapping a state mutation
   - When explicit is the right call (most of the time, on macOS)

3. **Transitions**
   - `.transition(...)` for view appearance/disappearance
   - Custom transitions (briefly)

4. **Animation curves and timing**
   - Default curves; `.easeInOut`, `.spring`, etc.
   - Brief — the names matter more than the syntax

5. **Gestures**
   - Tap, long-press, drag
   - **Hover** — macOS-specific, important, often missed (`.onHover`)
   - Gesture composition briefly

6. **macOS conventions: restraint**
   - Less motion than iOS overall
   - Hover states do work that touch states do on iOS
   - Where motion is appropriate (selection feedback, sheet presentation) and where it isn't

7. **Claude Code's tendencies**
   - Tends to over-animate (carry-over from iOS heuristics)
   - Often skips hover states
   - How to push back

## Demos worth considering

- A small implicit-vs-explicit animation comparison — useful, tactile
- A hover-state demo — high value because it's macOS-specific and underweighted in iOS-trained codebases
- Show a *restrained* example deliberately, contrasted with an overdone version — the taste calibration matters more than the API
- Skip elaborate spring/curve demos unless Danny asks

## Out of scope (defer)

- Lottie / external animation libraries
- Drag-and-drop systems — chapter 13 / advanced
- `Animation` as state, advanced custom animation
- Metal / Canvas animation — chapter 12 (Canvas) and beyond

If we drift into any of these, flag it and park.

## Notes

- macOS HIG conventions matter *more* than the API surface in this chapter. The taste calibration is the load-bearing thing.
- Hover states are not optional on macOS — emphasise this. Claude Code-generated code often forgets them entirely.
- Don't get pulled into spring physics tuning. The point is recognition and restraint.
