---
name: staff-onboarding
description: >
  Personalize Claude for a church or ministry staff member so it knows who they are and how they work.
  In Chat it produces a Custom Instructions block; in Cowork or Code it also sets up their workspace and
  context files. Trigger on "help me personalize Claude", "set me up", or "onboard me".
---

# Staff Onboarding

Personalize Claude for a church or ministry staff member: who they are, their role, and how they like to
work and communicate. If they have used Chat for a while with **memory on**, Claude often already knows a
lot about them; lead from that. This should feel like a short, friendly interview that confirms what is
known and fills in the rest, not a blank form and not a one-shot dump.

Most staff are in **Chat**, so that is the main path. Cowork and Claude Code add a local workspace on
top of the same personalization.

## Org background (customize this for your church)

> **For the maintainer who installs this skill:** if your church has org-wide context that every staff
> member shares, list it here so the interview stays about the *person*, not the organization. For
> example: the church management system you run (Rock RMS, Planning Center, Breeze, etc.) and its
> version, or any brand / documentation skills that already reach staff automatically. Anything you put
> here, Claude should weave in silently and never quiz the user on. Delete this block if you have nothing
> org-specific to add.

Keep the interview about *them*, not about the organization.

## Core principle: start from what you already know

Never open with a cold "tell me about yourself." First surface what you already know about this person
from memory, then confirm it interactively (ask, do not assert), correct, and fill the gaps. A blank
interview feels like busywork, but a wall of "here is everything I know about you" is not an interview
either. Aim for a real back-and-forth.

## If they are already set up (do not re-interview)

Check first for existing setup: a saved Custom Instructions block, filled-in `context/` files, or a
`CLAUDE.md`. If it is there, this is a **return visit**, not a first run. Do not re-ask questions they
have already answered. Instead, briefly show what is already captured and ask only what they want to
**change, add, or remove**, then update in place. Re-run the full interview only if the setup is empty
or they explicitly ask to start over, and never overwrite their answers or make them redo the whole
thing.

## In Chat (the main path)

1. **Recall briefly, then calibrate.** Give a *short* read of what you know (a couple of lines, not a
   wall of text) and invite corrections, then set the depth:
   - If memory is rich: *"I've got a good picture already. Want a quick confirm-and-build, or go deeper
     so we really tune it?"*
   - If memory is thin: *"I don't have much on you yet. Quick setup, or a thorough one?"*

   Keep this to a few sentences. Do not dump a multi-paragraph summary of everything you know; you
   confirm the details interactively in the interview itself.
2. **Interview, one question at a time.** Use the question set below. Ask one, let them answer, then ask
   the next. Never dump all the questions at once. Keep it conversational and react to what they say.
3. **Draft, show, refine.** Turn their answers into a Custom Instructions block, show it, and invite
   changes. Iterate until they are happy. Do not hand over a block and move on; the tweaking is what
   makes it theirs.
4. **Close cleanly.** Once they are happy with the block, do one final wrap-up: show the finished block
   one more time, give the exact paste location (below), confirm they are set, and point them to one or
   two next steps. Do not trail off or re-open questions.

## The interview

Lead from memory, but **confirm, do not assert.** Turn what you know into quick check questions
("I have you as [role], still right?") rather than stating it as fact in a summary. On the **thorough
path, ask every question below even when you could infer the answer** from memory; the person's own
words beat your guess, and the back-and-forth is the whole point. Only skip a question they have just
answered themselves. On the **quick path**, keep it lean: confirm the essentials fast, then build.

**Make it easy and quick: offer options on every question and let them tap.** The goal is a finished
setup with as little typing as possible. Lead each question with a short list of tappable options and
invite additions, phrased plainly, for example *"Do any of these annoy you? Tap what lands, and tell me
any I miss."* Offer options by default; never wait for the person to ask, since "I'm not sure" is the
usual starting point.

- For the **preference questions** (tone, what to avoid, format, act vs ask): a **multi-select menu** of
  common options.
- For the **personal questions** (role, what they use Claude for, what "good" looks like): still offer a
  few example picks to react to, but always let them answer in their own words. Options beat a blank
  page; their own words make it personal.

Keep the default path short and move briskly to the block; do not turn every answer into a follow-up.

Starter menus to adapt (present as options, always invite "anything I missed"):

- **Role / what you do:** pastor or ministry lead; admin or operations; communications or creative;
  finance or giving; facilities; tech or data; leadership. (Pick the closest or say your own.)
- **What you'll use Claude for:** writing and email; planning and organizing; research and summarizing;
  questions about your systems; reports and data; brainstorming and thinking things through.
- **What "good" looks like:** got it right the first time; sounded like me; short and usable as-is;
  asked before assuming; caught something I missed.
- **What to avoid:** flattery or "great question" openers; hedging and over-caveating; filler sign-offs
  ("let me know if..."); restating the question before answering; em dashes; over-formatting or bullet
  soup; asking permission instead of acting; making things up instead of saying "not sure."
- **Communication tone:** warm and personal; direct and to the point; concise; thorough and detailed;
  casual; more formal.
- **Format:** prose over bullets; bullets for lists; short by default; headings on longer pieces; plain
  emails with no bullets or bold.
- **Act vs ask:** just do it and show me; check first on anything irreversible; always show a plan first.

**Quick path (the essentials):**

1. What is your role, and what do you spend most of your time on?
2. What do you want Claude's help with most? (writing, planning, research, email, your systems)
3. How do you like Claude to communicate with you? (tone, length, formal or casual)
4. Do any of these annoy you? (present the "what to avoid" menu above and invite additions)

**Thorough path adds:**

5. When Claude nails something for you, what did it get right? (what "good" looks like, in your words)
6. Any format preferences? (prose vs bullets, Markdown, how you like emails written)
7. Should Claude just act, or check with you first on bigger or irreversible things?
8. Do you write things other people read (congregation, volunteers, team)? If so, who is the audience
   and what tone fits?
9. Anything about how you work that would help Claude get it right the first time?
10. Optional: anything beyond work you'd want Claude to know? (interests, quirks)

Ask a follow-up when an answer is vague. "Be concise" is weaker than "lead with the answer, then a
sentence or two of why." Push gently for the specific version, in their own words.

## Building the Custom Instructions block

- **Right-size it.** A quick setup yields a short block (a few lines). A thorough one yields a richer
  block. Never pad.
- **Capture standards in their words**, not just toggles. "What good looks like" and "what to avoid"
  are what make a block feel personal; keep their phrasing.
- Include, as they gave it: who they are and their role, what they use Claude for, communication tone,
  format preferences, act-vs-ask preference, and audience/voice if they create content.
- Keep it to always-on basics. Deep work detail belongs in the Cowork context files, not here.
- If your church added org background above (a brand skill, ChMS docs) that already reaches staff, you do
  not need to restate it in every person's block.
- **Include the workspace line.** Add: "If I'm working in a folder that has a CLAUDE.md file, read and follow it." It lets Cowork honor a workspace `CLAUDE.md`, and it is harmless for Chat-only people.

Show the block in a fenced code block so they can copy it cleanly. Shape it to what they actually said;
this is only a starting shape:

```
My name is [name]. I work at [my church or organization] as [role]. I mostly [main focus / what I use Claude for].

How I like Claude to work with me:
- [tone preference]
- [format preference]
- [what good looks like, in their words]
- [what to avoid]
- [act vs ask preference]

If I'm working in a folder that has a CLAUDE.md file, read and follow it.
```

## Make it permanent (the paste steps)

1. Open **claude.ai** (browser or app).
2. Go to **Settings > General**. In the **Profile** section, find **Instructions for Claude**.
3. Paste the block there. It applies across their chats, and Cowork too.

That field is the whole point of the exercise: it turns fuzzy memory into an explicit, always-on setup.

## In Cowork or Claude Code (adds a workspace)

The **Instructions for Claude** field applies in Cowork as well, so once they have saved their block,
Cowork already knows who they are. Do **not** re-interview their identity here. Instead:

1. **Confirm it carried.** Have them ask *"what do you know about me?"* If for some reason Cowork does
   not know them, have them paste their Custom Instructions block, or run this Chat onboarding first.
2. **Scaffold the workspace** (only what is missing). Check first for an existing `CLAUDE.md` or a
   filled-in `context/` and never overwrite without asking. Create `context/`, `initiatives/`,
   `learnings/`, `projects/`, `templates/`, `working/`, `skills/`, then place starter files where they
   do not already exist: a `CLAUDE.md` at the workspace root, and `context/about-me.md`,
   `context/work-context.md`, and `context/working-preferences.md`. (If you bundle template files with
   this skill, copy them into place; otherwise generate sensible starters from the interview.)
3. **Fill the context files** from what they gave, plus their Custom Instructions block, and interview
   only for real gaps. Set the `User Timezone` line in `CLAUDE.md`. Show each file and let them correct
   it.

The Cowork context files are a deeper work layer on top of the always-on block. Keep the block as the
one short thing they maintain for identity and preferences.

**Where to keep the workspace.** Recommend they put the workspace folder in a synced cloud drive
(OneDrive, Google Drive, Dropbox, iCloud): it gives them backup, version history, undelete, and sync
across machines. Remind them a Cowork workspace lives on the computer where it is set up, so unlike Chat
it does not follow them across devices.

## Point them to what is next

Briefly: if your church has org-wide skills (brand, ChMS documentation), those already reach them; if
they want Claude to **write in their voice**, point them to a style-guide skill if one is installed; and
they should connect their tools (email, calendar, file storage, and their ChMS if supported). Suggest
they ask *"what do you know about me?"* in a fresh chat to confirm it took.

## Notes

- Never overwrite an existing `CLAUDE.md` or a filled-in context file without explicit confirmation.
- Adapted from Triumph Tech's Cowork starter kit.
