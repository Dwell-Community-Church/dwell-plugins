---
name: daily-brief
description: >
  Generates a comprehensive daily brief by pulling live data from your calendar, tasks,
  email, and (optionally) Rock RMS. Trigger on phrases like "daily brief", "morning brief", "what do I
  need to know today", "what's on my plate", "what's in my inbox", "catch me up", "brief me", or "the rundown".
  Writes the report to daily-brief.html when a workspace folder is available; otherwise
  presents it inline.
---

# Daily Brief

## Purpose

This skill produces a daily brief covering these areas:

1. **TL;DR** - top 3-5 things you need to know today (written last, placed first)
2. **Verse of the Day** - an encouraging Bible verse relevant to a ministry leader
3. **Today's Calendar** - upcoming meetings for today
4. **Action Items** - consolidated list of everything requiring your attention
5. **My Tasks** - tasks due soon or overdue (from your task tool and/or Rock reminders)
6. **Email Inbox** - important emails that need a response or action
7. **From Rock** *(optional)* - new connection requests, prayer requests, or reminders worth your attention today

Run all data-gathering steps in parallel where possible to save time. Gather only from the tools you have connected; silently skip any source you are not connected to. After presenting the brief, summarize the key highlights in the conversation, don't just say "done."

## Environment: workspace vs. browser

This skill runs in two modes. Detect which applies and behave accordingly:

- **Workspace mode** (Claude Code / Cowork, where you have a workspace folder and can run Bash): write the full report to `daily-brief.html` in the workspace folder, archiving the previous one first (see Archive Step).
- **Browser mode** (claude.ai in a browser, no workspace folder): do not try to write a file or run Bash. Present the brief directly in the conversation as a clean, well-formatted summary (or as an artifact if that's available). Skip the Archive Step.

If unsure, attempt the workspace path and fall back to presenting inline when there's no writable workspace. Never fail the whole brief just because a file can't be written; the content is what matters.

## Setup (per user)

This brief is personal to each user. Configure your own:
- **Weather location** (Step 0): set your city and state.
- **Key people**: the email step flags messages from important contacts; if you keep a `context/about-me.md` listing them it's used, otherwise general heuristics apply.
- **Connected tools**: connect whichever calendar, email, task, and Rock tools you want included; anything not connected is skipped silently.

## TL;DR (Write Last, Place First)

After completing all other steps, write a 3-5 bullet summary of the most important things to know today. Focus on anything urgent, anything requiring a decision, and overall workload. Written last, placed at the very top.

## Verse of the Day

Search the web for an encouraging Bible verse relevant to a ministry leader for today's date. Choose something that speaks to themes like wisdom, perseverance, servant leadership, shepherding, integrity, or vision. Avoid overly familiar verses; look for something fresh and thought-provoking.

## Step 0: Weather

```
GET https://wttr.in/[Your City, State]?format=j1
```

From the response, extract for today:
- `maxtempF` - the high temperature in °F
- `weatherDesc` - the condition description (e.g. "Sunny", "Partly cloudy")
- Choose an appropriate weather emoji based on the condition (☀️ 🌤️ ⛅ 🌥️ ☁️ 🌧️ ⛈️ 🌩️ 🌨️ 💨)

Store as `weather_high`, `weather_desc`, and `weather_icon`. If the request fails, omit the weather widget silently.

> **Setup:** Replace `[Your City, State]` in the URL with your location, no spaces (for example `Nashville,TN`). If you haven't set a location, skip the weather widget.

## Step 1: Today's Calendar

Read your calendar and list all appointments for today. If today is Monday, also check Friday's calendar for any meetings that may have generated action items.

Exclude any calendar items with "buffer" in the title; these are personal time blocks and should not appear in the report.

If there are no meetings today, say so clearly.

## Step 2: Action Items

After gathering data from all sections, compile a consolidated list of everything you need to act on. Include items from email, meeting follow-ups, your task tool, and Rock. Written last but placed here in the report. Keep it tight, only genuine action items, not passive information.

## Step 3: My Tasks - Due & Near-Due

Pull your assigned tasks from your task tool (and Rock reminders, if connected). Focus on:

- Tasks that are **overdue** (due date has passed)
- Tasks **due within the next 3 days**
- Tasks **in progress with no due date** (list briefly)

For each task include: task name, due date, urgency. If nothing is overdue or near-due, say so clearly.

**No Due Date flag:** After the due/near-due tasks, pull all incomplete tasks with no due date set. Render these at the very bottom of the sidebar card under an amber/yellow warning:

```
⚠️ No Due Date - X tasks
```

List each task by name. The purpose is to ensure nothing falls through the cracks. If there are no tasks missing a due date, skip this section entirely.

## Step 4: Email Inbox - Important Items Needing Attention

Search your inbox for emails that likely need your attention. Signal over noise, not every email, just the ones that matter.

**Look for:**
- Emails where you are the primary recipient (To:, not CC) and have not replied
- Emails from team members, partners, or congregants
- Threads appearing to wait on you

**Filtering heuristics:**
- Focus on the last 5 business days
- Deprioritize newsletters, notifications, automated emails, and calendar invites
- Skip threads with a recent reply from you
- Flag anything from key people (see your `context/about-me.md` if you keep one)

Aim for 3-8 genuinely important items. If nothing stands out, say so.

## Step 5: From Rock (Optional)

If you have the Rock connector enabled, surface a short, read-only snapshot worth seeing first thing:

- New connection requests assigned to you, or unassigned in your area, since yesterday
- New prayer requests submitted in the last day
- Rock reminders due today

Keep this read-only. Never write back to Rock or send communications from this brief. If the Rock connector is not enabled, skip this section silently.

## Archive Step (workspace mode only, run before writing new file)

**Only in workspace mode.** In browser mode, skip this entirely.

Before writing the new `daily-brief.html`, check if one already exists in the workspace folder. If it does:

1. Open the file and find the `<title>` tag to extract the date (e.g., `Daily Brief - Wednesday, March 25, 2026`)
2. Parse that date into `YYYY-MM-DD` format (e.g., `2026-03-25`)
3. Create an `archive/` folder in the workspace if it doesn't already exist
4. Move (rename) the existing file to `archive/daily-brief-YYYY-MM-DD.html`

Use Bash to perform the move. If no existing file is found, skip this step silently.

## Report Structure and Design

The brief is a single self-contained HTML document. **In workspace mode**, save it to `daily-brief.html` in the workspace folder. **In browser mode**, render it inline (or as an artifact) instead of saving.

**Layout:** Two-column grid, a wider main column on the left, a narrower sidebar on the right (~340px).

**Design system:**
- Font: a clean system font stack. Use `-apple-system, "Segoe UI", Roboto, Helvetica, Arial, sans-serif`. Default body weight 400; headings and names 700.
- Light mode: white cards on an off-white (`#FAFAFA`) background
- Neutral color palette, use these CSS custom properties:
  ```
  --brand-dark:   #1F2A37   (primary dark: text, card headers, headings)
  --brand-dark-2: #243447
  --brand-dark-3: #2E4258
  --accent:       #3B82F6   (accent: borders, highlights, unread dots)
  --accent-2:     #2563EB
  --accent-light: #EFF5FF   (light tint for summary cards, total rows)
  --accent-mid:   #BFD8FA   (mid tint for borders on summary cards)
  --muted:        #5D6B7A   (muted text)
  --bg:           #FAFAFA
  --card:         #FFFFFF
  --border:       #E3E3E3
  --text:         #1F2A37
  --text-muted:   #5D6B7A
  ```

  > **Make it your brand (optional):** to match your church or organization, swap `--brand-dark` and `--accent` for your own brand colors. If you have a brand skill installed, it has your palette.

- Card headers: solid `var(--brand-dark)` background with white text and 700 font weight
- Header: dark gradient (`var(--brand-dark)` to `var(--brand-dark-3)`) with white heading text. Uses `display: flex; justify-content: space-between; align-items: stretch` so both sides fill the same height. The left side uses `display: flex; align-items: center` to vertically center the greeting.
- **Header greeting (left):** Write a short, clever, context-aware greeting each morning, not just "Good morning" every day. Vary it based on the day of the week, season (Advent, Lent, Easter, summer), or something happening in the brief. Keep it warm and brief, one line with an emoji. Style: `font-size: 32px; font-weight: 700; color: #FFFFFF; line-height: 1; padding-top: 4px`.
- **Header right side:** A single frosted-glass pill using `background: rgba(255,255,255,0.1); border: 1px solid rgba(255,255,255,0.2); border-radius: 6px; display: flex; flex-direction: column; align-items: center; justify-content: center; padding: 8px 14px; gap: 1px`. Shows weather: icon + temp as value (e.g. "⛅ 72°F"), condition as label.
- Border radius: 8px on cards
- Color-coded status: green (`#16a34a`) / yellow (`#d97706`) / red (`#dc2626`) with matching soft backgrounds for badges

**Main column (left), full-width sections:**
1. ⚡ TL;DR - dark gradient card, bullet list
2. ✝️ Verse of the Day - blockquote with left accent border
3. 📅 Today's Calendar - table with time + event name + attendees
4. ✅ Action Items - checklist cards; urgent items get a red left border

**Sidebar (right), compact cards:**
1. 📋 My Tasks - task rows grouped by Overdue / Due Today / Due Next 3 Days, color-coded dots and badges; at the very bottom an amber-tinted "⚠️ No Due Date" section (omit if none)
2. 📧 Email - rows with sender name, subject (bold + unread indicator dot), and a one-line "why it matters" note
3. ⛪ From Rock *(if connected)* - connection requests, prayer requests, and reminders worth seeing today

**CSS:** All styles inline in a `<style>` block in `<head>`. No external stylesheets or frameworks. Use CSS custom properties (`:root` variables) for the color palette so the full design stays consistent.

In workspace mode, save the completed report to `daily-brief.html`, then share a concise summary of the most important highlights in the conversation. In browser mode, present the brief inline and give the same summary.

---

*Adapted from Triumph Tech's Cowork starter kit.*
