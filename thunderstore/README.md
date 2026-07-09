# FullHouse - Bigger Co-op Lobbies for Schedule I

> 🛟 **Need help or found a bug?** Get support at [support.doodesch.de](https://support.doodesch.de).

> **Bigger co-op lobbies.** Vanilla caps you at 4 players - FullHouse raises the cap (32 by default) so more
> friends can join the same game. Drop it in, host, and fill the lobby. Works on its own, no other lobby mod
> needed.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![Game](https://img.shields.io/badge/game-Schedule%20I-purple)
![MelonLoader](https://img.shields.io/badge/MelonLoader-0.7.3+-green)

## Features

- **Bigger lobbies, out of the box.** Raises the co-op cap from 4 to **32 by default**.
- **Configurable capacity.** One setting (`Capacity`, 2-250) sets the lobby size. 32 is the tested default.
- **Standalone.** Does the whole job itself - Steam lobby limit, the game's player list, the invite gate and
  the lobby UI. No other lobby mod required.
- **Plays nice with others.** If you run another cap mod too, FullHouse cooperates - the highest cap wins and
  nothing double-patches.
- **Clients follow the host.** A joining player automatically adopts the host's lobby size, so mismatched
  capacity settings still seat everyone.
- **Light-touch.** Only the lobby layer is touched; no FishNet, saves or gameplay changes.

## Requirements

- **Schedule I** (IL2CPP) with **MelonLoader 0.7.3+**. No other dependencies.
- **Every player in the lobby needs FullHouse** (the host to raise the limit, each client to seat the extras).

## Settings

`Capacity` (default `32`, range 2-250) in `UserData/MelonPreferences.cfg` under `[FullHouse]`. The game was
built for small lobbies, so counts well above 32 can get unstable - start modest.

## License

MIT. See the included LICENSE.md.
