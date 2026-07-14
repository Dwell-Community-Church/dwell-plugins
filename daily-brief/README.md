# daily-brief

A personalized morning brief. It pulls your **calendar, tasks, email**, and (optionally) **Rock RMS**
into one clean dashboard: a TL;DR, today's meetings, a consolidated action list, due and overdue tasks,
the emails that actually need you, and an optional read-only Rock snapshot (new connection requests,
prayer requests, reminders). There's a verse of the day for ministry leaders, too.

It writes a self-contained `daily-brief.html` when you're in a workspace (Cowork / Claude Code), or
presents the brief inline when you're in a browser. It only pulls from the tools you've connected and
silently skips the rest, and the Rock section is read-only: it never writes back or sends anything.

## Install

In Claude Code:

```
/plugin marketplace add Dwell-Community-Church/dwell-plugins
/plugin install daily-brief@dwell-plugins
```

Then say *"give me my daily brief."*

## Setup

It's personal to you. Set your **weather location** in the skill, connect whichever **calendar, email,
task, and Rock** tools you want included, and (optionally) keep a `context/about-me.md` listing key
people so the email step can flag messages from them.
