# 24th Anniversary (kRO 2026) for Ragnarok Offline

A mod for [Ragnarok Offline](https://github.com/Flux159/ragnarokoffline.app)
(renewal) that adds kRO's 24th anniversary event (24주년 기념, 2026): the
24th Anniversary Coin Exchanger in Prontera hands out the 20 daily Attendance
Boxes and the 24th Anniversary Gift Box, and trades the 24th Anniversary
Coins for potions, buffs, two costume weapons and a Himmelmez wig. A setting
moves the attendance boxes to the game's own Attendance Check window, as on
kRO. No server rebuild or rAthena change is needed.

What each file does, the setting, where it differs from kRO and what to check
in game are in the mod's own [README](anniversary-24th/README.md).

## Installing

Download `anniversary-24th-<version>.zip` from the latest
[release](../../releases/latest), then in the app: Settings → Mods → Install
from a folder…, and pick the zip. Restart the server for the NPC and tables,
and the app for the item text.

## Unverified values

Item names, box contents and item text come from the kRO client (October 2026
build). The attendance table and the Coin Exchanger's list come from gnjoy's
24th anniversary event page; AegisNames and English names from divine-pride.net.
English text for items the boxes hold is ROenglishRE's; the rest is translated
for this mod. Anything not confirmed by two sources is marked `[unverified]`
where it's used:

```sh
grep -rn unverified anniversary-24th/
```

Corrections with a source are welcome, Korean sources and kRO client data first.

## Repository layout

| Path | |
|---|---|
| `anniversary-24th/` | The mod, exactly as it goes in a player's mods folder. |
| `CHANGELOG.md` | One `## <version>` section per release; it becomes the release notes. |
| `scripts/build-release.py` | Checks the mod against the app's limits and builds the release zip. |
| `.github/workflows/` | `check.yml` runs the check on every push; `release.yml` publishes a release when `mod.json` has a new version; `delete-release.yml` (run by hand) removes one. |

## Making a release

1. Change the mod, raise `version` in `anniversary-24th/mod.json`, and add a
   `## <version>` section to `CHANGELOG.md`.
2. `python3 scripts/build-release.py --check`, commit, and push to `main`.

When `main` carries a version that has no release yet, the release workflow
builds `anniversary-24th-<version>.zip` from that commit, tags it `v<version>`, and
publishes it as a full release with that version's changelog section.

## License

GPL-3.0, the same as rAthena. See [LICENSE](LICENSE).
