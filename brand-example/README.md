# brand-example

A **template** for building your own organization's brand-identity skill, so Claude can design and style
things on-brand for your church or ministry.

This ships no real brand: everything is a placeholder. It gives you the *shape* of a brand skill that
works well with Claude, plus the portable lessons we learned building ours: use exact color values (not
"close enough"), watch accessibility contrast, make the brand opt-in for personal work, and expose your
palette as CSS variables.

## How to use it

1. Install it (below), or just copy the `skills/brand-example/SKILL.md` file.
2. Replace every `[BRACKETED]` placeholder with your real colors, fonts, and logo rules.
3. Bundle your own assets: a `brand-kit.json` (machine-readable values), an `assets/logos/` folder, and
   your brand guide PDF.
4. Rename it for your org (for example `acme-brand`) and remove the template banner.

## Install

In Claude Code:

```
/plugin marketplace add Dwell-Community-Church/dwell-plugins
/plugin install brand-example@dwell-plugins
```
