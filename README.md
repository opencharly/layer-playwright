# playwright

The [Playwright](https://playwright.dev) browser-automation CLI for OpenCharly
images.

The `playwright` candy installs the `playwright` npm package globally, so the
`playwright` binary is on `PATH` for AI-agent browser snapshots and scripted
browser automation.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `playwright` |
| Binary | `~/.npm-global/bin/playwright` |
| Install | global npm install (`package.json`) under `NPM_CONFIG_PREFIX` (`~/.npm-global`) |
| Requires | [`layer-nodejs`](https://github.com/opencharly/layer-nodejs) |
| Service / port | none |

## How to use it

Compose the layer by pinning this repo in a box's `candy:` list:

```yaml
my-agent-box:
  candy:
    base: fedora
    candy:
      - '@github.com/opencharly/layer-playwright:v2026.239.1637'
```

Then, inside the built image (or on a dev host):

```bash
playwright --version        # prints a semantic version
playwright --help           # lists install, codegen, and the other commands
playwright install chromium # download a browser build
```

The candy's `plan:` asserts the binary and package are installed,
`playwright --version` exits cleanly, and `playwright --help` lists the `install`
and `codegen` commands that define the CLI surface.

## Layout

- `charly.yml` — the `playwright:` candy entity (the `require:` on `layer-nodejs`
  and the `check:` assertions).
- `package.json` — pins the `playwright` npm package installed globally.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Family skill: `/charly-hermes:playwright-layer` (this repo carries no `skill:` entity — see `AGENTS.md`)
- Browser dependency: `/charly-coder:nodejs`
- Alternative automation: `/charly-check:cdp` (Chrome DevTools Protocol)
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
