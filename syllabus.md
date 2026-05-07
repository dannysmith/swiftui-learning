# Syllabus: Building macOS UIs with SwiftUI (and AI tooling)

A learning path for an experienced web developer building macOS apps via Claude Code, focused on installing the **mental models** needed to imagine, decompose, and communicate UI designs — not on becoming a Swift programmer.

The reference platform throughout is **macOS 26 (2026)**. iOS is mentioned only where it differs meaningfully.

## How this syllabus is shaped

The chapter order isn't arbitrary — two deliberate choices shaped it:

1. **State comes early (chapter 3).** SwiftUI is fundamentally state-driven, and *view-as-function-of-state* is the single biggest mental shift from web development. Skip it and the rest of the course doesn't hang together. State sits before windows, layout, or controls.
2. **Basic layout precedes atoms (chapter 5 before chapter 6).** Web instincts say "smallest units first" — but SwiftUI has no default flow like HTML; you can't render two buttons without a stack. So layout primitives come before the control toolbox; the heavier escape-hatches (`GeometryReader`, custom `Layout`, `Canvas`) are deferred to chapter 12.

Otherwise the spine is what you'd expect: tooling → landscape → fundamentals → state → app skeleton → layout → atoms → containers → composition → chrome → presentation → motion → escape hatches → AppKit → design → directing AI.

Per-chapter `README.md` briefs are starting frames, not contracts — each session can adapt them.

---

## Chapter 0 — Apple/Xcode primer

**Goal:** install enough scaffolding that the rest of the course doesn't trip on unfamiliar tooling vocabulary. The web equivalent is "what's a browser, what's a server, what's an HTTP request" — except Danny already knows what a macOS app *is*, so the gap is specifically about Apple's project structure and tooling.

**Key concepts:**
- What an Xcode project is: `.xcodeproj`, `.xcworkspace`, `.swiftpm`
- Typical file structure of a SwiftUI macOS app
- Xcode's panes: navigator, editor, inspectors, canvas
- Schemes and build configurations (at "what is this" level)
- Previews and the live canvas — what they are, why they change how you work
- Running the app on Mac
- Signing and entitlements briefly, so the words aren't scary later
- Apple's WWDC "Tour of Xcode" sessions as supplementary viewing

**Outcome:** scaffold `teaching-scaffold-app/` as a minimal "hello world" macOS app and look around it together. From here on, Danny has a real project to point at when discussing concepts.

---

## Chapter 1 — Landscape and mental model

**Goal:** orient. Establish what the major frameworks are, where each fits, and what the headline shift is from web development.

**Key concepts:**
- AppKit vs SwiftUI vs UIKit — what each is, where each is used, where macOS 26 sits
- The declarative + state-driven shift: *the view is a function of state*, contrasted with HTML/CSS where state lives elsewhere and the DOM is mutated
- Why this shift matters for how you decompose UIs
- Component-library ecosystem: there isn't one. Apple's frameworks dominate; you compose from primitives. Move on.

**Outcome:** Danny can explain the relationship between AppKit and SwiftUI in one paragraph, and can articulate the core mental shift from web UI work.

---

## Chapter 2 — SwiftUI fundamentals

**Goal:** install the core SwiftUI grammar — enough to read AI-generated SwiftUI code and reason about its structure.

**Key concepts:**
- The `View` protocol and the `body` property
- Views are values (structs), not objects; they're cheap and recreated frequently
- The modifier model: views, view modifiers, and how chained modifiers compose. **Order matters** — this is the grammar
- Just enough Swift syntax: structs, trailing closures, `some View`, basic property wrapper syntax
- How to read a typical SwiftUI view definition top-to-bottom

**Outcome:** Danny can look at a SwiftUI view definition and parse what it's doing structurally, even if he doesn't know every modifier by name.

---

## Chapter 3 — State and data flow

**Goal:** install the model of how data moves through a SwiftUI view tree. This is the single biggest mental shift from web development and the most common source of confusion when reading AI-generated code.

**Key concepts:**
- Why state is special in SwiftUI: views are recomputed when state changes
- `@State` — view-local state
- `@Binding` — two-way references passed down the tree
- `@Observable` (and the older `ObservableObject` for context) — reference-type state shared across views
- `@Environment` — implicit context propagation
- `@AppStorage` — bridge to user defaults
- Unidirectional data flow: state down, events up
- Common traps: state in the wrong place, accidentally creating new state on each render

**Outcome:** Danny can reason about where state should live for a given UI and can identify the right property wrapper for a given data-flow shape.

---

## Chapter 4 — The macOS app skeleton

**Goal:** understand what an actual macOS app *is* in SwiftUI terms — the top-level structure, windows, scenes, and how the app starts.

**Key concepts:**
- The `App` protocol and the `@main` entry point
- `Scene` and what scenes are for
- `WindowGroup` vs `Window` vs `Settings` — when each applies
- Multi-window apps and macOS-specific window behaviours
- App-level menus and the menu bar
- How an app actually launches and what the framework does on your behalf

**Outcome:** Danny can describe the structure of a macOS app from `@main` down to the first view, and can reason about when to use which scene type. Begin accreting into `teaching-scaffold-app/`.

---

## Chapter 5 — Layout primitives

**Goal:** install the SwiftUI layout model — which is meaningfully different from CSS and easy to get wrong without the right mental picture.

**Key concepts:**
- Stacks: `VStack`, `HStack`, `ZStack` — the everyday workhorses
- `Spacer` and how it greedily consumes space
- `.frame()` and the ideal/min/max sizing model
- `.padding()` and where it sits in the modifier chain
- Alignment: stack alignment, view alignment, the `Alignment` type
- The SwiftUI layout protocol at a conceptual level: parent proposes a size, child returns a size, parent positions child
- Why this is different from CSS and where the intuition breaks

**Outcome:** Danny can predict, for a simple layout, how SwiftUI will size and position the views. Can reason about why `.frame(maxWidth: .infinity)` does what it does.

---

## Chapter 6 — Atomic components

**Goal:** know the toolbox. Every routinely-used SwiftUI control, with the variants and modifiers worth knowing.

**Key concepts:**
- Text and labels: `Text`, `Label`, `Image`, SF Symbols
- Buttons: `Button`, button styles, common modifier patterns
- Input controls: `TextField`, `SecureField`, `TextEditor`, `Toggle`, `Slider`, `Stepper`, `DatePicker`, `ColorPicker`
- Selection: `Picker` and its styles, `Menu`
- Feedback: `ProgressView`, `Link`
- Cross-cutting modifiers: `.foregroundStyle`, `.font`, `.help`, `.disabled`, `.controlSize`

**Outcome:** Danny has a working vocabulary of controls and can pick the right one for a given input shape without looking it up.

---

## Chapter 7 — Structural containers

**Goal:** know the building blocks for organising controls into recognisable macOS UI patterns.

**Key concepts:**
- `List` — the workhorse for collections
- `Form` and `Section` — the macOS settings/preferences idiom
- `ScrollView` — when you need it, when you don't
- Lazy stacks: `LazyVStack`, `LazyHStack` — when they matter
- `Grid` and `LazyVGrid` — when each applies
- `DisclosureGroup`, `GroupBox` — disclosure and visual grouping
- How these compose with the layout primitives from chapter 5

**Outcome:** Danny can decompose a settings-style or list-style UI into the right container hierarchy.

---

## Chapter 8 — Composition, view identity, and performance

**Goal:** understand how to build larger UIs by composing smaller ones, and the subtle traps that cause AI-generated code to be "working but wrong."

**Key concepts:**
- Extracting subviews and when to do it
- `@ViewBuilder` — what it is, how it shapes what you can write inside view bodies
- Custom view modifiers — when they're worth it
- Environment values — passing context implicitly
- View identity: how SwiftUI decides whether two views in different renders are "the same view." This is the source of many subtle bugs
- `id()`, `.id(_:)` and forcing identity
- Performance traps at a conceptual level: unnecessary recomputation, state in the wrong place, expensive work in `body`
- Why these traps matter especially for AI-generated code

**Outcome:** Danny can decompose a complex UI into reusable subviews, and can recognise the shape of view-identity and performance bugs when they appear.

---

## Chapter 9 — Window chrome and navigation

**Goal:** master the macOS-specific UI structures: the things that make a macOS app *look* like a macOS app.

**Key concepts:**
- `NavigationSplitView` — the canonical macOS sidebar+content+detail pattern
- Toolbars: `ToolbarItem`, placement, customisation
- Sidebars and sidebar styles
- Inspectors — the right-hand panel pattern
- Tabs in macOS context (different from iOS)
- Menus and `commands` — app-level and contextual
- How these compose for a typical macOS app shell

**Outcome:** Danny can specify a complete macOS app shell — "split view with sidebar, toolbar with these items, inspector on the right, these app menus" — and reason about how the pieces fit.

---

## Chapter 10 — Presentation

**Goal:** know the modal and transient UI patterns and when each is appropriate.

**Key concepts:**
- Sheets, popovers, alerts, confirmation dialogs
- Contextual menus
- Inspectors as a presentation pattern (cross-reference chapter 9)
- macOS conventions: when to use a sheet vs a panel vs a new window
- Brief mention: where AppKit `NSPanel` is still required (full coverage in chapter 13)

**Outcome:** Danny can pick the right presentation style for a given interaction and knows the macOS conventions around each.

---

## Chapter 11 — Animation, transitions, gestures

**Goal:** understand how SwiftUI handles motion and interaction, focused on macOS-appropriate use.

**Key concepts:**
- Implicit animation: `.animation(_:value:)`
- Explicit animation: `withAnimation { }`
- Transitions on view appearance/disappearance
- Gestures: tap, drag, hover (macOS-specific and important)
- macOS conventions: restraint. Less motion than iOS. Hover states matter
- How Claude Code tends to over- or under-use these

**Outcome:** Danny can specify motion and interaction in macOS-appropriate ways and can spot when generated code has overdone it.

---

## Chapter 12 — Intermediate layout

**Goal:** know the escape hatches from the basic layout model — what they are, when to reach for them, when not to.

**Key concepts:**
- `GeometryReader` — what it does, why it's often misused
- Alignment guides — for cross-stack alignment
- The `Layout` protocol — custom layouts when stacks aren't enough
- `Canvas` — when you genuinely need to draw
- Heuristic: most layouts don't need any of this. Recognise when they do.

**Outcome:** Danny knows these tools exist, knows roughly when each applies, and (importantly) knows when to push back if Claude Code reaches for `GeometryReader` unnecessarily.

---

## Chapter 13 — AppKit when you need it

**Goal:** understand what AppKit is, how it interoperates with SwiftUI, and the genuine 2026 cases where SwiftUI alone isn't enough.

**Key concepts:**
- What AppKit is: the older, imperative, still-very-much-alive framework underneath
- The seams: `NSViewRepresentable`, `NSViewControllerRepresentable`
- How to wrap an `NSView` so it slots into a SwiftUI hierarchy (with a basic worked example)
- The genuine 2026 holdouts where people still reach for AppKit:
  - True `NSPanel` behaviour (floating, non-activating, HUD windows)
  - Deep window chrome customisation
  - `NSTextView` for serious text editing
  - Certain advanced table behaviours
  - Custom drag-and-drop at the system level
  - Some accessibility edge cases
- How to communicate "this needs AppKit" to Claude Code when it matters

**Outcome:** Danny can recognise when a UI requirement is going to need AppKit, can describe the seam to Claude Code, and isn't surprised when generated code drops to AppKit for a specific reason.

---

## Chapter 14 — Designing well on macOS

**Goal:** internalise Apple's macOS design conventions for 2026 — enough to spot when generated UIs feel wrong and to guide them back.

**Key concepts:**
- Apple HIG for macOS 26 essentials
- Density and conventions that differ from iOS and the web
- Control sizing (`.controlSize`) and when each is appropriate
- Semantic colours and dark mode
- Accessibility basics — the things that aren't optional
- Where macOS expectations diverge from iOS most sharply

**Outcome:** Danny can critique a macOS UI against platform conventions and can specify designs that feel native rather than ported.

---

## Chapter 15 — Working with Claude Code

**Goal:** consolidate the course into practical guidance for directing Claude Code (and similar agents) to build good macOS UIs.

**Key concepts:**
- How to spec a UI using the vocabulary built across the course
- What Claude Code is reliably good at
- What it's bad at: window chrome subtleties, view identity bugs, over-using `GeometryReader`, iOS-isms creeping into macOS code
- Verification patterns: what to look for when reading generated code
- Iteration patterns: how to push back productively when generated code is wrong
- Current (April 2026) practical advice on the tooling

**Outcome:** Danny can confidently brief Claude Code on a macOS UI, recognise when the output is wrong, and direct iteration toward correct results.
