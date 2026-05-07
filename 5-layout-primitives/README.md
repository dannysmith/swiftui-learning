# Chapter 5 — Layout primitives

## Where we are

We can describe an app (chapter 4), but the views in it are tiny and unstyled. Now we cover the layout model — *the* part of SwiftUI that web developers find most counter-intuitive, because SwiftUI's size negotiation is meaningfully different from CSS. Get this wrong and everything afterwards feels mysterious.

## Goal

By the end of this session Danny should be able to:

- Predict, for a simple layout, how SwiftUI will size and position the views
- Reason about why `.frame(maxWidth: .infinity)` does what it does (and why `width: 100%` is the wrong analogy)
- Explain the parent-proposes / child-returns negotiation in his own words
- Choose between `VStack`, `HStack`, `ZStack`, and `Spacer` for routine layouts

## Concepts to cover

1. **Stacks: `VStack`, `HStack`, `ZStack`**
   - The everyday workhorses
   - Spacing, alignment parameters
   - When to nest, when to reach for something else

2. **`Spacer`**
   - Greedily consumes available space along the stack's axis
   - Why `Spacer` behaviour can feel surprising at first

3. **`.frame()` and the ideal/min/max sizing model**
   - Fixed `.frame(width:height:)` vs flexible `.frame(min:ideal:max:)`
   - `maxWidth: .infinity` and what it actually means
   - Why this isn't `width: 100%`

4. **`.padding()` and modifier-chain placement**
   - Where in the chain `.padding` sits affects what gets padded
   - Cross-reference modifier-order from chapter 2

5. **Alignment**
   - Stack alignment vs view alignment
   - The `Alignment` type
   - Brief mention of alignment guides (full treatment chapter 12)

6. **The SwiftUI layout protocol — conceptually**
   - Parent proposes a size to its child
   - Child returns the size it wants
   - Parent positions child within itself
   - This single mental model explains most of the surprising behaviour

7. **Where CSS intuition breaks**
   - No flow layout
   - No `display: block` / `display: inline`
   - Sizing isn't unilateral — it's a negotiation

## Demos worth considering

- An interactive HTML widget demonstrating `.frame(min/ideal/max)` sizing as a slider — this is exactly the case `CLAUDE.md`'s visual-aids section flagged. Worth building.
- A side-by-side `.padding().background()` vs `.background().padding()` reminder (cross-ref chapter 2)
- A small `.swift` file with a few stacks demonstrating alignment options
- A "predict the layout, then run it" exercise: prose first, then run

## Out of scope (defer)

- `GeometryReader`, `Canvas`, custom `Layout` protocol, alignment guides in depth — chapter 12
- `List`, `Form`, `ScrollView`, `Grid` — chapter 7
- View identity affecting layout — chapter 8

If we drift into any of these, flag it and park.

## Notes

- This chapter rewards hands-on poking. Don't try to prose-only it — the layout protocol is one of the cases where running and tweaking really does teach something prose can't.
- The HTML/CSS analogy is *most useful* and *most dangerous* in this chapter. Use it where the contrast clarifies; flag where it misleads.
- The single most important takeaway: parent proposes, child returns. If Danny leaves with that, the rest follows.
