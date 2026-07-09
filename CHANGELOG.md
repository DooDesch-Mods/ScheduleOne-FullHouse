# Changelog

All notable changes to FullHouse are documented here. This project adheres to
[Semantic Versioning](https://semver.org/).

## [1.0.0] - 2026-07-09

Initial release.

### Added
- Raises the Schedule I co-op lobby cap from the vanilla 4 to a configurable maximum (`Capacity`, default
  32, range 2-250, in MelonPreferences under `[FullHouse]`).
- Standalone: grows the game's fixed player array, raises the Steam lobby member limit after the lobby is
  created, opens the invite gate, and clones the lobby UI slots so all seats show - no other lobby mod needed.
- Cooperative with other lobby-cap mods: only ever raises the cap (never lowers), never replaces the game's
  lobby creation, and a single-flight guard prevents double-patching, so the highest cap simply wins.
- Touches only the Steam lobby and the game's own `Lobby`/`LobbyInterface`; leaves FishNet, saves and
  gameplay untouched.
