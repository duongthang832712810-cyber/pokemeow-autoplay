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

[![Version](https://img.shields.io/badge/version-1.06-blue?style=for-the-badge)]()
[![Python](https://img.shields.io/badge/python-3.10+-yellow?style=for-the-badge&logo=python&logoColor=white)]()
[![Discord](https://img.shields.io/badge/Discord_Server-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/K4vfTbgh2U)
[![License](https://img.shields.io/badge/license-Paid_(Key_Required)-green?style=for-the-badge)]()

**Auto-catch Pokémon with fully customizable settings, multi-account support, captcha solving, and more.**

[Features](#-features) &bull; [Installation](#-installation) &bull; [Usage](#-usage) &bull; [Config](#%EF%B8%8F-config-overview) &bull; [Flags](#-flags) &bull; [Pricing](#-pricing) &bull; [Changelog](#-changelog) &bull; [Warning](#%EF%B8%8F-warning)

</div>

---

> [!CAUTION]
> **Self-bots violate Discord Terms of Service** and can lead to **permanent account termination**.
> Always use an alt account. Use entirely at your own risk.

---

## ⚡ Features

<table>
<tr>
<td width="50%">

**🎮 Core Automation**
- Auto hunt Pokémon
- Auto fish Pokémon
- Auto battle NPC
- Auto buy Ball
- Auto check, reroll & send help quest
- Auto check & hatch egg
- Auto catchbot
- Auto lootbox

</td>
<td width="50%">

**🛠️ Utilities & Support**
- Auto repel
- Auto claim daily reward
- Auto release duplicate Pokémon
- Auto grazz
- Auto hunt and swap
- Auto solve captcha
- Support webhook notify
- Support human-behavior actions

</td>
</tr>
</table>

---

## 📥 Installation

### Required Files

| File | Description |
|:-----|:------------|
| `Pokemeow Autoplay.exe` | Main application |
| `config.yml` | Main configuration file |
| `example.bat` | Launcher template |

> Place all files in the **same folder** before running.

---

## 🚀 Usage

### Quick Start

1. Edit `config.yml` to match your preferences
2. Edit `example.bat` — set your token, channel ID, session name, and toggle any flags
3. Double-click `example.bat` to launch

> [!WARNING]
> **Never share your token**, config file, or key with anyone.

---

## ⚙️ Config Overview

| Key | Description |
|:----|:------------|
| `DISCORD_TOKEN` | Your Discord token — keep this private |
| `CHANNEL_ID` | The PokéMeow channel to run in |
| `SESSION_NAME` | Label shown in logs for this session |

---

## 🚩 Flags

All flags are set inside `example.bat` as environment variables. Set each to `True` or `False`.

### Identity

| Flag | Default | Description |
|:-----|:-------:|:------------|
| `SESSION_NAME` | — | Display name for this session in logs |
| `DISCORD_TOKEN` | — | Your Discord user token |
| `CHANNEL_ID` | — | Channel ID to run the bot in |
| `HUMAN_PLAY` | `False` | Enable human-behavior simulation (random delays, natural timing) |

### Feature Toggles

| Flag | Default | Description |
|:-----|:-------:|:------------|
| `ENABLE_HUNTING` | `True` | Auto hunt Pokémon |
| `ENABLE_FISHING` | `True` | Auto fish Pokémon |
| `ENABLE_BATTLE_NPC` | `True` | Auto battle NPC |
| `ENABLE_EXPLORING` | `True` | Auto explore |
| `ENABLE_AUTO_CATCHBOT` | `True` | Auto catchbot |
| `ENABLE_AUTO_HUNT` | `True` | Auto hunt mode |
| `ENABLE_AUTO_SWAP` | `True` | Auto hunt and swap |
| `ENABLE_AUTO_BUY_BALLS` | `True` | Auto buy Poké Balls when low |
| `ENABLE_AUTO_RELEASE_DUPLICATES` | `True` | Auto release duplicate Pokémon |
| `ENABLE_AUTO_EGG_HATCH` | `True` | Auto hatch eggs |
| `ENABLE_AUTO_LOOTBOX_OPEN` | `True` | Auto open loot boxes |
| `ENABLE_AUTO_QUEST_REROLL` | `True` | Auto check, reroll & send help quest |
| `ENABLE_AUTO_GRAZZ` | `True` | Auto grazz |
| `ENABLE_AUTO_REPEL` | `True` | Auto repel |
| `ENABLE_AUTO_DAILY` | `True` | Auto claim daily reward |
| `ENABLE_WEBHOOK` | `True` | Send webhook notifications on catches |

### Example `example.bat`

```bat
@echo off
set SESSION_NAME=MySession
set DISCORD_TOKEN=YOUR_TOKEN_HERE
set CHANNEL_ID=YOUR_CHANNEL_ID
set HUMAN_PLAY=False

set ENABLE_AUTO_BUY_BALLS=True
set ENABLE_AUTO_RELEASE_DUPLICATES=True
set ENABLE_AUTO_EGG_HATCH=True
set ENABLE_AUTO_LOOTBOX_OPEN=True
set ENABLE_AUTO_QUEST_REROLL=True
set ENABLE_FISHING=True
set ENABLE_BATTLE_NPC=True
set ENABLE_HUNTING=True
set ENABLE_EXPLORING=True
set ENABLE_WEBHOOK=True
set ENABLE_AUTO_GRAZZ=True
set ENABLE_AUTO_REPEL=True
set ENABLE_AUTO_DAILY=True
set ENABLE_AUTO_CATCHBOT=True
set ENABLE_AUTO_SWAP=True
set ENABLE_AUTO_HUNT=True

"Pokemeow Autoplay.exe"
pause
```

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

> To purchase a key or ask questions, join the **[Discord Server](https://discord.gg/K4vfTbgh2U)**.

---

## 📋 Changelog

### v1.06
- Removed proxy support
- Removed `predict_captcha_url` config option
- Switched config format from `config.ini` → `config.yml`
- General stability improvements

### v1.05 and earlier
- Multi-account support
- Auto captcha solving integration
- Webhook notify support
- Human-behavior action simulation
- Proxy support

---

## ⚠️ Warning

- This tool is a **self-bot** and violates Discord's Terms of Service
- Usage may also violate PokéMeow bot rules
- The developer is **not responsible** for any account bans or losses
- Always use on an **alt account**

---

<div align="center">

**v1.06** &mdash; Pokemeow Autoplay

[![Discord](https://img.shields.io/badge/Join_the_Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/K4vfTbgh2U)

</div>
