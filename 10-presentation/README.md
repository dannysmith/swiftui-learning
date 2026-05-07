# Chapter 10 — Presentation

## Where we are

Chapter 9 built the persistent app shell. Now: the *modal and transient* layer — sheets, popovers, alerts, contextual menus. The question this chapter answers is "given an interaction, which presentation pattern fits?"

## Goal

By the end of this session Danny should be able to:

- Pick the right presentation style for a given interaction (sheet vs popover vs alert vs new window)
- Implement each pattern in SwiftUI with the right binding
- Recognise where AppKit `NSPanel` is still the answer (full coverage chapter 13)

## Concepts to cover

1. **Sheets**
   - `.sheet(isPresented:)` and `.sheet(item:)`
   - Sizing, dismissal, the macOS-vs-iOS sheet feel

2. **Popovers**
   - `.popover(isPresented:)` and anchoring
   - When a popover is the right call

3. **Alerts**
   - `.alert(...)` for blocking confirmations
   - Title / message / button conventions

4. **Confirmation dialogs**
   - `.confirmationDialog(...)` — destructive actions, "are you sure?"
   - When over `.alert`

5. **Contextual menus**
   - `.contextMenu { ... }`
   - macOS right-click conventions

6. **Inspectors as a presentation pattern**
   - Cross-reference chapter 9 — inspectors are persistent presentation
   - When an inspector beats a sheet

7. **macOS conventions: sheet vs panel vs new window**
   - When each is the platform-correct choice
   - Why getting this wrong makes an app feel "off"

8. **Brief: where `NSPanel` is still required**
   - Floating, non-activating, HUD windows
   - Defer details to chapter 13 — just flag the seam exists

## Demos worth considering

- A sheet containing an editing form — strong canonical example
- A popover anchored to a button — useful and quick
- A right-click contextual menu on a row in `teaching-scaffold-app/`'s list (from chapter 9)
- A decision-tree diagram for "which presentation should I use?" — high value as a reference
- Probably skip dedicated alert/confirmationDialog demos; well-understood and dull

## Out of scope (defer)

- Custom `NSPanel` behaviour and floating windows — chapter 13
- Presentation transitions / animation — chapter 11
- Modal *windows* via the `Window` scene — already touched in chapter 4
- Custom sheet sizing extensions

If we drift into any of these, flag it and park.

## Notes

- The decision of "when sheet, when popover, when window" is more important than the syntax. macOS expectations differ from iOS sharply here.
- Claude Code tends to over-use sheets (iOS muscle memory). Flag this when it comes up.
