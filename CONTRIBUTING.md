# Contributing Profiles to the Profile Hub

The Profile Hub is a GitHub-backed catalog of keybind profiles served via jsDelivr. This repository hosts:

- `manifest.json` — lists games and their profiles.
- `profiles/` — profile JSON files.
- `stats.json` — community stats (downloads/upvotes/downvotes/favorites).

## How to submit
1) Prepare your profile JSON following the KeybindProfile schema (must include `profileData.devices[]`).
2) Add an entry to `manifest.json` under the correct game:
   - Use `gameId`/`gameName` (preferred). `id`/`name` are tolerated but should be normalized.
   - Profile entries should use `path` (preferred) and include `id`, `name`, `type`, `author`, `version`, `description`, `lastUpdated`.
3) Place the profile file at the `path` you referenced (e.g., `profiles/<game>/<id>.json`).

## Validation
- Ensure each profile has:
  - `author`, `version`, `updated` (unix seconds) and `profileData.devices` array.
  - `path` matches an actual file.
- Avoid duplicate `profile.id` within a game.

## Automation
- A Cloudflare Worker handles in-app submissions by committing to this repo.
- `stats.json` is planned to be updated by a GitHub Action (see `.github/workflows/update-stats.yml` template).

## Coding style
- JSON should be minified or consistently formatted; prefer 2-space indentation in the repo.
- Keep keys stable and avoid trailing commas.

## Questions
Open a GitHub issue with details about the game/profile you’re adding.

