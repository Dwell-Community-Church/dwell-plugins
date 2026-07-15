# dwell-plugins

General-purpose Claude skills and plugins for churches and ministries, shared by the ICT team at
[Dwell Community Church](https://www.dwellcc.org).

These are Claude Code and Claude Cowork plugins we built for our own staff and cleaned up to share.
They aren't tied to any one church management system (though a couple can optionally pull from
**Rock RMS** if you use it). Use them, fork them, adapt them to your team. They're sanitized derivatives of what we run internally at Dwell, versioned independently of our internal builds.

> Looking for our **Rock RMS**-specific plugins (documentation and developer reference)? Those live in
> [Dwell-Community-Church/rock-plugins](https://github.com/Dwell-Community-Church/rock-plugins).

## What's here

| Plugin | What it does |
|--------|--------------|
| [`staff-onboarding`](./staff-onboarding) | Personalizes Claude for a staff member through a short interview, then produces a Custom Instructions block (and, in Cowork/Code, a workspace). |
| [`powerpoint-builder`](./powerpoint-builder) | Turns content you provide into a polished, editable `.pptx`, in your brand, a template you have, or a new custom style. You bring the words; it designs the deck. |
| [`daily-brief`](./daily-brief) | A personalized morning brief pulling your calendar, tasks, email, and (optionally) Rock RMS into one dashboard. |
| [`brand-example`](./brand-example) | A fill-in-the-blanks template for building your own organization's brand-identity skill. |

## Install

In Claude Code:

```
/plugin marketplace add Dwell-Community-Church/dwell-plugins
/plugin install staff-onboarding@dwell-plugins
/plugin install powerpoint-builder@dwell-plugins
/plugin install daily-brief@dwell-plugins
/plugin install brand-example@dwell-plugins
```

## Support

Shared as-is, with no warranty or guarantees (see [LICENSE](LICENSE)). Issues and pull requests are
welcome and we'll look when we can, but this is a side effort from a church ICT team, not a supported
product.

## Credits

Built by the Dwell Community Church ICT team. `staff-onboarding` and `daily-brief` are adapted from
Triumph Tech's Cowork starter kit. Thanks to Triumph Tech and the Rock community.

## License

[Apache License 2.0](LICENSE).
