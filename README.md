# bolognalife-content

Curated content served at runtime to the [Bologna Life](https://gitlab.com/marcobotton/bolognalife) Flutter app. Updates here go live the next time someone opens the app — no app release needed.

## What's here

| File | What it is |
|---|---|
| `events.json` | Curated list of city-impacting events in Bologna — sports fixtures, BolognaFiere trade shows, major concerts. The app fetches the raw URL from `main`. |
| `prompts/curate-events.md` | Prompt template for AI-assisted weekly curation. Run with any capable LLM, paste the output into `events.json`, commit. |

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

## Updating

### Manual

1. Edit `events.json` on the web (gitlab.com supports this) or pull, edit locally, push.
2. Commit + push to `main`.
3. Next app launch picks up the change.

### AI-assisted (recommended for weekly batches)

1. Open `prompts/curate-events.md`, fill in `{{date}}` with the start date of the window.
2. Paste into Claude / Duo / your LLM of choice with web access.
3. Review the output against this README's schema.
4. Replace or extend `events.json`. Commit.

## License

The events list is editorial; the curation choices are CC0. The underlying facts (fixtures, fair dates, etc.) come from each team's / venue's public sources and have no copyright claim.
