# AI Prompt Library

Battle-tested prompt suites for AI-assisted software and game development.
Each prompt is a complete role/method contract — paste it as the system or
opening message and drive an AI coding agent through a full discipline.

## Contents

### [`game-making/`](game-making/)
The **Game Forge** suite — end-to-end native game creation with AI agents:

| Prompt | What it does |
|---|---|
| [Universal Game Forge Master Prompt](game-making/universal-game-forge-master-prompt.md) | Full-cycle game direction, systems design, implementation, validation and distribution in one prompt |
| [Final Diamond Polish](game-making/final-diamond-polish-prompt.md) | Hostile audit, bug hunt, balance review, optimization and gold-master packaging pass |
| [Follow-Up Prompt Toolkit](game-making/game-dev-follow-up-toolkit.md) | Modular follow-ups: retheme/spiritual successor, porting, DLC scope, post-mortems |

Markdown versions are canonical; PDFs are identical print copies.

### [`skyrim-skse/`](skyrim-skse/)
- [SKSE Native Plugin Review Prompt](skyrim-skse/skse-native-plugin-review-prompt.txt) —
  senior C++ reviewer persona for Skyrim SE/AE SKSE plugin modernization
  (VS2022 / MSVC v143 / x64 constraints, legacy-header include rules,
  no-build review workflow).

## How to use

Copy a prompt verbatim into the system/first message of your AI coding session,
then attach your project. Each file is self-contained — no hidden dependencies
between them.

## License

MIT — see [LICENSE](LICENSE).
