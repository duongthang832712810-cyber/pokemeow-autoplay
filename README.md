# Pokemeow Autoplay

A ready-to-run Windows tool.

## Banner (console branding)

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

---

## Files
Put these in the same folder:
- `Pokemeow Autoplay.exe`
- `RUN.bat`
- `config.ini`
- `proxies.json` (optional)

Auto-created at runtime:
- `logs/`
- `captchas/`
- `errors.log`

---

## Quick start
1) Open `RUN.bat` with Notepad.
2) Set:
   - `DISCORD_TOKEN`
   - `CHANNEL_ID`
   - `SESSION_NAME`
3) (Optional) Proxy:
   - set `PROXY_ID=proxy_1`
   - edit `proxies.json`
4) Double-click `RUN.bat`.

---

## RUN.bat (how it works)
`RUN.bat` sets environment variables (DISCORD_TOKEN, CHANNEL_ID, flags...) and then starts the EXE.

If you want to disable proxy: set `PROXY_ID=` (empty).

---

## config.ini
Controls:
- ball selection by rarity
- rarity colors in console
- quest keep list
- webhook URLs (optional)
- captcha solver URL (optional)

Keep the same formatting/indentation for the JSON blocks.

---

## proxies.json (optional)
Format:
- keys: `proxy_1`, `proxy_2`, ...
- value: `http://user:pass@host:port`

Example:
{
  "proxy_1": "http://user:pass@host:port",
  "proxy_2": "http://user:pass@host:port"
}

---

## Hotkeys (console)
While the bot is waiting/sleeping:
- `p` pause (Enter to resume)
- `s` show statistics (Enter to resume)
- `h` toggle hunting
- `f` toggle fishing
- `b` toggle battle

---

## Logs / troubleshooting
- Session log: `logs/<SESSION_NAME>.log`
- If something fails silently: check `errors.log`

Common issues:
- Token invalid → login fails.
- Channel ID wrong → cannot find channel.
- Proxy wrong → set `PROXY_ID=` to disable or fix `proxies.json`.
