# bolognalife-content

Curated content served at runtime to the [Bologna Life](https://gitlab.com/marcobotton/bolognalife) Flutter app. Updates here go live the next time someone opens the app — no app release needed.

## What's here

| File | What it is |
|---|---|
| `events.json` | Curated list of city-impacting events in Bologna — sports fixtures, BolognaFiere trade shows, major concerts. The app fetches the raw URL from `main`. |

The editorial process — including the prompt template that drives weekly curation — lives in the private app repo, not here.

## events.json schema

Array of objects with these fields. All fields are required (use `""` or `null` for "no value" where the type allows it).

| Field | Type | Notes |
|---|---|---|
| `id` | string | Stable key. Convention: `<kind>-<YYYY-MM-DD>-<slug>` |
| `title` | string | Display name |
| `kind` | enum | `soccer` · `basketball` · `baseball` · `football` · `volley` · `fiera` · `concert` · `other` |
| `venue` | string | Where it happens |
| `startDate` | ISO-8601 | Date-only (`"2026-09-15"`) or with time (`"2026-05-18T20:45:00+02:00"`) |
| `endDate` | ISO-8601 \| null | `null` = single-day event |
| `impactLevel` | enum | `low` · `medium` · `high` · `very_high` |
| `description` | string | One short line of context, can be `""` |
| `url` | string | Deep link; can be `""` |
| `sourceNote` | string | Audit trail — where you saw the info. Not shown in UI; can be `""` |

## License

Curated content is licensed under [CC BY-NC 4.0](LICENSE) — free to reuse with attribution for non-commercial purposes. The underlying facts (fixtures, fair dates) are not themselves copyrightable.
