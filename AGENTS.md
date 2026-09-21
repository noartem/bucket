# AGENTS.md

Guidance for coding agents working in this repository.

## Project

This is the **noartem** Scoop bucket:

```pwsh
scoop bucket add noartem https://github.com/noartem/bucket
scoop install noartem/twentymate
```

- One manifest per app, in `bucket/<app>.json`, named after the app.
- On every manual addition or removal of an app in the bucket, update the `## Applications` table in `README.md` so it stays in sync with the manifests.
- Before committing a new or updated manifest, verify it with the bucket scripts:
  - `pwsh -NoProfile -File bin/checkver.ps1 <app> -u` — resolves the latest version and rewrites the manifest via its autoupdate rules.
  - `pwsh -NoProfile -File bin/checkhashes.ps1 <app>` — downloads each URL and verifies the pinned hash.
  - `pwsh -NoProfile -File bin/formatjson.ps1 <app>` — normalizes JSON formatting.
- Preferred conventions for new manifests: `checkver: "github"` with a matching `autoupdate` block (per-architecture `hash` URL objects when a release ships `.sha256` sidecars), 4-space indent.
