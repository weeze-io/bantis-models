# bantis-models

The over-the-air model list for [bantis](https://github.com/weeze-io). The app fetches
`models.json` from this repo at launch.

It's the **fallback**: when a harness's CLI can list its own models, bantis uses that list and
ignores this file for that harness. This file applies only when a CLI can't list its models (Claude
Code always, any other CLI when its list command fails).

## Format

```json
{ "version": 1, "models": [ { "id": "sonnet", "label": "Claude Sonnet 5", "harness": "claude_code", "isDefault": true } ] }
```

Per entry: `id` (passed to the CLI; `""` means the CLI's own default), `label`, `harness`
(`claude_code`, `codex`, `opencode`, `cursor`, `pi`, `copilot`), and optionally `isDefault`,
`hidden` (hide a broken model, with a `note` saying why), `note`, and `minAppVersion`.

## Changing it

Run `pnpm check:models <path to this models.json>` in the bantis repo before you push. Every
entry that isn't hidden has to pass.
