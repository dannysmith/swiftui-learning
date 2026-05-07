# Chapter 9 — Window chrome and navigation

## Where we are

We can compose UIs (chapter 8). Now we put the macOS-specific clothing on the app: sidebars, toolbars, inspectors, app menus — the things that make a Mac app *look and feel* like a Mac app rather than an iOS port.

## Goal

By the end of this session Danny should be able to:

- Specify a complete macOS app shell — sidebar, content, detail, toolbar, inspector, menus — and reason about how the pieces fit
- Pick the right placement for toolbar items
- Add app-level menu commands and contextual menus

## Concepts to cover

1. **`NavigationSplitView`**
   - The canonical macOS sidebar+content+detail pattern
   - Two-column vs three-column variants
   - How selection drives detail

2. **Toolbars**
   - `.toolbar { ... }` and `ToolbarItem`
   - Placement values (`.primaryAction`, `.navigation`, `.principal`, etc.) — what each means on macOS
   - Customisable toolbars (user can rearrange)

3. **Sidebars and styles**
   - `.listStyle(.sidebar)` and the macOS sidebar look
   - Sections within sidebars
   - Sidebar collapse behaviour

4. **Inspectors**
   - The right-hand panel pattern (`.inspector { ... }`)
   - When to use an inspector vs a sheet vs a popover

5. **Tabs in macOS context**
   - `TabView` on macOS — *not* the iOS bottom tab bar
   - When tabs make sense in a Mac app (rarely as primary nav; often within a window)

6. **Menus and `commands`**
   - App-level: `.commands` on a `Scene` (cross-ref chapter 4)
   - Replacing default menu groups
   - Contextual menus (`.contextMenu`)

7. **Composing into a full app shell**
   - Putting `NavigationSplitView` + toolbar + inspector + commands together
   - Walk through a typical macOS app skeleton

## Demos worth considering

- Add `NavigationSplitView` to `teaching-scaffold-app/` with a sidebar list driving a detail view — major beat, hugely tactile
- Add a toolbar with a couple of `ToolbarItem`s
- Add an `.inspector { }` panel — once seen, the pattern sticks
- Custom app menu commands via `.commands`
- This chapter is where `teaching-scaffold-app/` starts looking like a real macOS app

## Out of scope (defer)

- Sheets, popovers, alerts — chapter 10
- Custom window chrome (transparent titlebar, hidden traffic lights) — chapter 13
- `MenuBarExtra` / status-bar-only apps
- Document-based navigation (`DocumentGroup`)

If we drift into any of these, flag it and park.

## Notes

- macOS tabs are *not* iOS tabs. Don't let Claude Code default to the iOS bottom-tab pattern — flag it explicitly.
- This is the chapter where the "this looks native" feeling really arrives. Take time over it.
- Pay attention to sidebar styling — Apple updates it across releases and the macOS 26 surface is what matters.
