# Chapter 14 — Designing well on macOS

## Where we are

We have every piece of the technical stack — SwiftUI grammar, state, layout, controls, chrome, presentation, motion, escape hatches, AppKit interop. Now: how to use all of it in a way that feels *native* to macOS, rather than like a ported iOS or web app. This chapter is about taste, conventions, and Apple's HIG.

## Goal

By the end of this session Danny should be able to:

- Critique a macOS UI against platform conventions and identify what feels off
- Spec designs that feel native rather than ported from iOS or web
- Pick the right control sizing, density, and colour treatment for a given context
- Know where macOS expectations diverge most sharply from iOS

## Concepts to cover

1. **Apple HIG for macOS 26 essentials**
   - Where to read it; what's load-bearing; what's reference
   - The sections most relevant to building a typical macOS app

2. **Density and conventions**
   - macOS is denser than iOS — more controls, smaller targets, more on screen
   - Why density expectations are different (mouse vs touch)
   - Where the iOS design language actively misleads

3. **Control sizing**
   - `.controlSize` (`.mini`, `.small`, `.regular`, `.large`)
   - When each is appropriate
   - The default sizing across contexts

4. **Semantic colours and dark mode**
   - System colours (`.primary`, `.secondary`, `.accentColor`, etc.)
   - Why hardcoded colours break dark mode
   - The macOS-specific palette concerns (vibrancy, materials)

5. **Accessibility basics**
   - Things that aren't optional: labels, traits, focus order, dynamic type
   - The minimum bar Claude Code-generated code rarely meets without prompting

6. **Where macOS expectations diverge from iOS most sharply**
   - Tabs (already touched in chapter 9)
   - Modal patterns (chapter 10)
   - Toolbar density and placement
   - Right-click / contextual menu expectations
   - Window-level conventions (close, minimise, zoom — not "back" buttons)

## Demos worth considering

- Probably no code demos. This chapter is reference + critique.
- A "before / after" of an iOS-feeling design vs a macOS-feeling design — could be screenshots, diagrams, or even mocked-up prose comparisons. Useful.
- Pointing at concrete Apple HIG sections live (rather than recalling them) is more valuable than building anything.
- A short critique exercise — show a UI, spot what feels wrong, name the convention being violated.

## Out of scope (defer)

- Full accessibility deep dive (deserves its own course; we cover the minimum bar only)
- Localisation
- Visual design at the level of pixel-pushing icons and assets
- Specific competitor-app teardowns

If we drift into any of these, flag it and park.

## Notes

- Apple updates the HIG most years. Point Danny at the *live* document for macOS 26, not at training-data snapshots.
- Density and control sizing is the most-different-from-iOS thing — over-spend time here if anywhere.
- Claude Code defaults to iOS-feeling sizing and density. Almost every generated UI will need a critique pass against macOS conventions.
