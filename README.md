# Stress Brawler — Boss Art

Public hosting for the Stress Brawler mobile game's Daily Challenge boss art. The shipped app fetches `bosses-manifest.json` (and the images it references) live, with no caching — this is the **only** network dependency in the game, scoped to opening the Daily Challenge screen. Anything pushed here goes live immediately, no app update needed.

## `weekdays` — the regular 7-boss rotation

One entry per weekday (`"0"`=Sunday .. `"6"`=Saturday), each `{ name, taunt, imageUrl }`. This only overrides **art and flavor text** — HP, the timer, and behaviors (side-switch, guard, etc.) for these 7 ship in the app itself and aren't editable here.

## `events` — one-off special-occasion bosses (Halloween, etc.)

Keyed by the **exact calendar date** in `YYYY-MM-DD` (local time), e.g. `"2026-10-31"`. An event entry on today's date takes over Daily Challenge completely for that day, then reverts to the normal weekday boss on its own the next day — no cleanup needed, an old date just never matches again.

Minimum to add a monster:
```json
"events": {
  "2026-10-31": {
    "name": "PUMPKIN KING",
    "taunt": "Trick or treat... mostly trick.",
    "imageUrl": "https://raw.githubusercontent.com/manifoldecor/stress-brawler-boss-art/main/art/pumpkin-king.png"
  }
}
```
That's enough on its own — HP defaults to 1200, the timer to 35s, and it fights with no special behavior. To make it play differently, add any of:
```json
    "hp": 1500,
    "timeLimitSec": 40,
    "behaviors": ["enrage"]
```
Valid `behaviors` values: `sideSwitch` (hops left/right, must be hit with the matching hand), `guard` (periodic shield phases, ~90% damage reduction while up), `enrage` (faster attacks under 30% HP), `speedster` (fast attacks the whole fight), `bigCounterDamage` (a misread counter costs much more HP). Combine as many as you want in the array.

## Adding art

Drop the image file in `art/`, then point `imageUrl` at it:
`https://raw.githubusercontent.com/manifoldecor/stress-brawler-boss-art/main/art/<filename>`

Managed via the [Boss Art Uploader](https://claude.ai/artifact/CucgoGzK8TMhrQKo3qifMx) for the 7 weekday slots, or edit `bosses-manifest.json` directly on GitHub (including adding `events` entries, which the uploader doesn't have a form for yet).
