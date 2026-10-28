# Monday Karma dungeons

Hand-built battles for Souls Training Ground (Soul Sanctuary Lv. 1-4, 100050-100053)
and Gathering of Souls (Sacred Land of the Souls Lv. 1-3, 100000-100002). They replace
generated stand-ins: all-Imp waves paying at most 110 Karma, and catchable Dilias, Miku and
Mimic bosses. Written by `scripts/gen_karma_dungeon.py`; its docstring explains every number.

| Mission | Energy | Waves | Boss | Most Karma per clear |
|---|---|---|---|---|
| 100050 Soul Sanctuary Lv. 1 | 8 | 6 | Memetes, 27,800 HP | 10,450 |
| 100051 Soul Sanctuary Lv. 2 | 10 | 8 | Hell King Hades, 40,000 HP | 17,610 |
| 100052 Soul Sanctuary Lv. 3 | 13 | 8 | Death God Lodaga, 120,000 HP | 33,940 |
| 100053 Soul Sanctuary Lv. 4 | 15 | 8 | Hellborn Dilias, 240,000 HP | 109,800 |
| 100000 Sacred Land of the Souls Lv. 1 | 13 | 6 | Memetes | 10,450 |
| 100001 Sacred Land of the Souls Lv. 2 | 20 | 8 | Hell King Hades | 17,610 |
| 100002 Sacred Land of the Souls Lv. 3 | 25 | 8 | Death God Lodaga | 33,940 |

"Most Karma" counts every drop and every chest. Each Karma piece drops on a lucky hit, so a
real clear pays less: one emulator clear of Lv. 4 paid 71,100. Nothing in these battles can be
caught.

## Install

Copy the files into `<balance_root>/server/missions/`. The game server picks up a new or
changed file within about 2 seconds, with no rebuild and no restart. Delete a file to serve
the archive record again.

## Test

`scripts/test_karma_dungeon_wire.py` (see its docstring) runs each file against a local
server and checks:
- the waves, HP and Karma fields;
- that nothing can be caught;
- that the Karma chests are in drop_info;
- that MissionEnd credits the Karma.
