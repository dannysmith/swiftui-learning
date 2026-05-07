# Chapter 15 — Working with Claude Code

## Where we are

End of the course. We've built the full mental model — grammar, state, layout, controls, containers, composition, chrome, presentation, motion, escape hatches, AppKit interop, design taste. This chapter is consolidation: how to actually direct Claude Code (and similar agents) on real macOS UI work, using the vocabulary now installed.

## Goal

By the end of this session Danny should be able to:

- Brief Claude Code on a macOS UI requirement using the right vocabulary
- Recognise the failure modes that come up most often in generated SwiftUI/macOS code
- Verify and iterate on generated code productively
- Understand the (current, April 2026) practical advice on tooling and workflow

## Concepts to cover

1. **Spec'ing UIs in the vocabulary built across the course**
   - From "I want a sidebar with a list and a detail view" to "use `NavigationSplitView` with `.sidebar` style, single-selection driving the detail column, toolbar items in the trailing position…"
   - The level of detail Claude Code actually needs vs over-specifying

2. **What Claude Code is reliably good at**
   - Boilerplate views, conventional layouts, well-trodden patterns
   - Standard SwiftUI components, common modifier chains

3. **What Claude Code is bad at**
   - Window chrome subtleties (transparent titlebars, NSPanel behaviour)
   - View identity bugs (state in the wrong place, list reorders)
   - Over-using `GeometryReader` when `.frame(maxWidth: .infinity)` would do
   - iOS-isms creeping in: bottom tabs, oversized controls, sheet over popover, missing hover states
   - Missing accessibility basics

4. **Verification patterns**
   - What to look for when reading generated code
   - Quick sanity checks: state placement, modifier order, identity, control sizing
   - When to ask for explanation vs when to just rewrite

5. **Iteration patterns**
   - How to push back productively when generated code is wrong
   - When to re-spec vs when to ask for a fix
   - The "show me three options" pattern for ambiguous design decisions

6. **Current (April 2026) practical advice**
   - Model choice considerations
   - Workflow with Xcode Previews + Claude Code
   - Tooling notes that may date — flag explicitly

## Demos worth considering

- A *worked spec example*: take a UI requirement from chapter 9 or 10, spec it as Claude Code would receive it, look at the (real or hypothetical) output, walk through the verification pass. This is the strongest possible consolidation.
- Possibly a side-by-side: a vague spec vs a precise spec, showing how output quality tracks specification quality
- No new SwiftUI demos here — the SwiftUI content is settled. This is workflow.

## Out of scope (defer)

- Other AI coding tools (Cursor, Copilot, Codex CLI, etc.) beyond brief mention
- General prompt engineering theory
- Non-UI work (data layer, networking, build systems)

If we drift into any of these, flag it and park.

## Notes

- This chapter is consolidation, not new material. If Danny feels the earlier chapters didn't fully land, revisit them rather than papering over with workflow tricks.
- The "current advice" section will date fastest of anything in the course — flag this explicitly. The structural points (verification, iteration, what generators are bad at) age slower.
- Bring back examples from earlier chapters where Claude Code's tendencies were flagged (iOS tabs, GeometryReader overuse, missing hover) — this chapter should feel like the threads tying together.
