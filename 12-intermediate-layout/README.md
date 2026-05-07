# Chapter 12 — Intermediate layout

## Where we are

Chapter 5 covered the basic layout model. We've used it for many chapters and it's mostly enough. Now: the escape hatches — `GeometryReader`, alignment guides, the `Layout` protocol, `Canvas` — and (importantly) when *not* to reach for them.

## Goal

By the end of this session Danny should be able to:

- Recognise when a layout problem genuinely needs an escape hatch vs when stacks-and-frames will do
- Articulate what `GeometryReader` does, why it's commonly misused, and what to push back on
- Know that `Layout`, alignment guides, and `Canvas` exist, what each is for, and when to consider them

## Concepts to cover

1. **`GeometryReader`**
   - What it does: gives you the size/position of the proposed space
   - Why it's commonly misused (fills available space; breaks parent's sizing expectations)
   - Common patterns where it's correct vs where it's a code smell

2. **Alignment guides**
   - For aligning across stack boundaries
   - When stacks alone can't do what you want

3. **The `Layout` protocol**
   - Custom layouts when stacks are genuinely insufficient
   - High-level only — the goal is recognition

4. **`Canvas`**
   - When you need to *draw* rather than compose views
   - Performance and use-case sketches

5. **Heuristic: most layouts don't need any of this**
   - The signal that you might genuinely need an escape hatch
   - The signal that you've been pushed into one unnecessarily

## Demos worth considering

- A `Canvas` demo — tactile, the only one in this chapter that *adds* to the mental model rather than just naming a thing
- One alignment-guide example showing a cross-stack alignment problem
- **Don't** demo `GeometryReader` heavily. The goal is "recognise it, distrust over-use." A tiny snippet plus prose is enough.
- A `Layout`-protocol demo is probably overkill for this course — name it, point at where to learn more, move on.

## Out of scope (defer)

- Lower-level drawing (Metal, CoreGraphics direct)
- `TimelineView` and time-driven Canvas in depth
- `PreferenceKey` mechanics in any depth
- The full `Layout` protocol API surface

If we drift into any of these, flag it and park.

## Notes

- The most important outcome from this chapter is *skepticism*. Danny should leave able to push back when Claude Code reaches for `GeometryReader` for something a `.frame(maxWidth: .infinity)` would handle.
- This chapter is more "vocabulary + when-not-to" than mastery. Resist the temptation to deep-dive.
