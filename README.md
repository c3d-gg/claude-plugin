# c³d.gg Claude Code plugins

The plugin marketplace for [c3d-gg](https://github.com/c3d-gg). Each plugin
lives in its own repo; this one is just the catalog.

## Install

```
/plugin marketplace add c3d-gg/claude-plugin
/plugin install clauc@c3d
```

## Plugins

| plugin | what it does |
|---|---|
| [clauc](https://github.com/c3d-gg/clauc) | Branch-level time tracking — estimate from your own history instead of vibes. Opinionated: requires [Bun](https://bun.sh). |

## How releases work

Marketplace entries pin a git tag (`ref`) and a `version`. Claude Code only
re-fetches a plugin when its version string changes, so shipping an update is:

1. Tag a release in the plugin repo (`git tag v0.x.y && git push --tags`).
2. Bump `ref` and `version` for that entry in
   `.claude-plugin/marketplace.json` here.
3. Users pick it up on `/plugin marketplace update c3d` (or the background
   auto-refresh).

## Adding a plugin

1. Give the plugin its own repo under `c3d-gg` with a
   `.claude-plugin/plugin.json` at the root.
2. Add an entry to `.claude-plugin/marketplace.json` with a
   `{ "source": "github", "repo": "c3d-gg/<name>", "ref": "v0.1.0" }` source.
3. Validate before pushing:

   ```sh
   claude plugin validate .
   ```

## License

MIT — individual plugins carry their own license.
