# Games Expert

Portable, version-aware gaming expertise for **Codex**, **Claude Code**, and **Gemini CLI**.

Games Expert is an extensible collection of focused Agent Skills that helps AI assistants answer gameplay questions with the right game, mode, platform, progression stage, and patch context. It keeps stable game knowledge local while directing time-sensitive questions—such as patches, seasons, rotations, events, prices, and current meta—to fresh sources.

No API keys, background services, or runtime dependencies are required.

## Supported games

| Game | Typical topics |
| --- | --- |
| Minecraft | Java vs. Bedrock, survival, crafting, farms, redstone, commands, enchanting |
| Fortnite | Battle Royale, Zero Build, loadouts, quests, Creative, UEFN |
| GTA V / GTA Online | Missions, businesses, heists, vehicles, progression, weekly changes |
| League of Legends | Champions, roles, builds, runes, matchups, macro, ranked improvement |
| VALORANT | Agents, maps, utility, economy, aim, team compositions, ranked play |
| Counter-Strike 2 | Maps, weapons, economy, utility, Premier, settings, demo review |
| Roblox | Experience-specific help, Roblox Studio, Luau, publishing, platform safety |
| Elden Ring | Builds, stats, bosses, quests, exploration, endings, Shadow of the Erdtree |
| Whiteout Survival | Heroes, generations, formations, Fire Crystal, rallies, events, SvS, F2P planning |

## Why separate skills?

Each game has its own skill and reference material. The assistant loads only the relevant game context instead of injecting one large gaming prompt into every conversation. This improves routing, reduces irrelevant context, and makes each game easier to maintain independently.

The plugin does **not** retrain or fine-tune the underlying model. It supplies reusable instructions, decision rules, source guidance, and domain references at answer time.

## Install

### Codex and ChatGPT desktop

Add the GitHub repository as a plugin marketplace, then install the plugin:

```bash
codex plugin marketplace add erhan/games-expert
codex plugin add games-expert@games-expert
```

Restart the desktop app or begin a new conversation after installation so the skills are discovered.

### Claude Code

Add the repository as a marketplace and install the plugin:

```bash
claude plugin marketplace add erhan/games-expert
claude plugin install games-expert@games-expert
```

For local development without installing:

```bash
git clone https://github.com/erhan/games-expert.git
claude --plugin-dir ./games-expert
```

### Gemini CLI

Install the repository as a Gemini CLI extension:

```bash
gemini extensions install https://github.com/erhan/games-expert.git --auto-update
```

Restart Gemini CLI after installation. Gemini discovers the Agent Skills in the root `skills/` directory.

For local development:

```bash
git clone https://github.com/erhan/games-expert.git
gemini extensions link ./games-expert
```

## Usage examples

The skills are designed for automatic invocation. Ask naturally:

- “I am at Furnace 30 and mostly F2P in Whiteout Survival. What should I save for SvS?”
- “Review my Gen 3 Whiteout Survival heroes and suggest a Bear Hunt formation.”
- “Design a reliable iron farm for Minecraft Java and list the materials.”
- “Give me a low-spoiler Elden Ring strength build for level 80.”
- “How should I play this VALORANT retake with a controller?”
- “Create a four-week League of Legends improvement plan for a Gold support player.”

For better answers, include relevant details such as the game version, platform, mode, rank, progression stage, state age, hero generation, spending style, or spoiler preference.

## Accuracy and freshness

The shared source policy instructs assistants to:

- separate stable mechanics from version-sensitive information;
- verify patches, seasons, rotations, events, prices, codes, and current meta;
- prefer official patch notes, support pages, and developer documentation;
- label community-derived strategy and avoid inventing exact values;
- distinguish platform, edition, mode, server, state age, and progression differences;
- avoid cheats, account theft, exploit automation, and real-money trading fraud.

Game publishers change live-service systems frequently. Always verify high-cost or irreversible in-game decisions against the current game client and official announcements.

## Project structure

```text
games-expert/
├── plugin.json                     # Portable Agent Plugins manifest
├── .codex-plugin/plugin.json       # Codex compatibility manifest
├── .agents/plugins/marketplace.json
├── .claude-plugin/
│   ├── plugin.json
│   └── marketplace.json
├── gemini-extension.json
├── references/source-policy.md
└── skills/
    ├── whiteout-survival-expert/
    ├── minecraft-expert/
    └── ...
```

## Contributing

Contributions are welcome. Useful contributions include:

- a focused skill for another game;
- corrections to outdated or ambiguous guidance;
- better official source links;
- clearer routing between editions, modes, platforms, or progression stages.

Keep skills concise. Put game-specific details in that game's `references/` directory, keep time-sensitive claims out of static instructions, and include official sources whenever possible.

## Disclaimer

This is an independent community project. It is not affiliated with, endorsed by, or sponsored by the publishers or developers of the supported games. All game names and trademarks belong to their respective owners.

## License

[MIT](LICENSE) © 2026 Erhan BÜTE
