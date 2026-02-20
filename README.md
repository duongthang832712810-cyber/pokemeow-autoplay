# Pokemeow Autoplay (Windows)

This `upload/` folder is **ready to run** on Windows: put the files together, edit `RUN.bat` + `config.ini`, then start.

---

## 1) Folder structure / required files

Keep these files in the **same folder** (as provided in `upload/`):

- `Pokemeow Autoplay.exe`
- `RUN.bat`
- `config.ini`
- `proxies.json` *(optional — only if you use a proxy)*

Created automatically at runtime:
- `logs/` (per-session logs)
- `captchas/` (captcha images, if any)
- `errors.log` (global error log)

---

## 2) Quick start

1) Right-click `RUN.bat` → **Edit** (or open with Notepad).
2) Set the required values:
   - `DISCORD_TOKEN`
   - `CHANNEL_ID`
   - `SESSION_NAME`
3) (Optional) Proxy:
   - enable: `set PROXY_ID=proxy_1` then edit `proxies.json`
   - disable: `set PROXY_ID=` *(empty)*
4) Double-click `RUN.bat` to run.

---

## 3) `RUN.bat` — flags (enable/disable features)

`RUN.bat` does two things:
- sets environment variables (token/channel/flags…)
- starts `Pokemeow Autoplay.exe`

### Required
```bat
set SESSION_NAME=MySession
set CHANNEL_ID=123456789012345678
set DISCORD_TOKEN=YOUR_TOKEN
```

### Proxy
- Use proxy:
```bat
set PROXY_ID=proxy_1
```
- No proxy:
```bat
set PROXY_ID=
```

### Flags (how to edit)
- Format: `set FLAG_NAME=True` or `set FLAG_NAME=False`
- Examples:
  - Disable exploring:
    `set ENABLE_EXPLORING=False`
  - Disable webhook mirroring:
    `set ENABLE_WEBHOOK=False`

Available flags (see `RUN.bat`):
- `ENABLE_SHOW_ID`
- `ENABLE_AUTO_BUY_BALLS`
- `ENABLE_AUTO_RELEASE_DUPLICATES`
- `ENABLE_AUTO_EGG_HATCH`
- `ENABLE_AUTO_LOOTBOX_OPEN`
- `ENABLE_AUTO_QUEST_REROLL`
- `ENABLE_FISHING`
- `ENABLE_BATTLE_NPC`
- `ENABLE_HUNTING`
- `ENABLE_EXPLORING`
- `ENABLE_WEBHOOK`
- `ENABLE_AUTO_GRAZZ`
- `ENABLE_AUTO_REPEL`
- `ENABLE_AUTO_DAILY`
- `ENABLE_AUTO_CATCHBOT`
- `ENABLE_AUTO_SWAP`
- `ENABLE_AUTO_HUNT`

Notes:
- Keep the `True/False` spelling exactly like the template.
- If you mistype a flag name, the program may ignore it.

---

## 4) `config.ini` — ball logic / quests / webhook / captcha

Open `config.ini` with Notepad.

### 4.1 Pokéball mapping by rarity
- `rarity_pokeball_mapping`: chooses which ball to throw per rarity.
- Example: make `Rare` use `ultraball`:
  ```ini
  "Rare": "ultraball",
  ```

### 4.2 Rarity colors
- `rarity_color_mapping`: console colors only.

### 4.3 Quest keep list
- `keep_quest_type`: quest types to **keep** (do not reroll).

### 4.4 Default balls
- `fishing_ball`, `hunt_item_ball`, `fishing_shiny_golden_ball`

### 4.5 Webhook (optional)
- To mirror rare catches to a webhook:
  - set `webhook_url_success=...`
  - set `webhook_url_failed=...`
- Leave blank to disable.

### 4.6 Captcha solver (optional)
- `predict_captcha_url=`: solver base URL
- Leave blank to use the fallback (if implemented by the tool).

**Important:** JSON blocks inside `config.ini` must keep their indentation/formatting. Don’t break commas/braces.

---

## 5) `proxies.json` (optional)

Format:
- keys: `proxy_1`, `proxy_2`, ...
- values: proxy URL `http://user:pass@host:port`

Example:
```json
{
  "proxy_1": "http://user:pass@host:port",
  "proxy_2": "http://user:pass@host:port"
}
```

Then set in `RUN.bat`:
```bat
set PROXY_ID=proxy_1
```

---

## 6) Hotkeys (console)

While the bot is waiting/sleeping:
- `p` pause (press Enter to resume)
- `s` show statistics (press Enter to resume)
- `h` toggle hunting
- `f` toggle fishing
- `b` toggle battle

---

## 7) Logs / troubleshooting

- Session log: `logs/<SESSION_NAME>.log`
- Global error log: `errors.log`

Common issues:
- Invalid token → login fails.
- Wrong channel ID / cannot find channel → re-check `CHANNEL_ID` and permissions.
- Bad proxy → disable proxy (`PROXY_ID=`) or fix `proxies.json`.
