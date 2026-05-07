# Chapter 2 — SwiftUI fundamentals

> NOTE: this file was generated as an example. It should be fairly accurate, but it can be changed at will when replanning our syllabus. 

## Where we are

Chapter 1 established the landscape: AppKit, SwiftUI, UIKit, and the headline shift that the view is a function of state. This chapter installs the **core SwiftUI grammar** — enough that Danny can read AI-generated SwiftUI code and reason about its structure. State itself comes in chapter 3; here we're just learning the shape of a SwiftUI view.

## Goal

By the end of this session Danny should be able to:

- Look at any reasonable SwiftUI view definition and parse what it's doing structurally
- Explain what `body` is and why views being *values* (not objects) matters
- Read a chain of modifiers and predict roughly what they do
- Articulate why modifier order matters, with at least one concrete example where reordering changes behaviour
- Read enough Swift syntax to not be thrown by the common patterns that appear in generated SwiftUI code

This is not a Swift language tutorial. We cover only as much syntax as is required to read SwiftUI views fluently.

## Concepts to cover

1. **The `View` protocol and `body`**
   - What it means for a type to "be a view"
   - The `body` property: a computed property returning `some View`
   - Why `body` is called repeatedly and what that implies

2. **Views are values, not objects**
   - SwiftUI views are structs; they're cheap, recreated frequently, and don't have a long-lived identity in the way DOM elements do
   - The framework manages identity behind the scenes (full treatment in chapter 8)
   - Mental model: think of a view definition as a *recipe*, not a *thing*

3. **The modifier model**
   - `.padding()`, `.background()`, `.foregroundStyle()` etc are not properties of the view — they wrap the view in a new view
   - Chained modifiers compose outward
   - **Order matters.** Worked example: `.padding().background(.blue)` vs `.background(.blue).padding()` — show both, explain the difference
   - Why this is the *grammar* of SwiftUI

4. **Just enough Swift syntax**
   - `struct Foo: View { var body: some View { ... } }` — read this fluently
   - Trailing closures: why `VStack { Text("hi") }` works
   - `some View` as an opaque return type — what it means at the level Danny needs
   - Property wrapper syntax (`@State var x = 0`) — the shape only; semantics in chapter 3
   - Computed properties briefly, since `body` is one

5. **Reading a typical SwiftUI view top-to-bottom**
   - Walk through a non-trivial example view definition
   - Name each piece, trace the structure
   - This is the consolidation exercise

## Demos worth considering

- A side-by-side modifier-order demo (`.padding().background()` vs reverse) is a strong candidate — this is exactly the kind of thing prose alone makes harder than it needs to be. Possibly a small `.swift` file or a quick HTML/CSS analogue depending on what feels clearest.
- The "read this view" walkthrough is best as prose with the code inline, not as a runnable demo.
- A demo of *views being values* is probably **not** worth building — it's a conceptual point that prose handles fine. Resist the urge.

## Out of scope (defer)

- State and property wrapper *semantics* — chapter 3
- Layout sizing model — chapter 5
- View identity and performance — chapter 8
- Specific atomic components — chapter 6

If we drift into any of these, flag it and park.

## Notes

This chapter is foundational and the pacing should reflect that. It's better to spend longer here and have the grammar properly installed than to rush and have everything later feel slightly opaque.
