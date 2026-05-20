<div align="center">

<pre>
██████╗░░█████╗░██╗░░██╗███████╗███╗░░░███╗███████╗░█████╗░░██╗░░░░░░░██╗
██╔══██╗██╔══██╗██║░██╔╝██╔════╝████╗░████║██╔════╝██╔══██╗░██║░░██╗░░██║
██████╔╝██║░░██║█████═╝░█████╗░░██╔████╔██║█████╗░░██║░░██║░╚██╗████╗██╔╝
██╔═══╝░██║░░██║██╔═██╗░██╔══╝░░██║╚██╔╝██║██╔══╝░░██║░░██║░░████╔═████║░
██║░░░░░╚█████╔╝██║░╚██╗███████╗██║░╚═╝░██║███████╗╚█████╔╝░░╚██╔╝░╚██╔╝░
╚═╝░░░░░░╚════╝░╚═╝░░╚═╝╚══════╝╚═╝░░░░░╚═╝╚══════╝░╚════╝░░░░╚═╝░░░╚═╝░░

░█████╗░██╗░░░██╗████████╗░█████╗░██████╗░██╗░░░░░░█████╗░██╗░░░██╗
██╔══██╗██║░░░██║╚══██╔══╝██╔══██╗██╔══██╗██║░░░░░██╔══██╗╚██╗░██╔╝
███████║██║░░░██║░░░██║░░░██║░░██║██████╔╝██║░░░░░███████║░╚████╔╝░
██╔══██║██║░░░██║░░░██║░░░██║░░██║██╔═══╝░██║░░░░░██╔══██║░░╚██╔╝░░
██║░░██║╚██████╔╝░░░██║░░░╚█████╔╝██║░░░░░███████╗██║░░██║░░░██║░░░
╚═╝░░╚═╝░╚═════╝░░░░╚═╝░░░░╚════╝░╚═╝░░░░░╚══════╝╚═╝░░╚═╝░░░╚═╝░░░
</pre>

[![Version](https://img.shields.io/badge/version-1.9.0-blue?style=for-the-badge)]()
[![Platform](https://img.shields.io/badge/platform-Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)]()
[![Discord](https://img.shields.io/badge/Discord_Server-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/K4vfTbgh2U)
[![Paid App](https://img.shields.io/badge/access-Paid_App-green?style=for-the-badge)]()

**Pokemeow Autoplay is a private paid desktop app for automating PokéMeow gameplay with configurable behavior, license verification, captcha solving, webhooks, and runtime control tools.**

[Features](#-features) &bull; [Installation](#-installation) &bull; [Usage](#-usage) &bull; [Configuration](#%EF%B8%8F-configuration-overview) &bull; [Hotkeys](#-runtime-hotkeys) &bull; [Pricing](#-pricing) &bull; [Changelog](./CHANGELOG.md) &bull; [Warning](#%EF%B8%8F-warning)

</div>

---

> [!CAUTION]
> **Self-bots violate Discord Terms of Service** and can lead to **permanent account termination**.
> Always use an alt account. Use this app entirely at your own risk.

---

## ⚡ Features

<table>
<tr>
<td width="50%">

**🎮 Core Automation**
- Auto hunt Pokémon using the `;p` flow
- Auto fish Pokémon, pull the fish, and throw the selected ball
- Auto battle NPCs or configured user targets
- Auto checklist scan with follow-up actions
- Auto inventory scan across inventory pages
- Auto catchbot start and return-result tracking
- Auto daily reward claim
- Auto daily hunt check and low-rarity reroll
- Auto daily swap token claim

</td>
<td width="50%">

**🧰 Inventory & Resource Automation**
- Auto buy Poké Balls when ball stock is low
- Configurable shop budget and scaled ball purchase ratios
- Auto release duplicate Pokémon and track returned coins
- Auto hatch ready eggs and hold a new egg when available
- Auto open lootboxes after a configurable minimum amount
- Auto use Grazz Berries after a configurable minimum amount
- Auto use Repels after a configurable minimum amount
- Auto quest check, quest reroll filtering, and help request support

</td>
</tr>
<tr>
<td width="50%">

**🎯 Catching Intelligence**
- Rarity-based ball selection for hunting encounters
- Fishing encounter rarity lookup and ball selection
- Pokémon-specific ball overrides for hunting and fishing
- Special ball selection for Pokémon holding items
- Automatic ball downgrade when the preferred ball is unavailable
- Improved fishing state detection for bite, no-nibble, got-away, encounter, and result states
- Legendary, Shiny, and Golden catch/fail webhook notifications
- User-only special webhook notifications for Pokémon-specific ball override encounters
- Catch result parsing for coins, items, tokens, and rarity counts

</td>
<td width="50%">

**🛡️ Safety & Support Tools**
- Paid app access with license verification before Discord connection
- App version display, license status panel, and update notice support
- Captcha detection, download, solving, and submission
- Temporary-ban detection before and after captcha solving
- Human-behavior mode with randomized delays, warm-up timing, distractions, and long breaks
- Runtime pause, statistics view, and task toggle hotkeys
- Session statistics for catches, coins, items, lootboxes, eggs, battles, captcha count, Grazz, Repel, and released Pokémon

</td>
</tr>
</table>

---

## 📥 Installation

### Required Files

| File | Description |
|:-----|:------------|
| `Pokemeow Autoplay v1.9.0.exe` | Main application |
| `settings.yml` | External editable settings file |
| `example.bat` | Launcher template for your session variables and feature toggles |

> Place all files in the **same folder** before running. The app is distributed as a compiled executable; source code is private and is not included with the public app package.

---

## 🚀 Usage

### Quick Start

1. Put `Pokemeow Autoplay v1.9.0.exe`, `settings.yml`, and your launcher `.bat` in the same folder.
2. Edit `settings.yml` to match your preferred automation behavior.
3. Edit `example.bat` and set your session name, Discord token, target channel ID, human-behavior mode, and feature toggles.
4. Run the launcher `.bat`.
5. Keep the app window open while it runs.

> [!WARNING]
> **Never share your Discord token, launcher file, or settings file with anyone.**

---

## ⚙️ Configuration Overview

### Launcher Variables

These values are set in your launcher `.bat` file.

| Variable | Description |
|:---------|:------------|
| `SESSION_NAME` | Display name shown in the app logs |
| `DISCORD_TOKEN` | Your Discord user token; keep it private |
| `CHANNEL_ID` | The Discord channel ID where PokéMeow commands are sent |
| `HUMAN_PLAY` | Enables human-behavior timing when set to `True` |

### Feature Toggles

Set each toggle to `True` or `False` in your launcher `.bat` file.

| Toggle | Description |
|:-------|:------------|
| `ENABLE_HUNTING` | Enables automatic Pokémon catching with `;p` |
| `ENABLE_FISHING` | Enables automatic fishing with `;f` |
| `ENABLE_BATTLE_NPC` | Enables automatic battle runs |
| `ENABLE_EXPLORING` | Reserved launcher toggle for exploration-related automation |
| `ENABLE_AUTO_CATCHBOT` | Enables automatic catchbot start/result handling from checklist |
| `ENABLE_AUTO_HUNT` | Enables daily hunt check and reroll handling from checklist |
| `ENABLE_AUTO_SWAP` | Enables daily swap token claim from checklist |
| `ENABLE_AUTO_BUY_BALLS` | Enables automatic ball purchasing when stock is low |
| `ENABLE_AUTO_RELEASE_DUPLICATES` | Enables automatic duplicate release |
| `ENABLE_AUTO_EGG_HATCH` | Enables egg hatch and egg hold automation |
| `ENABLE_AUTO_LOOTBOX_OPEN` | Enables automatic lootbox opening |
| `ENABLE_AUTO_QUEST_REROLL` | Enables quest checking, reroll filtering, and help request support |
| `ENABLE_AUTO_GRAZZ` | Enables automatic Grazz Berry usage |
| `ENABLE_AUTO_REPEL` | Enables automatic Repel usage |
| `ENABLE_AUTO_DAILY` | Enables automatic daily reward claim |
| `ENABLE_WEBHOOK` | Enables direct webhook notifications for important and special catch results |

### `settings.yml` Options

| Setting | Description |
|:--------|:------------|
| `server_url` | App service URL for captcha and webhook support |
| `max_budget` | Maximum coins the app can spend in one shop run |
| `ball_budget_ratio` | Relative budget ratio for Poké Ball, Great Ball, Ultra Ball, and Master Ball purchases; values are scaled automatically and `0` skips a ball type |
| `min_grazz` | Minimum Grazz Berries required before using all |
| `min_repel` | Minimum Repels required before using all |
| `min_lootbox` | Minimum lootboxes required before opening all |
| `fishing_ball` | Default ball preference for fishing encounters |
| `fishing_shiny_golden_ball` | Ball preference for Shiny/Golden fishing encounters |
| `hunt_item_ball` | Ball preference when a hunted Pokémon is holding an item |
| `webhook_url_success` | Discord webhook URL for successful important catches |
| `webhook_url_failed` | Discord webhook URL for failed important catches |
| `keep_quest_type` | Quest keywords/types that should be kept instead of rerolled |
| `battle_mode` | Battle target mode, such as NPC or user target mode |
| `battle_target` | One or more NPC levels or user IDs; the app chooses one randomly |
| `battle_skills` | Skill rotation used during battle automation |
| `rarity_pokeball_mapping` | Ball preference for each Pokémon rarity |
| `pokemon_pokeball_mapping` | Optional Pokémon-specific ball overrides for normal hunting and fishing encounters; Legendary, Shiny, and Golden encounters still use rarity protection first |

---

## ⌨️ Runtime Hotkeys

Hotkeys are available while the app is sleeping between actions.

| Key | Action |
|:----|:-------|
| `P` | Pause execution until Enter is pressed |
| `S` | Show session statistics, then pause until Enter is pressed |
| `H` | Toggle hunting task on/off |
| `F` | Toggle fishing task on/off |
| `B` | Toggle battle task on/off |

---

## 🧾 App Access & Updates

- Pokemeow Autoplay is a paid public app; source code is private and not distributed.
- The app verifies license status before connecting to Discord.
- The app shows useful status details such as session name, license state, expiry time, remaining time, app version, service version, and captcha solve count.
- Update notices help users know when a newer public build is available.
- If the app provides a download/update link, use it to get the latest public build.

---

## 💳 Pricing

<table>
<tr>
<th align="center">Plan</th>
<th align="center">Duration</th>
<th align="center">Price (USD)</th>
<th align="center">Price (VND)</th>
</tr>
<tr>
<td align="center">⚡ Weekly</td>
<td align="center">7 days</td>
<td align="center"><strong>$1</strong></td>
<td align="center">30,000 ₫</td>
</tr>
<tr>
<td align="center">🔥 Monthly</td>
<td align="center">30 days</td>
<td align="center"><strong>$3</strong></td>
<td align="center">100,000 ₫</td>
</tr>
</table>

> To purchase access or ask questions, join the **[Discord Server](https://discord.gg/K4vfTbgh2U)**.

---

## 📋 Changelog

The full changelog is maintained in **[CHANGELOG.md](./CHANGELOG.md)** and is ordered from newest to oldest.

---

## ⚠️ Warning

- This app is a **self-bot** and violates Discord's Terms of Service.
- Usage may also violate PokéMeow bot rules.
- Account bans, cooldowns, captcha locks, or other losses are possible.
- The developer is **not responsible** for any account bans or losses.
- Always use an **alt account**.

---

<div align="center">

**v1.9.0** &mdash; Pokemeow Autoplay

[![Discord](https://img.shields.io/badge/Join_the_Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/K4vfTbgh2U)

</div>
