---
name: brand-example
description: >
  Example template for building your organization's brand-identity skill. Copy this, replace the
  placeholders with your real colors, fonts, and logo rules, and bundle your own logo files. Use as a
  starting point when you want Claude to design or style anything on-brand for your church or ministry.
---

# Brand Identity Reference (TEMPLATE)

> **This is a template, not a finished brand skill.** It shows the *shape* of a brand-identity reference
> that works well with Claude. Everything in `[BRACKETS]` is a placeholder: replace it with your
> organization's real values, delete what does not apply, and add what is missing. When you have filled
> it in, rename it (for example `acme-brand`) and remove this banner.

Source: `[your brand guidelines file / where these rules come from]`. Last verified `[date]`. If your
brand guide changes, re-verify this skill against it before relying on it for critical work.

**What a finished brand skill should bundle (this template ships none of it):**
- `brand-kit.json` — the same brand data in machine-readable form (colors with hex/RGB/CMYK, typography,
  logo rules). Read it when you need structured values; keep it in sync with this document.
- `assets/logos/` — your logo files (SVG preferred; PNG at a couple of sizes as fallback). Reference them
  by relative path when embedding or inlining a logo.
- `assets/guidelines/` — your source brand guide (PDF), for humans.

## When to apply the brand (ask first for personal work)

State your policy here. A good default: **the brand is opt-in per piece, not automatic.** For
presentations and for personal or internal documents, do not reach for brand colors, fonts, or logos on
your own; ask first whether they want it on-brand. Apply the brand without asking only when the work
clearly represents the organization outwardly (a public flyer, a church-wide announcement, signage), or
when the person explicitly asks for it. When unsure, ask.

## Color palette

List your exact colors and tell Claude to use them precisely. **Use exact hex values; don't substitute
"close enough" colors.**

| Role | Name | Hex | Notes |
|------|------|-----|-------|
| Primary | `[Primary name]` | `[#000000]` | carries the brand; general layout, headlines |
| Primary | `[Secondary name]` | `[#000000]` | |
| Neutral | White | `#FFFFFF` | |
| Accent | `[Accent name]` | `[#000000]` | accent only; a pop to draw attention, not dominant |
| Body copy | `[Body color]` | `[#000000]` | reserved for body text |

Spell out any per-color rules (which colors carry the brand vs. accent-only, which are reserved for the
logo or body copy, which combinations are not allowed).

### Accessibility caution (worth adding even if it isn't in your brand guide)
Check your brand colors for contrast. Bright accent colors often **fail WCAG AA contrast for body text
on white** — fine for large display text, decorative accents, or use on a dark background, but not for
paragraphs. Note here which pairings pass and which don't, so Claude picks readable combinations.

## Typography

Name your typefaces and where each is used. Include a fallback for when the primary font is unavailable
(for example in email, where custom web fonts often don't load).

| Element | Font | Color | Notes |
|---------|------|-------|-------|
| Main headline | `[Font]` | `[color]` | |
| Subheadline | `[Font]` | `[color]` | `[case / letter-spacing rules]` |
| Body copy | `[Font]` | `[color]` | |

If your primary font is served from a web-font provider, put the loading snippet and the exact
`font-family` name here so Claude can wire it into web pages. State the email rule separately (usually: a
system-safe fallback font only).

## Logo usage

Describe your logo variants (full color, white/reverse for dark backgrounds, grayscale, wordmark-only,
small-form-factor for tiny sizes, icon/mark only) and when to use each. Then:

- **Clear space:** the minimum breathing room around the logo.
- **Minimum size:** the smallest it may appear, and when to switch to a small-form-factor version.
- **Never do this:** don't skew, stretch, recolor, rotate, outline, or otherwise edit the logo.

If you bundle logo files, list them here with their relative paths (e.g. `assets/logos/logo-color.svg`)
and note "prefer SVG for embedding." Keep the same paths in `brand-kit.json`.

## Photography, icons, patterns

Short, concrete guidance for each, if you use them:
- **Photography:** the style you want (candid vs. posed, processing, any color-overlay rules), and
  whether original or stock is preferred.
- **Icons:** style (solid vs. line), colors on light vs. dark backgrounds, clear space.
- **Patterns:** what elements your patterns are built from, and whether new ones are allowed.

## Layouts (slides, flyers, signage, social)

For each format your team produces, capture the rules that keep things consistent: required logo
placement, which fonts, standard sizes/dimensions, and any approval step. Keep these as *starting
points* unless your brand treats them as strict.

## Sub-brands (optional)

If you have ministries or events with their own look, give each its own section: accent color(s), any
distinct typeface, and the rule for how it relates to the parent logo (must it appear, and when).

## When generating HTML / CSS / other markup

- Reference colors by hex; do not approximate.
- Apply styling via CSS classes or framework-appropriate styling, not inline styles (except genuinely
  dynamic values).
- Match the typography rules for the right (sub-)brand.
- When unsure which brand or sub-brand applies, ask before defaulting.

### CSS custom properties (drop-in pattern)

Ship your palette and fonts as CSS variables so every generated page stays consistent. Replace the
placeholder values:

```css
:root {
  /* core palette */
  --brand-primary:   [#000000];
  --brand-secondary: [#000000];
  --brand-accent:    [#000000];
  --brand-body:      [#000000];
  --brand-white:     #FFFFFF;

  /* typography */
  --brand-font-primary:   "[Primary Font]", system-ui, sans-serif;
  --brand-font-secondary: "[Fallback Font]", system-ui, sans-serif;
}
```

### Common context cheat sheet (fill in your combinations)
- Web body copy: `[body color]` on white, `[primary font]`.
- Web headline: `[headline color]`, `[primary font]`.
- Button / CTA: `[background]` with `[text color]`.
- Email: `[fallback font]` only.

---

*Template shared by the Dwell Community Church ICT team. Bring your own brand.*
