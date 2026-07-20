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

[![Version](https://img.shields.io/badge/version-2.4.1-blue?style=for-the-badge)]()
[![Platform](https://img.shields.io/badge/platform-Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)]()
[![Discord](https://img.shields.io/badge/Discord_Server-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/K4vfTbgh2U)
[![Paid App](https://img.shields.io/badge/access-Paid_App-green?style=for-the-badge)]()

**A paid Windows client for PokéMeow automation with optional runtime pacing, hunting, fishing, battles, checklist rewards, inventory actions, ball buying, quest handling, webhooks, captcha handling, and runtime statistics.**

[Functions](#main-functions) &bull; [Runtime Pacing](#runtime-pacing) &bull; [Feature Details](#feature-details) &bull; [Setup](#setup) &bull; [Configuration](#configuration) &bull; [Hotkeys](#runtime-hotkeys) &bull; [Pricing](#pricing) &bull; [Warning](#warning)

</div>

---

> [!CAUTION]
> This app automates a Discord user account. The user is solely responsible for their account, commands, tokens, proxy, and all activity performed with the client. The developer does not guarantee uninterrupted service and is not liable for bans, restrictions, captcha locks, lost data, lost access, or any other consequence caused by use of the client.

---

> [!TIP]
> **Need direct captcha assistance?** Try [Meow Captcha on Discord Discovery](https://discord.com/discovery/applications/1502217750444249208).
> It is an external Discord service; review its permissions, terms, privacy policy, and account risks before use.

---

## v2.4.1 Highlights

- Current 2.4.1 client line for long-session autoplay.
- Optional automatic stop after the configured number of valid hunt encounters.
- Startup logs show the configured encounter target and Discord proxy mode.
- Stronger runtime stability for continuous long-session autoplay.
- Optional runtime pacing with timed sessions, breaks, and configurable feature flags.
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
| Battle | Starts the hardcoded `;b npc 1` battle flow and clicks the first available attack button until the fight ends. |
| Checklist | Reads `;cl` and runs supported ready actions such as daily reward, CatchBot, swap token, and daily hunt. |
| Inventory | Scans inventory pages and triggers supported item actions such as eggs, lootboxes, Grazz, Repels, and quests. |
| Ball Shop | Checks coin balance and buys balls based on configured budget ratios when ball stock is low. |
| Duplicate Release | Releases duplicate Pokémon and tracks returned coins. |
| Quest Handling | Reads quests, keeps only the exact `:dexcaught:` quest type, rerolls unwanted quests when reset scrolls are available, and logs readable quest summaries. |
| CatchBot | Starts CatchBot when ready, handles returned rewards, and tracks returned Pokémon counts. |
| Webhooks | Sends important catch/fail notifications for Legendary, Shiny, Golden, and configured special Pokémon encounters. |
| Discord Proxy | Routes Discord gateway, CDN captcha, and direct Discord webhook traffic through the authenticated proxy configured in the launcher. License/API traffic stays direct. |
| Captcha | Detects captcha prompts, solves supported captcha flow faster, and recovers more cleanly after challenge states. |
| Statistics | Tracks catches, encounters, coins, items, tokens, lootboxes, eggs, battles, captcha count, releases, Grazz, Repels, and CatchBot returns. |
| Runtime Pacing | Human-Mode adds optional timed sessions and breaks. It does not prevent account restrictions or guarantee account safety. |

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
- Occasionally skips a hunt cycle or sends a typo before the correct command.
- Parses Pokémon name, rarity, held-item state, and available balls.
- Uses rarity-based ball rules from `settings.yml`.
- Supports Pokémon-specific ball overrides.
- Uses `hunt_item_ball` when a wild Pokémon is holding an item.
- Falls back to another usable ball when the preferred ball is unavailable.
- Occasionally skips or varies normal-ball throws; Legendary, Shiny, and Golden ball choices are never randomized.
- Waits 1-3 seconds immediately before clicking the selected ball.
- Parses catch/fail result.
- Tracks encounter count, catch count, coins, items, and rarity stats.
- Can stop cleanly after the configured number of valid hunt encounters when `STOP_ON_ENCOUNTER_LIMIT=True`.
- Can send webhook notifications for important encounters.
- Queries and logs the first market listing after successful Legendary, Shiny, or Golden catches.

</td>
<td width="50%">

### Fishing

Enable:

```bat
set ENABLE_FISHING=True
```

What it does:

- Sends fishing command `;f`.
- Occasionally skips a fishing cycle or sends a typo before the correct command.
- Waits for fishing state updates.
- Detects no nibble and got-away results.
- Clicks pull when a bite appears.
- Parses the fished Pokémon encounter.
- Looks up fishing rarity from local Pokémon data.
- Applies default fishing ball, rarity ball, and Pokémon-specific override rules.
- Occasionally skips or varies normal-ball throws; Legendary, Shiny, and Golden ball choices are never randomized.
- Waits 1-3 seconds immediately before clicking the selected ball.
- Parses catch/fail result.
- Tracks fish encounters, catches, rarity stats, and fishing tokens.
- Can send webhook notifications for important encounters.
- Queries and logs the first market listing after successful Legendary, Shiny, or Golden catches.

</td>
</tr>
<tr>
<td width="50%">

### Battles

Enable:

```bat
set ENABLE_BATTLE_NPC=True
```

What it does:

- Always starts battle with `;b npc 1`.
- Clicks the first available attack button until the battle ends.
- Detects battle win/end states.
- Tracks battle wins, earned coins, and received items.

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

What it does:

- Detects low Poké Ball or Great Ball stock.
- Checks coin balance.
- Uses `min_budget`, `max_budget`, and `ball_budget_ratio` from `settings.yml`.
- Applies the configured percentage for each ball type to the remaining budget.
- Sends shop buy commands only when the budget can buy at least one ball.
- Waits for the configured scheduler interval before checking again after an insufficient-budget run.

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

What it does:

- Sends `;q`.
- Reads quest lines from the quest embed.
- Converts emoji quest types into readable labels.
- Keeps only quests whose parsed type is exactly `:dexcaught:`.
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

## Runtime Pacing

Enable:

```bat
set ENABLE_HUMAN_MODE=True
```

Human Mode is an optional runtime pacing mode for long unattended sessions. It alternates timed activity sessions with longer breaks and occasional micro-breaks.

What it does:

- Runs the normal scheduler continuously while enabled.
- Alternates timed active sessions with longer rest periods.
- Occasionally takes a short micro-break before a scheduled command.

> Runtime pacing does not prevent account restrictions or remove the risks of automation.

---

## Human-Mode And Bot-Mode

```bat
set ENABLE_HUMAN_MODE=True
```

Human-Mode enables the optional runtime pacing described above.

```bat
set ENABLE_HUMAN_MODE=False
```

Bot-Mode follows the scheduler more directly and is easier to predict when testing. It does not use the optional runtime pacing layer.

Both modes use the same core automation features. The difference is how the runtime session is paced.

---

## Setup

This guide is for the packaged Windows client:

```text
Pokemeow Autoplay v2.4.1.exe
```

Recommended release folder:

```text
Pokemeow Autoplay/
  Pokemeow Autoplay v2.4.1.exe
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
4. Fill in `SESSION_NAME`, `DISCORD_TOKEN`, and `CHANNEL_ID`; `PROXY_IP` is optional.
5. Turn feature toggles on or off.
6. Double-click the launcher `.bat`.

Launcher example:

```bat
@echo off
set SESSION_NAME=Hunter
set DISCORD_TOKEN=YOUR_DISCORD_TOKEN
set CHANNEL_ID=YOUR_CHANNEL_ID
set PROXY_IP=
set ENABLE_HUMAN_MODE=True

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
set STOP_ON_DAILY_LIMIT=False
set STOP_ON_ENCOUNTER_LIMIT=False

cd /d "%~dp0.."
"Pokemeow Autoplay v2.4.1.exe"
pause
```

If the app filename changes, update the final command:

```bat
"Pokemeow Autoplay vX.X.X.exe"
```

---

## Build Release Package

Run `build_release.bat` from the repository root. The script reads the
release version from the version badge in this README, checks that the same
version exists in `CHANGELOG.md`, builds the executable, and packages the
current release files.

Required build environment:

- `.venv-build\Scripts\python.exe`
- Nuitka installed in the build environment
- `assets\masterball.ico`
- `data\pokemon_info.json`

Build modes:

```bat
build_release.bat 1
```

Build the release folder only.

```bat
build_release.bat 2
```

Create a ZIP from an existing release folder.

```bat
build_release.bat 3
```

Build the release folder and ZIP package.

The generated package contains exactly these current files:

```text
release/
  Pokemeow Autoplay v2.4.1/
    Pokemeow Autoplay v2.4.1.exe
    README.md
    CHANGELOG.md
    settings.example.yml
    run/
      example.bat
```

The package launcher is copied from `run/example.bat`; the build script only
replaces its final `python main.py` command with the generated executable
name. Any later changes to the example launcher, YAML template, README, or
changelog are therefore included automatically in the next build.

---

## Configuration

### Launcher Variables

| Variable | Description |
|:--|:--|
| `SESSION_NAME` | Name shown for this running session |
| `DISCORD_TOKEN` | Discord user token |
| `CHANNEL_ID` | Channel where commands are sent |
| `PROXY_IP` | Optional authenticated HTTP proxy for Discord gateway, CDN, and webhook traffic; leave empty for direct mode; format `HOST:PORT:USERNAME:PASSWORD` |
| `ENABLE_HUMAN_MODE` | `True` for Human-Mode, `False` for Bot-Mode |
| `STOP_ON_DAILY_LIMIT` | `True` to stop the app when the daily catch limit is reached; `False` to disable the blocked command for the current session |
| `STOP_ON_ENCOUNTER_LIMIT` | `True` to stop after the hunt encounter limit in `settings.yml`; `False` to leave the scheduler running |

Enabled value:

```text
True
```

Every other value, including different casing, is disabled. Missing feature flags are disabled.

`PROXY_IP` is optional. If it is missing or empty, Discord runs in direct mode.
If it is present, it must use the exact format `HOST:PORT:USERNAME:PASSWORD`;
an invalid value stops startup. A valid proxy is used for Discord gateway,
Discord CDN captcha downloads, and direct Discord webhooks. License/API
requests and server webhooks remain direct.

At startup, Discord mode is logged as `[Discord] Proxy: HOST:PORT` or
`[Discord] Proxy: None`. Proxy credentials are never printed.

At startup, the encounter limit is logged as `[Encounter Limit] Target: N`
when enabled or `[Encounter Limit] Target: None` when disabled. Reaching the
enabled target logs `[Encounter Limit] Reached: N/N`, prints statistics, and
closes Discord.

### settings.yml Options

| Setting | Description |
|:--|:--|
| `server_url` | Service URL provided with the app |
| `encounter_limit` | Required session hunt encounter limit; integer `>= 1` |
| `min_grazz` | Minimum Grazz Berries before using all |
| `min_repel` | Minimum Repels before using all |
| `min_lootbox` | Minimum lootboxes before opening all |
| `min_budget` | Minimum Pokecoins budget before auto-buy runs |
| `max_budget` | Maximum Pokecoins budget used by auto-buy |
| `ball_budget_ratio` | Exact percentage mapping for the remaining auto-buy budget |
| `fishing_ball` | Default ball for normal fishing encounters |
| `fishing_shiny_golden_ball` | Ball for rare fishing encounters when no stronger rule applies |
| `hunt_item_ball` | Ball for hunted Pokémon holding an item |
| `webhook_url_success` | Webhook for successful important catches |
| `webhook_url_failed` | Webhook for failed important catches |
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

### Proxy authentication fails

If `PROXY_IP` is empty, direct mode is expected. If it has a value, check that
it contains exactly four non-empty parts and that the proxy account is valid. A
`407` error means the proxy rejected authentication; the client does not fall
back to direct mode when a proxy value is configured.

---

## Changelog

See [CHANGELOG.md](./CHANGELOG.md) for public update notes.

---

## Warning

- This app automates a Discord user account.
- The user is solely responsible for their account, token, proxy, configuration, commands, and activity.
- The user must comply with Discord, PokéMeow, and applicable third-party rules.
- Account bans, restrictions, captcha locks, cooldowns, data loss, and loss of access are possible.
- The developer provides no account-safety guarantee and is not liable for any consequence of use.
- Use an alternate account only if the user accepts these risks.

---

<div align="center">

**v2.4.1** &mdash; Pokemeow Autoplay

[![Discord](https://img.shields.io/badge/Join_the_Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/K4vfTbgh2U)

</div>
