# dwell-plugins

General-purpose Claude skills and plugins for churches and ministries, shared by the ICT team at
[Dwell Community Church](https://www.dwellcc.org).

These are Claude Code and Claude Cowork plugins we built for our own staff and cleaned up to share.
They aren't tied to any one church management system (though a couple can optionally pull from
**Rock RMS** if you use it). Use them, fork them, adapt them to your team.

> Looking for our **Rock RMS**-specific plugins (documentation and developer reference)? Those live in
> [Dwell-Community-Church/rock-plugins](https://github.com/Dwell-Community-Church/rock-plugins).

## What's here

| Plugin | What it does |
|--------|--------------|
| [`powerpoint-builder`](./powerpoint-builder) | Turns content you provide into a polished, editable `.pptx`, in your brand, a template you have, or a new custom style. You bring the words; it designs the deck. |
| [`daily-brief`](./daily-brief) | A personalized morning brief pulling your calendar, tasks, email, and (optionally) Rock RMS into one dashboard. |

## Install

In Claude Code:

```
/plugin marketplace add Dwell-Community-Church/dwell-plugins
/plugin install powerpoint-builder@dwell-plugins
/plugin install daily-brief@dwell-plugins
```

## Support

Shared as-is, with no warranty or guarantees (see [LICENSE](LICENSE)). Issues and pull requests are
welcome and we'll look when we can, but this is a side effort from a church ICT team, not a supported
product.

## Credits

Built by the Dwell Community Church ICT team. Thanks to the Rock community.

## License

[Apache License 2.0](LICENSE).
