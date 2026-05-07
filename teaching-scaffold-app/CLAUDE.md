# teaching-scaffold-app

This directory holds the SwiftUI macOS app that accretes features chapter by chapter as Danny works through the parent repo's syllabus. It's pedagogy-with-continuity — a real running app that gives concepts a context to live in — **not a product to ship.**

## Current state

The Xcode project has been pre-scaffolded with a default macOS SwiftUI template (Interface: SwiftUI, no Core Data/SwiftData, no tests). The structure on disk:

```
teaching-scaffold-app/
├── CLAUDE.md                       (this file)
├── TeachingScaffoldApp.xcodeproj/  (the project bundle)
└── TeachingScaffoldApp/            (source folder)
    ├── Assets.xcassets/
    ├── ContentView.swift
    └── TeachingScaffoldAppApp.swift
```

To open: double-click `TeachingScaffoldApp.xcodeproj`, or `open TeachingScaffoldApp.xcodeproj` from the terminal.

## Lifecycle

- **Chapter 0** *tours* this pre-scaffolded project, naming each piece against the concepts being introduced (`.xcodeproj` bundle, source folder, `Assets.xcassets`, `App` and `ContentView` files, Previews, panes, etc.). The wizard step has already been done — chapter 0's consolidation is recognition, not creation.
- **Chapters 1–3** mostly leave this app idle. Concepts there are taught conceptually rather than by accretion.
- **Chapter 4 onwards** starts adding features here: scenes, settings, layout patterns, controls, navigation chrome, presentation, and so on. By the end of the course this app should embody the full set of chapter concepts in a runnable form.

## Working in here

See the parent `../CLAUDE.md` for overall operating instructions. Short version: the goal is Danny's understanding. Don't add features beyond what the current chapter calls for, don't optimise for the app being a polished deliverable, and don't accrete from chapters Danny hasn't reached yet.
