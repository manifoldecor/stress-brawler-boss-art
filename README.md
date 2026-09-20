# Stress Brawler — Boss Art

Public hosting for the Stress Brawler mobile game's Daily Challenge boss art. The shipped app fetches `bosses-manifest.json` (and the images it references) live — this is the **only** network dependency in the game, scoped to opening the Daily Challenge screen.

- `bosses-manifest.json` — one entry per weekday (`"0"`=Sunday .. `"6"`=Saturday), each `{ name, taunt, imageUrl }`.
- `art/` — the actual boss images referenced by the manifest. Currently placeholder art generated as a starting point — replace these (and the `imageUrl` fields above) with real designs anytime; no app update needed, just edit `bosses-manifest.json` and push.

Managed via the [Boss Art Uploader](https://claude.ai/artifact/CucgoGzK8TMhrQKo3qifMx) — drop new art there and it gets synced here.
