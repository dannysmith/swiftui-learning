# Repo setup notes

A short brief for the throwaway Claude Code session that will set this repo up.

## What you're doing

You're setting up a learning repository for Danny. The four files already in this repo (`CLAUDE.md`, `syllabus.md`, `2-swiftui-fundamentals/README.md`, and this file) were drafted in a planning conversation. The full transcript of that conversation is in `_origin-conversation.md` — read it for context on the *why* behind decisions.

Your job in this session is **setup**, not teaching. Specifically:

1. **Read the four existing files plus the origin conversation.** Make sure the conclusions in `CLAUDE.md` and `syllabus.md` match the final state of that conversation. Flag anything that looks inconsistent.

2. **Iterate on `CLAUDE.md` with Danny.** The operating instructions are the most important file in the repo and the one most likely to need adjustment once Danny imagines actually using them. Walk through it with him, ask clarifying questions, propose tightenings. Don't just rubber-stamp.

3. **Create chapter directory briefs.** For each chapter in `syllabus.md` (chapters 0, 1, 3–15 — chapter 2 already has its `README.md` as a template), create the directory and a `README.md` following the same shape as `2-swiftui-fundamentals/README.md`:
   - "Where we are" (relating to previous chapter)
   - "Goal" (what Danny should be able to do by end)
   - "Concepts to cover" (numbered, with brief notes on each)
   - "Demos worth considering" (with explicit notes on which concepts *don't* warrant demos)
   - "Out of scope (defer)" — important for keeping chapters focused
   - "Notes" — anything chapter-specific worth flagging

   Do these one or two at a time and let Danny review before continuing. Don't batch all 14 in one go.

4. **Scaffold `teaching-scaffold-app/`** as a minimal hello-world macOS SwiftUI app. This is technically a chapter 0 activity but creating it now means it's there from day one. Keep it absolutely minimal.

## What you're not doing

- Teaching anything. This session is setup-only.
- Adding to `teaching-scaffold-app/` beyond the initial hello-world.
- Editing `syllabus.md` without explicit discussion. The chapter list is settled; per-chapter content can be elaborated in the chapter `README.md` files instead.

## When you're done

The repo should be in a state where Danny can start a fresh CC session, say "we're on chapter 0, let's start," and the teaching can begin cleanly per the procedure in `CLAUDE.md`.
