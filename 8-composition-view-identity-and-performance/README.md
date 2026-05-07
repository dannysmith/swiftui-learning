# Chapter 8 — Composition, view identity, and performance

## Where we are

We have all the pieces — grammar, state, layout, controls, containers. Now: how to build *larger* UIs out of smaller ones, and the subtle traps that cause AI-generated code to look fine but behave wrongly. This is one of the highest-density "AI codes it but it's quietly broken" chapters in the course.

## Goal

By the end of this session Danny should be able to:

- Decompose a complex UI into reusable subviews and know when extraction is worth it
- Explain `@ViewBuilder` at the level needed to read view bodies fluently
- Articulate what *view identity* is in SwiftUI and recognise the bug shapes it produces
- Spot the common performance traps in AI-generated SwiftUI code at a conceptual level

## Concepts to cover

1. **Extracting subviews**
   - When and why — readability, reuse, performance
   - The subtle pitfalls (lifting state inadvertently, breaking identity)

2. **`@ViewBuilder`**
   - What it is conceptually — a result builder that lets you write multi-statement view bodies
   - Why you can't write arbitrary control flow in a view body
   - When to use it on your own functions/properties

3. **Custom view modifiers**
   - The `ViewModifier` protocol
   - When extracting a modifier is worth it (vs a subview, vs a function)

4. **Environment values, deeper**
   - Custom environment keys
   - When env is the right propagation mechanism vs prop-drilling

5. **View identity**
   - How SwiftUI decides whether two views in successive renders are "the same view"
   - Structural identity (position in the view tree) vs explicit identity (`.id(_:)`)
   - Why this matters: state, animation, and lifecycle all depend on identity
   - The subtle bugs that follow when identity is wrong

6. **`.id(_:)` and forcing identity**
   - Forcing a view to be re-created
   - Why this is sometimes the right answer — and often a code smell

7. **Performance traps at a conceptual level**
   - Unnecessary recomputation
   - State in the wrong place causing avoidable invalidation
   - Expensive work in `body`
   - Why these traps especially bite AI-generated code

## Demos worth considering

- A "before / after" subview-extraction example — clear and useful
- A view-identity bug demo: a list reorders, state attaches to the wrong row. **However**, `CLAUDE.md` flags view identity as a concept that diagrams and prose serve better than a runnable demo. Be cautious here — a Mermaid diagram might be stronger than `.swift` code.
- Probably **no** dedicated `@ViewBuilder` demo — its semantics are obscured by code, not revealed. Prose + a single annotated example is better.
- If a perf trap is worth showing, a minimal "expensive-work-in-body" snippet beats anything elaborate.

## Out of scope (defer)

- Custom `Layout` protocol — chapter 12
- Profiling with Instruments in any depth (mention only)
- Combine / async patterns
- `EquatableView`, `_printChanges()`, and other deep optimisation tools

If we drift into any of these, flag it and park.

## Notes

- This chapter has the highest concentration of "AI code looks fine but is wrong" traps. The teaching mode here is *recognition*, not memorisation.
- Resist the demo-bias more aggressively here than elsewhere. View identity in particular is a place where code obscures the concept. Lead with prose and diagrams.
- Connect back to chapter 3 — many "performance" issues are really state-placement issues.
