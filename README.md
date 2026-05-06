# `runlog-org/.github`

This repo holds metadata that GitHub renders at the org level for [`runlog-org`](https://github.com/runlog-org).

- [`profile/README.md`](./profile/README.md) → rendered at [github.com/runlog-org](https://github.com/runlog-org) as the org profile.
- [`design.md`](./design.md) → cross-repo brand and design tokens. Public-facing surfaces (READMEs, the website, blog headers, social cards) consume from here.
- [`renovate.json`](./renovate.json) → cross-repo Renovate preset. Schedule, grouping rules, GitHub Actions SHA-pinning, and runlog-schema fan-out tracking live in one place; per-repo configs extend it.
- [`SECURITY.md`](./SECURITY.md) → org-wide security policy that applies to every repo without its own.

## Renovate onboarding

To bring a new runlog-org repo onto the central Renovate config, add a one-line `renovate.json` at its root:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>runlog-org/.github"]
}
```

That single line inherits the schedule, grouping rules, SHA-pinning, vulnerability handling, and cross-repo runlog-schema tracking defined here. Per-repo overrides go below the `extends` line in the same file.

If you're looking for the project itself, start at [github.com/runlog-org](https://github.com/runlog-org) for the introduction and the repo grid.
