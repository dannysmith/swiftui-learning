# Chapter 0 — Apple/Xcode primer

## Where we are

This is the start of the course. We're not building mental models of SwiftUI yet — we're getting the **tooling vocabulary** in place so the rest of the course doesn't trip on unfamiliar terms. The web equivalent is "what's a browser, what's a server, what's an HTTP request" — except Danny already knows what a Mac app *is*, so the actual gap is specifically Apple's project structure and Xcode itself.

There is no previous chapter to relate to.

## Goal

By the end of this session Danny should be able to:

- Recognise the file types that make up an Xcode project, and roughly what each is for
- Look at an Xcode window and name the panes
- Explain what Previews are and why they shape how SwiftUI work feels different from "edit, compile, run"
- Run a SwiftUI app on the Mac and know what's happening
- Have toured the pre-scaffolded `teaching-scaffold-app/`, naming each file and pane against the concepts above, so there's a real project he understands the shape of from now on

This chapter is recognition vocabulary, not mastery. If a section feels like territory Danny already knows, skip it.

## Concepts to cover

1. **What an Xcode project actually is**
   - `.xcodeproj` — the project bundle (it's a directory, not a file)
   - `.xcworkspace` — wraps multiple projects; you'll see this when SPM dependencies are involved
   - `.swiftpm` / `Package.swift` — Swift Package Manager projects, the lighter-weight alternative
   - When you see each one and why

2. **File structure of a typical SwiftUI macOS app**
   - The `@main` entry-point file (`AppNameApp.swift`)
   - `ContentView.swift` convention
   - `Assets.xcassets` — the asset catalog, where images and colours live
   - `Info.plist` briefly — metadata, capabilities
   - The "compared to a web project" framing where it helps

3. **Xcode's panes**
   - Navigator (left): files, search, debug, breakpoints
   - Editor (centre): code, with the Canvas (Previews) attached
   - Inspectors (right): file inspector, attributes inspector
   - Debug area (bottom)
   - Where to find things; not how to master each pane

4. **Schemes and build configurations**
   - At "what is this" level only — the run/stop button, Debug vs Release
   - Why this is rarely something you'll directly mess with

5. **Previews and the live canvas**
   - What they are: live hot-reload of any SwiftUI view, without launching the app
   - Why they change how you work — and why this shapes how you ask Claude Code to structure code (small, previewable views)
   - The `#Preview { ... }` macro shape

6. **Running the app on Mac**
   - Cmd+R; what happens
   - "Simulator" is an iOS thing — on macOS, the app just runs as a normal Mac app
   - Stopping, rebuilding, where logs appear

7. **Signing and entitlements (briefly)**
   - "Automatic signing" defaults — what this means
   - Entitlements as the sandbox/permissions thing (file access, network, etc.)
   - We don't dwell — just make the words not scary later

8. **Touring `teaching-scaffold-app/`**
   - The project is already scaffolded (default macOS SwiftUI template, no Core Data, no tests). The wizard step has been done outside the chapter to keep the lesson focused.
   - Open it in Xcode and walk through it together: the `.xcodeproj` bundle, the source folder, `Assets.xcassets`, `TeachingScaffoldAppApp.swift`, `ContentView.swift`, and the panes/Previews.
   - Name each piece against concepts 1–7 above. This is the consolidation step.
   - If anything in the wizard's choices is worth flagging in retrospect (e.g. why no Core Data, why no tests), do so.

## Demos worth considering

- The chapter outcome **is** the tour: walk through `teaching-scaffold-app/` together, opening files, identifying panes, naming each piece. That's the strongest possible grounding.
- A live Preview in action — change a `Text` label in `ContentView.swift`, watch it update — is a strong tactile beat. Worth doing.
- Running the app (Cmd+R) once so Danny sees the actual default SwiftUI window appear. Quick, satisfying, demystifying.
- Probably no other dedicated demos. This chapter is more "look at things and name them" than "build small isolated examples."

## Out of scope (defer)

- SwiftUI grammar — chapter 2
- Anything about Swift the language beyond a quick "what's a struct" recap if needed
- Build configurations beyond awareness — generally not worth Danny's time
- Mac App Store distribution, notarisation, code signing for distribution
- Swift Package Manager in any depth
- Testing frameworks (XCTest, Swift Testing)
- Instruments / profiling

If we drift into any of these, flag it and park.

## Notes

- This chapter is supplementary-viewing-friendly. Apple has a "Tour of Xcode" WWDC session most years that covers most of this in 30–40 minutes — point Danny at the most recent one as optional pre-watching or follow-up.
- Don't dwell. The goal is "I now recognise these words and panes," not "I have mastered Xcode."
- The teaching-scaffold-app stays minimal here. We don't add features until chapter 4 (the macOS app skeleton chapter), where the structure becomes pedagogically relevant.
