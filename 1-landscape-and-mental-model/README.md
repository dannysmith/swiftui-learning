# Chapter 1 — Landscape and mental model

## Where we are

Chapter 0 got the Xcode tooling vocabulary in place and we've got `teaching-scaffold-app/` scaffolded as a real project to point at. Now we orient at the **framework level**: what frameworks actually exist on Apple platforms, how they fit together, and the *one* big mental shift Danny needs to make from web development before any of the SwiftUI grammar in chapter 2 will land properly.

This is a short chapter. It's orientation, not deep dive.

## Goal

By the end of this session Danny should be able to:

- Explain in one paragraph what AppKit, SwiftUI, and UIKit are and how they relate
- Articulate the declarative + state-driven shift in his own words, with the HTML/CSS contrast clear
- Know why "what's the macOS equivalent of shadcn/MUI?" is the wrong question on Apple platforms, and stop looking
- Have a rough mental picture of the framework stack his code sits on top of

## Concepts to cover

1. **The three frameworks**
   - **AppKit** — the original, imperative framework from the NeXT era. `NSWindow`, `NSView`, `NSViewController`. Still very much alive on macOS in 2026.
   - **UIKit** — the iOS-side imperative framework. Parallel evolution, separate codebase. Mentioned for completeness; Danny doesn't need it for now.
   - **SwiftUI** — the declarative framework introduced in 2019, layered on top of both AppKit (on macOS) and UIKit (on iOS).
   - Where macOS 26 sits: SwiftUI is the default for new code; AppKit is the foundation it stands on, and the escape hatch when SwiftUI doesn't reach (covered in chapter 13).
   - Diagram-friendly: a layered stack with your app on top.

2. **The declarative + state-driven shift**
   - The headline: **the view is a function of state.**
   - Contrast with HTML/CSS: there, state lives elsewhere (JS variables, server) and you mutate the DOM imperatively. In SwiftUI, you describe what the UI should look like *given* the current state, and the framework figures out what to render.
   - The closer analogy is React: SwiftUI is React-flavoured. But SwiftUI has stronger opinions about state ownership and propagation than React does — full treatment in chapter 3.
   - Why this matters for *decomposition*: when designing a SwiftUI UI you start from "where does the data live?", not "what's the DOM tree?"

3. **Component-library ecosystem (or lack thereof)**
   - There's no shadcn, no MUI, no Chakra, no Ant Design.
   - Apple's frameworks dominate; you compose UIs from primitives.
   - A small ecosystem of helpers exists (Pow for animation, a few SwiftUI utility libraries) but nothing structural — there's no "design system" you'd pull in.
   - **Don't dwell.** This is just closing the question so it stops being a thing Danny wonders about.

4. **The shape of the rest of the course**
   - Briefly map the next few chapters so Danny knows where each piece fits: chapter 2 grammar, chapter 3 state, chapter 4 the app skeleton.
   - The point is to set expectations, not preview content.

## Demos worth considering

- **A Mermaid diagram of the framework stack** is probably the strongest visual aid here — AppKit/UIKit at the bottom, SwiftUI layered on top, your app at the very top. Worth producing.
- **No code demos.** This chapter is conceptual. Reaching for code here would actively obscure the orientation we're trying to install. Resist.
- A side-by-side prose contrast (web/imperative vs SwiftUI/declarative) using a trivial counter example is fine *if* prose alone isn't landing — but try prose first.

## Out of scope (defer)

- SwiftUI grammar — chapter 2
- Property wrappers and state mechanics — chapter 3
- AppKit interop, the seams, when to drop down — chapter 13
- Specific opinions on third-party Swift libraries
- iOS-specific concerns generally

If we drift into any of these, flag it and park.

## Notes

- If Danny is already crisp on the React-style declarative model from web work, the second concept can be brisk — confirm with him early and skip the basics if he's there.
- Don't overplay AppKit's "legacy" status. It's not deprecated; it's the foundation. SwiftUI sits on top of it on macOS. Framing it as "old and bad" would set up wrong expectations for chapter 13.
- Keep it short. Orientation chapters that overrun lose their job.
