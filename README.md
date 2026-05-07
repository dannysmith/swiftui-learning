
> [!NOTE]
> An Experiment in structured learning with Claude Code. Might be shit, might not 🤷‍♂️

# SwiftUI Learning

A personal learning repo where I (an experienced web/TS/Ruby developer) work through macOS SwiftUI development with Claude Code as my teacher. The aim isn't to learn Swift — it's to build a sound mental model of macOS UI development, so I can imagine, decompose, and brief Claude Code on real apps in the right vocabulary.

## How it works

The spine is [`syllabus.md`](syllabus.md) — sixteen chapters covering Apple/Xcode tooling, SwiftUI fundamentals, state, layout, controls, composition, window chrome, presentation, AppKit interop, design conventions, and how to direct AI tooling effectively. Each chapter has its own directory (`N-chapter-name/`) with a `README.md` brief, and may accumulate demo files, notes, and an exported session transcript as I work through it.

[`CLAUDE.md`](CLAUDE.md) is operating instructions for the AI — it puts Claude Code in *teacher* mode rather than coding-assistant mode (default to prose, not code; demos as a tool, not a default rhythm; and so on). [`teaching-scaffold-app/`](teaching-scaffold-app/) is a SwiftUI macOS app that accretes features from chapter 4 onwards — pedagogy-with-continuity rather than a product to ship.

The actual learning happens in Claude Code Desktop, opened against this repo. Each session is roughly one chapter.
