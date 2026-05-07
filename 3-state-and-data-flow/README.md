# Chapter 3 — State and data flow

## Where we are

Chapter 2 installed the SwiftUI grammar — `View`, `body`, modifiers, just-enough Swift. The phrase "view is a function of state" came up but wasn't cashed out. This chapter cashes it out. State is the load-bearing concept of SwiftUI, and the most common source of confusion when reading AI-generated code. If this lands cleanly, every later chapter sits on solid ground.

## Goal

By the end of this session Danny should be able to:

- Reason about *where* state should live for a given UI shape
- Pick the right property wrapper (`@State`, `@Binding`, `@Observable`, `@Environment`, `@AppStorage`) for a given data-flow shape
- Articulate "state down, events up" and why it matters
- Recognise the common shapes of state-related bugs in AI-generated code (state in the wrong place, state being recreated on each render)

## Concepts to cover

1. **Why state is special in SwiftUI**
   - Views are recomputed when their state changes
   - The framework owns the lifecycle of state-backing storage; *you* declare the shape
   - This is the part of "view = function of state" that has teeth

2. **`@State` — view-local state**
   - The default for "this view owns this piece of data"
   - Why it must be a `var`, why `private` is conventional
   - The struct-vs-class question lurking underneath (defer details)

3. **`@Binding` — two-way references**
   - How a parent passes mutable state down to a child without giving up ownership
   - The `$value` shorthand
   - The "lift state up" pattern from React, but enforced syntactically

4. **`@Observable` — reference-type shared state**
   - The modern macro for objects shared across views
   - Briefly mention `ObservableObject` / `@Published` — the older pattern Danny will see in older codebases
   - When to reach for this vs `@State`

5. **`@Environment` — implicit context propagation**
   - System-provided values (color scheme, locale, dismiss action)
   - Custom environment values (briefly; full treatment in chapter 8)

6. **`@AppStorage` — UserDefaults bridge**
   - Persisted, simple-typed state across launches
   - Where it fits and where it doesn't

7. **Unidirectional data flow: state down, events up**
   - The mental model that ties the wrappers together
   - Why this is more rigid than React's looser conventions

8. **Common traps**
   - State declared in the wrong view (shared state as `@State` in a child)
   - Accidentally creating new state on every render
   - Treating `@State` as a place to put derived values

## Demos worth considering

- A small "lift state up" demo using `@State` + `@Binding` between parent and child — high value, tactile
- A shared `@Observable` model used by two sibling views — the canonical example
- A Mermaid diagram of state direction (down) and events (up) — strong supporting visual
- A "broken vs fixed" snippet for the "state in the wrong place" trap — only if the prose alone isn't landing
- Probably **not** a dedicated `@Environment` demo — better as part of a larger example

## Out of scope (defer)

- View identity, `.id()`, and how state survives view reidentification — chapter 8
- Custom environment values in any depth — chapter 8
- Combine, async/await, or external state libraries
- Complex derived/computed state patterns

If we drift into any of these, flag it and park.

## Notes

- The React/Redux analogies are tempting but governed by the cross-language-analogies rule in `CLAUDE.md` — only reach for them if the SwiftUI explanation isn't landing on its own.
- `ObservableObject` is the *older* pattern; modern code uses `@Observable`. Lead with `@Observable` and mention the older one only so Danny can read older code.
- This chapter rewards going slow. Better to install the wrappers properly than to rush and have everything afterwards feel slightly off.
