# bf-private-server-data

Curated server data for [bf-private-server](https://github.com/joppe2001/bf-private-server), the
unofficial Brave Frontier revival server. The code repository ships no data; clone this one next
to it to get a server that boots with the full mission, AI, unit and summon catalogs.

> [!IMPORTANT]
> Unofficial fan project for preservation and interoperability. Not affiliated with or endorsed
> by gumi Inc. Brave Frontier and all related names belong to their respective owners. The
> decoded client tables (`mst/`) and the client's art and sound are **not** included here.

## Contents

| Folder | Server config key | What it holds |
|---|---|---|
| [`archive/`](archive/) | `archive_root` | Server-owned curated data: 3,386 missions (`mission.json`) and their per-difficulty variants, 470 enemy AI records (`ai.json`), 2,260 units (`unit.json`), summon gates (`gacha.json`), event and summon rotations, login campaigns, daily logins, Brave Slots, boss drops and the Summoner Journal. |
| [`balance-overlays/`](balance-overlays/) | `balance_root` (optional) | Hand-built replacement battles for specific missions: Fairy Tail, the Juggernaut, Monday Karma dungeons and Trials. |

`mission_sources.json` records where each mission record came from (captured, generated or
hand-built).

## Install

Clone both repositories side by side, then point the server's data roots at this one. From the
code repository's `server/deploy/` directory:

```bash
git clone https://github.com/joppe2001/bf-private-server-data.git ../../../bf-private-server-data
ln -s ../../../bf-private-server-data/archive archive
```

With Docker (`docker/run.sh` mounts only `server/`), copy instead of linking:
`cp -R ../../../bf-private-server-data/archive archive`. Or copy `archive/` in place by hand, or set `archive_root` in `deploy/config.json` to an absolute path.
`system/` (feature switches and fixtures) already ships with the code repository. The decoded client tables go in `mst_root` (`deploy/mst/`); obtain them
separately, see the code repository's [Getting started](https://github.com/joppe2001/bf-private-server/blob/main/docs/GETTING_STARTED.md).

The overlays are optional. To use one, copy its JSON file into
`<balance_root>/server/missions/`; the server picks it up within about 2 seconds without a
restart. The overlay format is documented in the code repository's
[balance overlay spec](https://github.com/joppe2001/bf-private-server/blob/main/server/docs/features/BALANCE_OVERLAYS.md)
and [battle builder notes](https://github.com/joppe2001/bf-private-server/blob/main/server/docs/features/BATTLE_BUILDER.md).

## Regenerating

Most files are generated, not hand-edited. The generators live in the code repository under
`server/scripts/` (`gen_*.py`); each one's docstring names the files it writes. Change the
generator and rerun it rather than editing the JSON, so later regenerations keep your change.

## Versioning

The data tracks the code repository's `main` branch. A server built from an older code commit
may reject fields added later; use data and code from the same date when in doubt.

## Contributing

Corrections to missing or wrong game content are welcome. Open an issue or pull request in the
[code repository](https://github.com/joppe2001/bf-private-server/issues/new/choose) using the
"Missing content" form, and include your source (wiki page, datamine, screenshot).
