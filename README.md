# FullHouse - Bigger Co-op Lobbies

> 🛟 **Need help or found a bug?** Get support at [support.doodesch.de/fullhouse](https://support.doodesch.de/fullhouse).

> Vanilla Schedule I caps co-op at 4 players. FullHouse raises that cap so more friends can join the same
> game - drop it in, host, and fill the lobby. It works on its own, needs no other lobby mod, and stays out
> of the way of the ones you already run.

![Version](https://img.shields.io/badge/version-1.1.0-blue)
![Game](https://img.shields.io/badge/game-Schedule%20I-purple)
![MelonLoader](https://img.shields.io/badge/MelonLoader-0.7.3+-green)
![Status](https://img.shields.io/badge/status-working-brightgreen)

## Features

- **Bigger lobbies, out of the box.** Raises the co-op cap from 4 to **32 by default** - host a lobby and
  invite more friends than the base game ever let you.
- **Configurable capacity.** One setting (`Capacity`, 2-250) sets how many players a lobby seats. 32 is the
  tested default; higher works but the game was built for small lobbies, so expect it to get rough.
- **Standalone - no other lobby mod required.** FullHouse does the whole job itself: the Steam lobby member
  limit, the game's internal player list, the invite gate and the lobby UI slots.
- **Plays nice with others.** If you already run another cap mod, FullHouse cooperates instead of fighting -
  the highest cap wins, and it never double-patches or lowers anyone's limit.
- **Clients follow the host.** A joining player automatically adopts the host's lobby size (read from the
  Steam lobby, no extra networking), so mismatched capacity settings still seat everyone the host admits.
- **Light-touch.** It patches the lobby layer (Steam lobby + the game's own `Lobby`/`LobbyInterface`) and
  raises the network transport's client limit so the extra seats can actually be connected into. Saves and
  gameplay are left alone.

## Requirements

| Component | Version / Source |
|---|---|
| Schedule I | IL2CPP (current Steam public build) |
| MelonLoader | `0.7.3+` |

No other dependencies - just MelonLoader. **Every player in the lobby needs FullHouse** (the host to raise
the limit, each client to seat the extra players).

## Installation

### Recommended: a Thunderstore mod manager

Install with r2modman / Gale from the Schedule I community; MelonLoader is pulled in automatically. Make
sure everyone in your group installs it.

### Manual

1. Install **MelonLoader 0.7.3** for Schedule I.
2. Drop **`FullHouse.dll`** into your Schedule I `Mods/` folder.
3. Have every player do the same.

## Configuration

Settings live in `UserData/MelonPreferences.cfg` under `[FullHouse]`.

| Setting | Default | What it does |
|---|---|---|
| `Capacity` | `32` | Maximum players a lobby seats (2-250). Values above 32 are untested and may get unstable. |

Editing the file takes effect on the next launch.

## How it works

The cap is enforced in two places, and both have to move. On the lobby side, FullHouse grows the game's
fixed 4-slot player array to your capacity, raises the Steam lobby member limit once the lobby exists,
opens the invite gate, and clones the lobby UI so all the slots show. On the network side it raises the
transport's own client limit - without that, seats beyond the vanilla count can be occupied in the lobby
but never connected into, and the joining player just waits on the loading screen.

It never replaces the game's lobby creation and adds no networking of its own, which keeps it resilient
across game updates.

The game's world sync and saves were designed around small lobbies, so very high player counts can be rough.
Start modest and see how your session holds up.

## Compatibility

Safe to run alongside other lobby-cap mods - FullHouse only ever raises the cap and coordinates so two mods
never conflict. All players in a lobby should run the same set of mods.

## Where the source lives

This repository has no `.cs` file, which surprises most people who open it. That is deliberate: the entire
engine is one file, [`fullhouse/FullHouse.cs`](https://github.com/DooDesch-Mods/ScheduleOne-Stash/blob/main/fullhouse/FullHouse.cs)
in the public [ScheduleOne-Stash](https://github.com/DooDesch-Mods/ScheduleOne-Stash) repo, and it is
compiled from there rather than copied here. Side Hustle links the same file, so a fix lands in both
without anyone keeping two copies in sync.

To build it yourself, check Stash out next to this repo (`../Stash`) - the project file picks it up from
there, and the release workflow does the same with a checkout subfolder.

## Credits

- **DooDesch** - mod author.

## License

Provided as-is under the [MIT License](LICENSE.md).
