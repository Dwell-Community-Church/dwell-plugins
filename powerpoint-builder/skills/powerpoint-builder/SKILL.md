---
name: powerpoint-builder
description: >
  Build a polished PowerPoint (.pptx) presentation from content you provide, in the look you choose:
  your organization's brand, a template you already have, or a new custom style. It designs and lays
  out your content; it does not write it for you. Trigger on "build a deck", "make slides", "make a
  presentation", "turn this into slides", or "PowerPoint".
---

# PowerPoint Builder

Turn content you provide into a clean, well-designed **PowerPoint (.pptx)** presentation. You handle
structure, layout, and visual style. You do **not** invent the content. This is a design tool, not a
ghostwriter.

It works in Chat, and in Cowork or Claude Code, where it can save the file into your workspace.

## What this skill does and does not do

- **Does:** organize the person's content into sensible slides, apply a chosen visual look, and produce
  a real, editable `.pptx` they can keep editing in PowerPoint (or import into Google Slides).
- **Does not:** write the presentation for them. Never invent facts, statistics, quotes, scripture
  references, or claims. If a slide needs something they did not provide, ask for it; do not fill it in.
  This matters most for teaching, sermon, and ministry content, where the words must be theirs.

You may reshape and tighten what they give you (split a wall of text across slides, turn a paragraph
into a few short points, suggest a slide order) as long as the substance stays theirs. When unsure what
they meant, ask rather than guess.

## The flow

1. **Get the content.** If they have not already given it, ask for what goes in the deck: an outline,
   notes, a document, bullet points, or a draft. If it is thin, ask them to expand it; do not pad it
   yourself.
2. **Pick the look.** Offer the three options as a neutral choice; never assume or default to one, wait
   for their pick:
   - **Your organization's brand:** on-brand for the church or organization.
   - **Match a template I have:** mimic a PowerPoint they already like.
   - **New custom style:** a fresh look.
3. **Build it** in that look (see below), using the `pptx` skill to generate the file.
4. **Check, then deliver.** Before handing it over, render the slides and confirm they look clean: no
   text overflow, no overlapping elements, and the file opens and validates. Fix any layout issue first.
   Then save the `.pptx` to the workspace (Cowork/Code) or offer it as a download (Chat), and clean up
   the scratch files the build created (build scripts, temp files, per-slide render images), leaving the
   finished deck (keep a PDF preview only if it is useful). Summarize the deck, its look and how to edit
   it, not the build tooling, and offer to revise specific slides.

## The three looks

### Your organization's brand
If a brand skill is installed for your organization, pull its palette, typography, and logo rules and
apply them to the deck theme: title slide, section dividers, content slides, and footer/logo placement.
If there is no brand skill, ask for the essentials instead: two or three brand colors (hex if they have
them), heading and body fonts, and how the logo should be used. Follow whatever brand rules they give
you (clear space, approved color variants).

### Match a template I have
Ask the person to provide their existing PowerPoint (`.pptx`) or template (`.potx`). Use the `pptx`
skill to read its theme, fonts, colors, and slide layouts, and build the new slides **on that template**
so the result matches what they already use. Reuse their masters and layouts rather than inventing new
ones. If they have several, ask which to match.

### New custom style
Guide a quick, low-effort setup, offering tappable starter choices rather than a blank page:
- A few **style directions** to pick from (for example: clean and minimal; bold and modern; warm and
  traditional; photo-forward).
- Then confirm **colors** (offer a small palette or let them name their own) and **fonts** (offer a
  couple of pairings).

Keep it to a few choices, not a long design interview. Apply the chosen style consistently, and offer to
save it so they can reuse it next time.

## Design principles (keep slides clean)

- One main idea per slide. Break dense content into more slides rather than crowding one.
- Short, scannable text: a few short points or a single line beats a paragraph on a slide.
- Consistent type sizes, spacing, and color across the whole deck.
- A clear title slide, section dividers for major parts, and a simple, readable content layout.
- No clip art, stock filler, or decoration that was not asked for.

## Environment: workspace vs. browser

- **Workspace mode** (Cowork / Claude Code): save the finished `.pptx` into the workspace folder and
  tell them the path.
- **Browser mode** (claude.ai Chat): produce the `.pptx` and offer it as a download.

If unsure, produce the file and offer the download.

## Notes

- File generation is handled by the `pptx` skill; this skill decides the content structure and the look,
  then hands off to it. In Cowork or Claude Code, if the JavaScript builder (pptxgenjs via npm) is
  unavailable, quietly use `python-pptx` instead; it is reliable. Never surface build-tool, package, or
  registry details to the user; keep everything they see about the deck itself.
- Optional, opt-in.
