# Chapter 13 — AppKit when you need it

## Where we are

We've covered SwiftUI in depth. Now the older, imperative framework underneath: AppKit. This chapter is about *recognition* — knowing what AppKit is, where it surfaces, the seams between it and SwiftUI, and the genuine 2026 cases where SwiftUI alone isn't enough.

## Goal

By the end of this session Danny should be able to:

- Recognise when a UI requirement is going to need AppKit
- Describe the SwiftUI/AppKit seam to Claude Code in the right vocabulary
- Read a basic `NSViewRepresentable` wrapper and understand what it's doing
- Not be surprised when generated code drops to AppKit for a specific reason

## Concepts to cover

1. **What AppKit is**
   - The older, imperative, still-very-much-alive framework underneath
   - `NSWindow`, `NSView`, `NSViewController` — the parallel to SwiftUI's `View` world
   - Tone: not legacy. Foundation + escape hatch.

2. **The seams**
   - `NSViewRepresentable` — wrap an `NSView` so it can sit in a SwiftUI view tree
   - `NSViewControllerRepresentable` — same for an `NSViewController`
   - The bridge between SwiftUI's declarative and AppKit's imperative model

3. **Worked example**
   - Wrapping a small `NSView` (something simple, like a `NSColorWell` or `NSVisualEffectView`)
   - Reading the `makeNSView` / `updateNSView` shape
   - Where coordinator objects fit (briefly)

4. **The genuine 2026 holdouts**
   - True `NSPanel` behaviour (floating, non-activating, HUD windows)
   - Deep window chrome customisation (transparent titlebars, hidden traffic lights, custom toolbars)
   - `NSTextView` for serious text editing (rich attributes, find/replace, language features)
   - Certain advanced table behaviours (`NSTableView`)
   - Custom drag-and-drop at the system level
   - Some accessibility edge cases

5. **Communicating "this needs AppKit" to Claude Code**
   - When briefing a task: how to state the AppKit seam clearly
   - What to expect in return

## Demos worth considering

- A single concrete `NSViewRepresentable` example, showing the wrapping shape end-to-end. One worked example beats five fragmentary ones.
- Maybe a transparent-titlebar `NSWindow` example if it's quick — visible, satisfying, illustrates the "deep chrome customisation" holdout
- Probably no other demos. This chapter is recognition + one solid example.

## Out of scope (defer)

- Full AppKit programming (you don't need to write idiomatic AppKit; you need to recognise it)
- Cocoa runtime internals, Objective-C bridging
- Interface Builder, nibs, Storyboards
- AppKit-specific patterns Claude Code can produce on demand if asked

If we drift into any of these, flag it and park.

## Notes

- Tone matters in this chapter. AppKit is *not* "the bad old way." It's the foundation SwiftUI sits on, and the escape hatch when SwiftUI doesn't reach. Frame it that way.
- The point is recognition, not fluency. Danny doesn't need to write AppKit; he needs to know when it's needed and how to ask for it.
- Apple keeps adding to SwiftUI each year, narrowing the holdout list — flag that the 2026 list is current-as-of-now and may shrink.
