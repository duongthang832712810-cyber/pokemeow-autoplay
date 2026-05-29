<div align="center">

<pre>
██████╗  ██████╗ ██╗  ██╗███████╗███╗   ███╗███████╗ ██████╗ ██╗    ██╗
██╔══██╗██╔═══██╗██║ ██╔╝██╔════╝████╗ ████║██╔════╝██╔═══██╗██║    ██║
██████╔╝██║   ██║█████╔╝ █████╗  ██╔████╔██║█████╗  ██║   ██║██║ █╗ ██║
██╔═══╝ ██║   ██║██╔═██╗ ██╔══╝  ██║╚██╔╝██║██╔══╝  ██║   ██║██║███╗██║
██║     ╚██████╔╝██║  ██╗███████╗██║ ╚═╝ ██║███████╗╚██████╔╝╚███╔███╔╝
╚═╝      ╚═════╝ ╚═╝  ╚═╝╚══════╝╚═╝     ╚═╝╚══════╝ ╚═════╝  ╚══╝╚══╝ 
                                                                       
 █████╗ ██╗   ██╗████████╗ ██████╗ ██████╗ ██╗      █████╗ ██╗   ██╗   
██╔══██╗██║   ██║╚══██╔══╝██╔═══██╗██╔══██╗██║     ██╔══██╗╚██╗ ██╔╝   
███████║██║   ██║   ██║   ██║   ██║██████╔╝██║     ███████║ ╚████╔╝    
██╔══██║██║   ██║   ██║   ██║   ██║██╔═══╝ ██║     ██╔══██║  ╚██╔╝     
██║  ██║╚██████╔╝   ██║   ╚██████╔╝██║     ███████╗██║  ██║   ██║      
╚═╝  ╚═╝ ╚═════╝    ╚═╝    ╚═════╝ ╚═╝     ╚══════╝╚═╝  ╚═╝   ╚═╝      
</pre>

[![Version](https://img.shields.io/badge/version-2.0.0-blue?style=for-the-badge)]()
[![Platform](https://img.shields.io/badge/platform-Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)]()
[![Discord](https://img.shields.io/badge/Discord_Server-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/K4vfTbgh2U)
[![Paid App](https://img.shields.io/badge/access-Paid_App-green?style=for-the-badge)]()

**A paid Windows client for 24/7 PokéMeow automation with Anti-Ban pacing, hunting, fishing, battles, checklist rewards, inventory actions, ball buying, quest handling, webhooks, captcha handling, and runtime statistics.**

[Functions](#main-functions) &bull; [Anti-Ban](#anti-ban-247-mode) &bull; [Feature Details](#feature-details) &bull; [Setup](#setup) &bull; [Configuration](#configuration) &bull; [Hotkeys](#runtime-hotkeys) &bull; [Pricing](#pricing) &bull; [Warning](#warning)

</div>

---

> [!CAUTION]
> This app automates a Discord user account. Discord and PokéMeow may restrict accounts for automated activity. Use an alternate account and accept the risk before running the client.

---

## v2.0.0 Highlights

- New 2.0.0 client line for long-session autoplay.
- Stronger 24/7 runtime stability for continuous long-session autoplay.
- Upgraded Anti-Ban pacing for smoother extended sessions with less repetitive behavior.
- Faster captcha solve flow with cleaner recovery after challenge states.
- Better handling for wait, retry, cooldown, refresh, and temporary anti-abuse responses.
- Improved scheduler reliability across hunting, fishing, battles, checklist, inventory, release, and shop automation.
- Cleaner runtime state handling so unavailable features do not spam repeated failed actions during the same session.

---

## Main Functions

| Area | What The Tool Does |
|:--|:--|
| Hunting | Sends `;p`, reads the wild Pokémon, chooses a ball, catches, parses result, updates stats, and sends webhook alerts when configured. |
| Fishing | Sends `;f`, handles bite/pull flow, detects no-nibble/got-away states, catches fish encounters, tracks tokens, and applies ball rules. |
| Battle | Starts battles against configured NPC/user targets and rotates configured skills until the fight ends. |
| Checklist | Reads `;cl` and runs supported ready actions such as daily reward, CatchBot, swap token, and daily hunt. |
| Inventory | Scans inventory pages and triggers supported item actions such as eggs, lootboxes, Grazz, Repels, and quests. |
| Ball Shop | Checks coin balance and buys balls based on configured budget ratios when ball stock is low. |
| Duplicate Release | Releases duplicate Pokémon and tracks returned coins. |
| Quest Handling | Reads quests, keeps preferred quest types, rerolls unwanted quests when reset scrolls are available, and logs readable quest summaries. |
| CatchBot | Starts CatchBot when ready, handles returned rewards, and tracks returned Pokémon counts. |
| Webhooks | Sends important catch/fail notifications for Legendary, Shiny, Golden, and configured special Pokémon encounters. |
| Captcha | Detects captcha prompts, solves supported captcha flow faster, and recovers more cleanly after challenge states. |
| Statistics | Tracks catches, encounters, coins, items, tokens, lootboxes, eggs, battles, captcha count, releases, Grazz, Repels, and CatchBot returns. |
| Anti-Ban 24/7 | Human-Mode adds advanced pacing, challenge-resilience handling, behavior variation, and safer runtime control for long sessions. |

---

## Feature Details

<table>
<tr>
<td width="50%">

### Hunting

Enable:

```bat
set ENABLE_HUNTING=True
```

What it does:

- Sends normal hunt command `;p`.
- Parses Pokémon name, rarity, held-item state, and available balls.
- Uses rarity-based ball rules from `settings.yml`.
- Supports Pokémon-specific ball overrides.
- Uses `hunt_item_ball` when a wild Pokémon is holding an item.
- Falls back to another usable ball when the preferred ball is unavailable.
- Parses catch/fail result.
- Tracks encounter count, catch count, coins, items, and rarity stats.
- Can send webhook notifications for important encounters.

</td>
<td width="50%">

### Fishing

Enable:

```bat
set ENABLE_FISHING=True
```

What it does:

- Sends fishing command `;f`.
- Waits for fishing state updates.
- Detects no nibble and got-away results.
- Clicks pull when a bite appears.
- Parses the fished Pokémon encounter.
- Looks up fishing rarity from local Pokémon data.
- Applies default fishing ball, rarity ball, and Pokémon-specific override rules.
- Parses catch/fail result.
- Tracks fish encounters, catches, rarity stats, and fishing tokens.
- Can send webhook notifications for important encounters.

</td>
</tr>
<tr>
<td width="50%">

### Battles

Enable:

```bat
set ENABLE_BATTLE_NPC=True
```

Settings:

```yml
battle_mode: npc
battle_target:
  - 1
  - 2
  - 3
battle_skills:
  - 1
  - 2
  - 1
```

What it does:

- Starts battle with one random configured target.
- Supports NPC mode and user target mode when configured.
- Rotates through configured skill buttons.
- Detects battle win/end states.
- Tracks battle wins and earned coins when available.
- Disables battle for the current session if requirements are missing.

</td>
<td width="50%">

### Checklist Actions

Checklist is always scheduled. Follow-up actions depend on toggles:

```bat
set ENABLE_AUTO_DAILY=True
set ENABLE_AUTO_CATCHBOT=True
set ENABLE_AUTO_SWAP=True
set ENABLE_AUTO_HUNT=True
```

What it does:

- Sends `;cl`.
- Reads ready checklist items.
- Claims daily reward when ready.
- Starts or processes CatchBot when ready.
- Claims daily swap token when ready.
- Checks daily hunt and rerolls low-rarity daily hunt targets when enabled.
- Stops the checklist chain cleanly if a child action needs retry, disable, or stop.

</td>
</tr>
<tr>
<td width="50%">

### Inventory Actions

Inventory is scheduled and can trigger several optional features:

```bat
set ENABLE_AUTO_EGG_HATCH=True
set ENABLE_AUTO_LOOTBOX_OPEN=True
set ENABLE_AUTO_GRAZZ=True
set ENABLE_AUTO_REPEL=True
set ENABLE_AUTO_QUEST_REROLL=True
```

What it does:

- Sends `;inv`.
- Reads inventory pages.
- Finds supported items and counts.
- Hatches ready eggs and holds a new egg when available.
- Opens lootboxes when count reaches `min_lootbox`.
- Uses Grazz Berries when count reaches `min_grazz`.
- Uses Repels when count reaches `min_repel`.
- Runs quest handling when quest reroll is enabled.

</td>
<td width="50%">

### Ball Shop

Enable:

```bat
set ENABLE_AUTO_BUY_BALLS=True
```

Settings:

```yml
max_budget: 200000
min_budget: 2000
ball_budget_ratio:
  pokeball: 85
  greatball: 45
  ultraball: 10
  masterball: 0
```

What it does:

- Detects low Poké Ball or Great Ball stock.
- Checks coin balance.
- Skips buying when budget is below `min_budget`.
- Caps spending by `max_budget`.
- Splits budget by `ball_budget_ratio`.
- Skips any ball type set to `0`.
- Sends shop buy commands only when the budget can buy at least one ball.
- Temporarily backs off if there are not enough coins.

</td>
</tr>
<tr>
<td width="50%">

### Duplicate Release

Enable:

```bat
set ENABLE_AUTO_RELEASE_DUPLICATES=True
```

What it does:

- Sends duplicate release command.
- Parses returned coin result when available.
- Tracks released Pokémon count.
- Tracks coins received from release.
- Disables release for the current session if requirements or limits block the action.

</td>
<td width="50%">

### Quest Handling

Enable:

```bat
set ENABLE_AUTO_QUEST_REROLL=True
```

Settings:

```yml
keep_quest_type:
  - Receive
  - ":dexcaught:"
  - oldrod
```

What it does:

- Sends `;q`.
- Reads quest lines from the quest embed.
- Converts emoji quest types into readable labels.
- Keeps quests matching `keep_quest_type`.
- Uses quest reset scrolls to reroll unwanted quests.
- Logs compact quest summaries such as `#1: oldrod | #2: Receive`.
- Can request quest help when supported by the running state.

</td>
</tr>
<tr>
<td width="50%">

### CatchBot

Enable:

```bat
set ENABLE_AUTO_CATCHBOT=True
```

What it does:

- Runs from checklist when CatchBot is ready or returned.
- Sends `;cb run`.
- Handles returned rewards.
- Starts CatchBot when enough coins are available.
- Detects not-enough-money and already-running states.
- Tracks returned Pokémon by rarity when reward data is available.

</td>
<td width="50%">

### Webhooks

Enable:

```bat
set ENABLE_WEBHOOK=True
```

Settings:

```yml
webhook_url_success: ""
webhook_url_failed: ""
```

What it does:

- Sends notifications for important successful catches.
- Sends notifications for important failed catches.
- Supports Legendary, Shiny, and Golden encounters.
- Supports configured Pokémon-specific special encounters.
- Keeps webhook URLs outside the launcher file.

</td>
</tr>
</table>

---

## Anti-Ban 24/7 Mode

Enable:

```bat
set HUMAN_PLAY=True
```

Anti-Ban 24/7 Mode is built for long unattended sessions. It keeps the normal farm loop running while adding a private behavior-control layer designed to make runtime activity look less mechanical, improve challenge resilience, and reduce account-flagging risk.

What it does:

- Runs normal scheduled farming continuously.
- Uses adaptive timing instead of simple fixed delays.
- Adds session-level pacing for 24/7 farming.
- Reduces repetitive action patterns that commonly make automation easier to detect.
- Improves recovery after captcha, cooldown, wait, refresh, and temporary anti-abuse responses.
- Helps lower bot-check and account-flagging risk during long runtime.
- Automatically falls back to normal farming when optional protection behavior is unavailable.

> Anti-Ban mode reduces risk for 24/7 automation, but no automation tool can remove all account restriction risk.

---

## Human-Mode And Bot-Mode

```bat
set HUMAN_PLAY=True
```

Human-Mode enables the Anti-Ban 24/7 behavior layer described above.

```bat
set HUMAN_PLAY=False
```

Bot-Mode follows the scheduler more directly and is easier to predict when testing. It does not use the advanced Anti-Ban 24/7 behavior layer.

Both modes use the same core automation features. The difference is how the runtime session is paced.

---

## Setup

This guide is for the packaged Windows client:

```text
Pokemeow Autoplay v2.0.0.exe
```

Recommended release folder:

```text
Pokemeow Autoplay/
  Pokemeow Autoplay v2.0.0.exe
  README.md
  CHANGELOG.md
  settings.example.yml
  run/
    example.bat
```

Quick setup:

1. Put the `.exe`, `README.md`, `CHANGELOG.md`, `settings.example.yml`, and `run` folder together.
2. Copy `settings.example.yml` to `settings.yml`.
3. Copy `run/example.bat` to a personal launcher such as `run/Hunter.bat`.
4. Fill in `SESSION_NAME`, `DISCORD_TOKEN`, and `CHANNEL_ID`.
5. Turn feature toggles on or off.
6. Double-click the launcher `.bat`.

Launcher example:

```bat
@echo off
set SESSION_NAME=Hunter
set DISCORD_TOKEN=YOUR_DISCORD_TOKEN
set CHANNEL_ID=YOUR_CHANNEL_ID
set HUMAN_PLAY=True

set ENABLE_AUTO_BUY_BALLS=True
set ENABLE_AUTO_RELEASE_DUPLICATES=True
set ENABLE_AUTO_EGG_HATCH=True
set ENABLE_AUTO_LOOTBOX_OPEN=True
set ENABLE_AUTO_QUEST_REROLL=True
set ENABLE_FISHING=True
set ENABLE_BATTLE_NPC=True
set ENABLE_HUNTING=True
set ENABLE_WEBHOOK=True
set ENABLE_AUTO_GRAZZ=True
set ENABLE_AUTO_REPEL=True
set ENABLE_AUTO_DAILY=True
set ENABLE_AUTO_CATCHBOT=True
set ENABLE_AUTO_SWAP=True
set ENABLE_AUTO_HUNT=True

cd /d "%~dp0.."
"Pokemeow Autoplay v2.0.0.exe"
pause
```

If the app filename changes, update the final command:

```bat
"Pokemeow Autoplay vX.X.X.exe"
```

---

## Configuration

### Launcher Variables

| Variable | Description |
|:--|:--|
| `SESSION_NAME` | Name shown for this running session |
| `DISCORD_TOKEN` | Discord user token |
| `CHANNEL_ID` | Channel where commands are sent |
| `HUMAN_PLAY` | `True` for Human-Mode, `False` for Bot-Mode |

Accepted enabled values:

```text
1, true, yes, on
```

Everything else is treated as disabled, except `HUMAN_PLAY`, which defaults to enabled when missing.

### settings.yml Options

| Setting | Description |
|:--|:--|
| `server_url` | Service URL provided with the app |
| `max_budget` | Maximum coins allowed for one shop run |
| `min_budget` | Minimum budget required before auto-buy runs |
| `ball_budget_ratio` | Relative budget split for ball purchases |
| `min_grazz` | Minimum Grazz Berries before using all |
| `min_repel` | Minimum Repels before using all |
| `min_lootbox` | Minimum lootboxes before opening all |
| `fishing_ball` | Default ball for normal fishing encounters |
| `fishing_shiny_golden_ball` | Ball for rare fishing encounters when no stronger rule applies |
| `hunt_item_ball` | Ball for hunted Pokémon holding an item |
| `webhook_url_success` | Webhook for successful important catches |
| `webhook_url_failed` | Webhook for failed important catches |
| `keep_quest_type` | Quest types that should not be rerolled |
| `battle_mode` | Battle mode, such as `npc` or `user` |
| `battle_target` | Battle targets the app may choose from |
| `battle_skills` | Battle skill rotation; use only skills available for the selected battle target |
| `rarity_pokeball_mapping` | Ball preference by rarity |
| `pokemon_pokeball_mapping` | Ball override for specific Pokémon |

Accepted ball names:

```text
pokeball
greatball
ultraball
premierball
masterball
```

Plural forms are accepted too.

---

## Runtime Hotkeys

Hotkeys are available while the app is waiting between actions.

| Key | Action |
|:--|:--|
| `P` | Pause until Enter is pressed |
| `S` | Show session statistics, then pause until Enter is pressed |
| `H` | Toggle hunting on/off |
| `F` | Toggle fishing on/off |
| `B` | Toggle battle on/off |

---

## Common Runtime Protection

The client can react to common blocking states:

- Please-wait cooldowns.
- Spawned Pokémon pending states.
- Catch/fish cooldown-ready messages.
- Missing balls.
- Missing fishing rod.
- Battle requirement missing.
- Daily limits.
- Vote requirements.
- New-account warnings.
- Temporary ban warnings.
- Captcha prompts.

When a feature is blocked for the current session, the client may disable that feature until restart instead of repeating the same failed action.

---

## Pricing

<table>
<tr>
<th align="center">Plan</th>
<th align="center">Duration</th>
<th align="center">Price (USD)</th>
<th align="center">Price (VND)</th>
</tr>
<tr>
<td align="center">Weekly</td>
<td align="center">7 days</td>
<td align="center"><strong>$2</strong></td>
<td align="center">40,000 ₫</td>
</tr>
<tr>
<td align="center">Monthly</td>
<td align="center">30 days</td>
<td align="center"><strong>$4</strong></td>
<td align="center">80,000 ₫</td>
</tr>
<tr>
<td align="center">Yearly</td>
<td align="center">365 days</td>
<td align="center"><strong>$40</strong></td>
<td align="center">800,000 ₫</td>
</tr>
</table>

Discord support:

https://discord.gg/K4vfTbgh2U

---

## Troubleshooting

### App closes immediately

Run the launcher `.bat` instead of double-clicking the `.exe`. The `pause` line keeps the window open so you can read the error.

### settings.yml not found

Put `settings.yml` beside the `.exe`, then start the app from the launcher.

### No commands are sent

Check:

- `DISCORD_TOKEN`
- `CHANNEL_ID`
- the account can see the channel
- feature toggles are set to `True`
- PokéMeow is available in that channel

### A feature disables itself

Check the related requirement: balls, rod, battle team, daily limit, vote state, or account state. Fix the requirement and restart the app.

### Webhook does not send

Check:

- `ENABLE_WEBHOOK=True`
- webhook URL is not empty
- webhook URL is valid
- the Discord webhook channel still exists

---

## Changelog

See [CHANGELOG.md](./CHANGELOG.md) for public update notes.

---

## Warning

- This app automates a Discord user account.
- Discord or PokéMeow may restrict automated activity.
- Account bans, captcha locks, cooldowns, or other losses are possible.
- The developer is not responsible for account restrictions or losses.
- Use an alternate account.

---

<div align="center">

**v2.0.0** &mdash; Pokemeow Autoplay

[![Discord](https://img.shields.io/badge/Join_the_Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/K4vfTbgh2U)

</div>
