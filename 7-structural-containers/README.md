# Chapter 7 — Structural containers

## Where we are

We have controls (chapter 6) and layout primitives (chapter 5). Containers organise those controls into recognisable macOS UI patterns — the settings form, the list, the grid. This chapter is the link between "I have buttons" and "I have a real-feeling macOS screen."

## Goal

By the end of this session Danny should be able to:

- Decompose a settings-style or list-style UI into the right container hierarchy
- Pick between `List`, `Form`, `Grid`, `ScrollView`, and lazy variants for a given shape
- Use `Section`, `GroupBox`, and `DisclosureGroup` to add structure within a container

## Concepts to cover

1. **`List`**
   - The workhorse for collections
   - Static rows vs `ForEach`-driven rows
   - Selection state, multi-select
   - List styles on macOS (`.sidebar`, `.inset`, `.bordered`)

2. **`Form` and `Section`**
   - The macOS settings/preferences idiom
   - Sections with headers/footers
   - Form styling differences between iOS and macOS

3. **`ScrollView`**
   - When you need it; when you don't (e.g. `List` already scrolls)
   - Horizontal vs vertical, both axes
   - `ScrollViewReader` mentioned briefly for programmatic scrolling

4. **Lazy stacks**
   - `LazyVStack`, `LazyHStack`
   - When laziness matters (large collections inside `ScrollView`)
   - Vs `List` — when each fits

5. **`Grid` and `LazyVGrid`**
   - Static `Grid` for known cell layouts
   - `LazyVGrid` for dynamic collections
   - Trade-offs between Grid and stacks-of-stacks

6. **`DisclosureGroup` and `GroupBox`**
   - Disclosure for expandable sections
   - `GroupBox` for visual grouping with a title
   - macOS-typical use cases

7. **Composing with the layout primitives from chapter 5**
   - Containers + stacks + frames working together

## Demos worth considering

- A `Form` with multiple `Section`s added to `teaching-scaffold-app/` (likely as the Settings scene from chapter 4) — this is the canonical macOS shape and worth doing properly
- A `List` with selection state — important macOS pattern
- A `LazyVGrid` if it teaches something specific about collections at scale; otherwise skip
- Probably **not** a separate `ScrollView` demo — usually composed with other containers

## Out of scope (defer)

- `NavigationSplitView` (sidebar+content+detail layout) — chapter 9
- Sidebar styling at the navigation level — chapter 9
- Custom `List` row swipe actions, contextual menus — chapter 10/11
- `NSTableView` wrapping for advanced behaviours — chapter 13
- `Table` (the macOS data-table view) — defer or briefly mention

If we drift into any of these, flag it and park.

## Notes

- The macOS Settings/Preferences idiom is very particular — sections, labels, padding all behave differently than they look in iOS code Claude Code might generate. Spend a little extra time here.
- `List` and `Form` overlap conceptually but have different defaults — make the distinction explicit.
