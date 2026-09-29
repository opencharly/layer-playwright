# AGENTS.md — layer-playwright

Standalone candy repo for the `playwright` layer — the Playwright browser
automation CLI installed globally via npm. The candy lives in `charly.yml` at the
repo root (the `require:` on `layer-nodejs` plus the `check:` assertions) with the
`playwright` npm package pinned in `package.json`. It carries **no `skill:`
entity**.

Canonical files:

- `charly.yml` — the `playwright:` candy entity (`require:` + `check:` probes; no
  `skill:` entity).
- `package.json` — pins the `playwright` npm package installed globally.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — user overview only; never agent guidance.

## Load these skills first (R0)

- `/charly-hermes:playwright-layer` — the family skill: the Playwright browser
  automation candy, its npm-global install path, and the browser dependency.
  Load before editing or troubleshooting the candy.
- `/charly-image:layer` — the candy authoring reference (`charly.yml` schema,
  `plan:` step verbs incl. `check:`, package sections, service declarations).
  Load before editing any entity field or plan step.
- **Missing owning skill:** this repo carries no `skill:` entity, so no
  repo-owned skill is projected for the candy; the closest family skill is
  `/charly-hermes:playwright-layer`. The gap is recorded against the named batch
  [opencharly/opencharly#291](https://github.com/opencharly/opencharly/issues/291).

## Build / validate / test

- The merge gate is the **org-wide** `charly/pr-validator` (required check
  `validate / validate`, defined in `opencharly/.github`); this repo has **no
  per-repo candy gate** and ships only `.github/workflows/tag-on-merge.yml`.
- `charly box validate` at the repo root checks the manifest parses and
  validates.
- The candy's `plan:` `check:` steps are the functional evidence: the binary at
  `~/.npm-global/bin/playwright`, the unpacked package, `playwright --version`
  exiting cleanly, and `playwright --help` listing `install` and `codegen`.

## Modify this repo

- Keep the `require:` on `layer-nodejs` and the npm-global install path in sync
  with the package's own layout; the `check:` probes name both.
- New behaviour claims belong in the `plan:` as an observable `check:` step.
- If an owning skill is authored, add the `skill:` entity here and update this
  signpost and the README in the same change.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge
  on PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the
  PR body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.
