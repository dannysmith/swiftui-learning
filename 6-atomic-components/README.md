# Chapter 6 — Atomic components

## Where we are

We can lay things out (chapter 5). Now the question is *what* we're laying out — the control toolbox. This chapter is breadth: the routinely-used SwiftUI controls, with the variants and modifiers worth recognising. It's a tour, not a deep dive.

## Goal

By the end of this session Danny should be able to:

- Reach for the right control for a given input shape without looking it up
- Recognise common cross-cutting modifiers and what they do
- Know which controls have macOS-specific styling concerns

## Concepts to cover

1. **Text and labels**
   - `Text`, `Label`, `Image`, SF Symbols
   - Styling with `.font`, `.foregroundStyle`
   - Brief mention of the SF Symbols app as a separate tool

2. **Buttons**
   - `Button` and the action/label pattern
   - Built-in button styles (`.borderedProminent`, `.bordered`, `.plain`, etc.)
   - When custom styles make sense

3. **Input controls**
   - `TextField`, `SecureField`, `TextEditor`
   - `Toggle`, `Slider`, `Stepper`
   - `DatePicker`, `ColorPicker`
   - Bindings as the universal input pattern (cross-ref chapter 3)

4. **Selection controls**
   - `Picker` and its styles (segmented, menu, inline)
   - `Menu` for arbitrary action menus
   - When each form is appropriate on macOS specifically

5. **Feedback**
   - `ProgressView` (determinate vs indeterminate)
   - `Link`

6. **Cross-cutting modifiers**
   - `.foregroundStyle`, `.font`, `.help`, `.disabled`, `.controlSize`
   - These apply to almost everything; learn once

## Demos worth considering

- A "control gallery" view added to `teaching-scaffold-app/` — one of every common control in a single scrollable view. Acts as both a reference and a consolidation. Worth building.
- A small `Picker` styles demo if Danny wants to compare the variants side-by-side
- Probably **don't** build a per-control demo — that's reference doc territory; gallery is the better shape

## Out of scope (defer)

- `List`, `Form`, `ScrollView`, `Grid` — chapter 7
- Custom `ButtonStyle` / `ToggleStyle` in depth
- Accessibility labels and traits — chapter 14
- Drag-and-drop on controls — chapter 13 / advanced
- Charts (`Charts` framework)

If we drift into any of these, flag it and park.

## Notes

- This is breadth, not depth. Don't dwell on any single control. Gallery > essay-per-control.
- macOS-specific styling concerns recur — flag where a control's macOS appearance differs from the iOS rendering Claude Code might default to.
- SF Symbols deserves its own brief mention as a *tool* (the SF Symbols.app), separately from the API.
