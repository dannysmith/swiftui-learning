# Chapter 4 — The macOS app skeleton

## Where we are

We have grammar (chapter 2) and state (chapter 3). Now we step *up* to the top level: what an actual macOS app *is* in SwiftUI terms — the entry point, the scenes, the windows. From this chapter onwards, `teaching-scaffold-app/` starts accreting features chapter by chapter.

## Goal

By the end of this session Danny should be able to:

- Describe a macOS app's structure from `@main` down to the first view
- Pick the right scene type (`WindowGroup`, `Window`, `Settings`) for a given app shape
- Reason about multi-window apps and macOS-specific window behaviours
- Add an app-level menu and a settings window to `teaching-scaffold-app/`

## Concepts to cover

1. **The `App` protocol and `@main`**
   - The entry point: a struct conforming to `App` with a `body` returning a `Scene`
   - What `@main` actually does

2. **`Scene` and what scenes are for**
   - Scenes are the top-level "things" an app presents — windows, settings panels, menu-bar items
   - One app, many scenes

3. **`WindowGroup` vs `Window` vs `Settings`**
   - `WindowGroup` — the user can open multiple of these (e.g. document windows)
   - `Window` — a single, unique window (e.g. a main app window)
   - `Settings` — the macOS Settings/Preferences scene; gets the standard ⌘, behaviour for free
   - Other scenes exist (`MenuBarExtra`, etc.) — mention briefly

4. **Multi-window apps and macOS window behaviours**
   - Restoring window state, window sizing, default position
   - Why this is fundamentally different from iOS

5. **App-level menus and the menu bar**
   - `.commands { ... }` on a scene
   - Adding, replacing, removing menu items
   - The macOS menu bar is *app-level*, not window-level

6. **How an app actually launches**
   - What the framework does on your behalf
   - Where you can hook in (briefly — `@Environment(\.scenePhase)`, app delegates)

## Demos worth considering

- Add a `Settings` scene to `teaching-scaffold-app/` — strong tactile beat, real macOS behaviour appears
- Add a custom command to the app menu — visible, immediate
- Possibly a second `WindowGroup` to demonstrate multi-window behaviour
- The app **is** the demo here. Single-file `.swift` snippets are less useful than poking at `teaching-scaffold-app/`.

## Out of scope (defer)

- Toolbars, sidebars, navigation chrome — chapter 9
- Window-level state coordination across multiple windows
- `MenuBarExtra` / status-bar apps in any depth
- Document-based apps (`DocumentGroup`)
- App lifecycle phase handling beyond a brief mention
- AppKit-level window customisation — chapter 13

If we drift into any of these, flag it and park.

## Notes

- This is the chapter where `teaching-scaffold-app/` starts being load-bearing pedagogically — every later chapter assumes Danny has a real app to add to.
- macOS has window concerns iOS doesn't (multi-window, restore state, secondary windows) — emphasise the macOS-specific angle.
- Apple changes scene API surface across releases — the macOS 26 surface is what matters; older patterns are noise.
