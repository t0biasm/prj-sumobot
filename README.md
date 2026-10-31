# prj-sumobot

Software for the Sumo Robot "Black Magic" (ATmega32U4), plus an Arduino Leonardo evaluation application.

| Path | Content |
|---|---|
| `applications/sumobot` | Sumobot application and components (see its README for the SW architecture) |
| `applications/arduinoLeonardo` | Arduino Leonardo kick-off application |
| `emb-toolchain` | submodule: [emb-toolchain](https://github.com/t0biasm/emb-toolchain), compilers and tooling |
| `emb-platform` | submodule: [emb-platform](https://github.com/t0biasm/emb-platform), MCU platform code |

## Getting started
```
git clone https://github.com/t0biasm/prj-sumobot.git
cd prj-sumobot
git submodule update --init            # no --recursive needed: FreeRTOS (C2000) is not used here
```
Create `user.bazelrc` (gitignored) with the Artifactory URL the compilers are downloaded from:
```
common --repo_env=EMB_ARTIFACTORY_URL=https://<host>/artifactory
```
Compiler downloads authenticate via `~/.netrc`. Then:
```
bazel build --config=atmega32u4 //applications/sumobot:app
bazel build --config=atmega32u4 //applications/arduinoLeonardo:app
```
Needs Bazelisk (version in `.bazelversion`).

## Dependencies
Shared repositories are git submodules pinned by commit and wired in `MODULE.bazel` via `local_path_override`. A CI job in the shared repositories builds this project against pending changes, and merged changes are propagated here by a bot.

## Known issues
- `//applications/sumobot/components/sysHwCfg/test` does not build on Linux (`avr8/mcal/test/avr/io.c` includes `<cstdint>` in a C file).
