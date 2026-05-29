# Change Log

All notable public app updates are listed from newest to oldest.

---

## v2.0.0

Customer-facing changes when upgrading from v1.9.2.

### Improved

- Updated the public client version to `2.0.0`.
- Updated license version validation for the 2.0.0 client release.
- Improved 24/7 runtime stability for continuous long-session autoplay.
- Upgraded Anti-Ban pacing for smoother extended sessions with less repetitive runtime behavior.
- Improved challenge-resilience handling for captcha prompts, wait states, cooldown responses, refresh states, and temporary anti-abuse checks.
- Improved captcha solve flow for faster response handling and cleaner recovery during active gameplay.
- Improved scheduler reliability across hunting, fishing, battle, checklist, inventory, release, and shop automation.
- Improved runtime state handling so temporarily unavailable features are skipped cleanly during the same session.
- Improved console/runtime wording for recovery actions, disabled features, and long-session monitoring.

### Fixed

- Fixed client/server version mismatch handling for the 2.0.0 release line.
- Fixed long-session edge cases that could interrupt 24/7 autoplay.
- Fixed cases where captcha or challenge recovery could delay the current command chain.
- Fixed retry behavior after wait, cooldown, refresh, and temporary anti-abuse responses.
- Fixed repeated failed-action loops when a feature becomes unavailable during the current runtime session.
- Fixed scheduler edge cases that could delay or skip task execution during extended operation.

### Upgrade Notes

- The 2.0.0 client requires the matching server version response for license validation.
- No required `settings.yml` migration is expected from v1.9.2 if existing values are valid.
- Existing launcher `.bat` feature toggles remain the same, but launchers should call `Pokemeow Autoplay v2.0.0.exe`.
- This release focuses on the 2.0.0 client version line, license compatibility, 24/7 stability, Anti-Ban pacing, captcha recovery, challenge handling, and cleaner runtime behavior.

---

## v1.9.1

Customer-facing changes when upgrading from v1.9.0.

### Added

- Added Anti-Ban 24/7 Mode improvements for long-running sessions.
  - Human-Mode now uses more advanced pacing and behavior variation for extended runtime.
  - The client is better at reducing repeated automation patterns, bot-check triggers, and account flagging risk.
  - Long sessions now feel less repetitive while keeping the same simple user controls.
- Added total catch tracking across hunting, fishing, and CatchBot returns.
- Added clearer quest summary output after checking quests.
  - Quest logs now show compact readable labels such as `#1: oldrod | #2: Receive | #3: dexcaught`.
- Added `min_budget` support for shop automation.
  - Default `min_budget` is `2000`.
  - Shop automation skips buying when the usable budget is below the minimum.
- Added clearer rarity coloring for hunt and fishing logs.
  - Super Rare results now use a brighter yellow color.
  - Daily hunt logs now show rarity-aware coloring.
- Added clearer battle result logs for win, lose, and forfeit outcomes.

### Improved

- Improved `Please wait` handling.
  - When the bot asks the user to wait, the client now waits 3 seconds and retries the same current action.
  - Retry no longer skips to the next scheduled action first.
  - This applies to normal `please wait`, pending spawned Pokemon, and catch/fish cooldown-ready messages.
- Improved Anti-Ban runtime scheduling.
  - Human-Mode now runs in longer natural sessions before taking longer breaks.
  - Bot-Mode keeps direct schedule-based operation for users who prefer predictable continuous automation.
  - Human-Mode and Bot-Mode now share the same base command timing ranges.
- Improved runtime disable behavior.
  - When a feature is disabled during a session because of vote requirements, missing resources, daily limits, out-of-ball states, battle requirements, or similar conditions, the client logs the reason once.
  - After that, the disabled feature is skipped automatically during the same session instead of repeatedly checking and logging the same problem.
- Improved checklist automation stability.
  - Daily, CatchBot, swap, and daily hunt follow-up actions now respect retry/disable/stop decisions more predictably.
  - A retry inside one checklist action keeps focus on the current action instead of moving to unrelated actions.
- Improved inventory automation stability.
  - Egg, lootbox, Grazz, Repel, and quest follow-up actions now stop or continue more cleanly when a child action returns retry/disable/stop.
- Improved battle automation.
  - Battle now waits for new battle state messages instead of relying on edited messages.
  - If a configured skill is not found, the client refreshes the latest battle message once before deciding to forfeit.
  - Battle win rewards now highlight the received Pokecoins more clearly.
- Improved shop automation.
  - Ball buying now respects both `max_budget` and `min_budget`.
  - Ball purchase order is clearer and follows the configured budget ratio.
- Improved scheduler logs.
  - Human-Mode and Bot-Mode startup logs are easier to distinguish.
  - Human-Mode session and break logs are shorter and avoid exposing unnecessary runtime details.
- Improved response handling logs.
  - Retry, disable, skip, refresh, captcha, and stop actions now use more consistent wording.

### Fixed

- Fixed retry behavior for `Please wait` responses so the current action is retried after 3 seconds instead of being skipped until the next loop.
- Fixed hunting and fishing schedule timing so the next run is based on the completed action, not the moment the action started.
- Fixed battle timeout behavior after clicking a skill.
- Fixed battle result detection so wins, losses, and forfeits are logged more accurately.
- Fixed missing-skill battle behavior by refreshing the latest battle state before forfeiting.
- Fixed shop budget logs so low-budget skips are shorter and cleaner.
- Fixed noisy response logs caused by long raw Discord messages.
- Fixed repeated disable warnings during the same runtime session.
- Fixed confusing quest log output by showing only readable quest labels.
- Fixed several edge cases where disabled child actions from checklist or inventory could continue the wrong action chain.

### Upgrade Notes

- No required `settings.yml` migration is expected from v1.9.0 if the existing values are valid.
- Existing launcher `.bat` feature toggles remain the same.
- Users should review `settings.example.yml` if they want the updated `min_budget` and battle skill examples.
- For battle automation, configure only skill buttons that are available for the selected Pokemon. If a configured skill does not exist, the client refreshes once and then forfeits the battle.
- This release focuses on Anti-Ban 24/7 behavior, battle reliability, shop safety, clearer rarity logs, retry correctness, scheduler stability, and runtime statistics.

---

## v1.9.0

- Improved startup flow so the app checks license status before connecting to Discord.
- Updated the startup display order:
  - The console clears first.
  - Version, license status, and verification checks run immediately.
  - The license status panel is shown before the app banner.
  - The app banner and safety notices are shown after a successful license check.
- Reduced unnecessary Discord connection attempts when the license is invalid, expired, or waiting for redeem.
- Improved Discord ready behavior with cleaner channel connection logging.
- Improved webhook behavior for important encounters:
  - Legendary, Shiny, and Golden encounters still notify the user webhook on both success and failure.
  - Only successful Legendary, Shiny, and Golden encounters are reported to the service.
  - Pokémon listed in `pokemon_pokeball_mapping` now notify only the user's webhook on both success and failure.
- Added special webhook handling for Pokémon-specific ball override encounters in both hunting and fishing.
- Improved hunting and fishing logs when a Pokémon-specific ball override is used.
- Reworked fishing message handling for faster and cleaner fishing turns.
- Improved fishing stage detection for bite, no-nibble, got-away, encounter, and result states.
- Improved fishing button timing by clicking the current updated message directly instead of performing an extra message refresh before each click.
- Reduced invalid or expired fishing button clicks caused by delayed message refreshes.
- Improved fishing result reliability for both successful catches and failed catches.
- Removed temporary verbose fishing and button debug logs from normal app output.
- Cleaned up fishing flow behavior so failed or unavailable actions stop cleanly without noisy recovery logs.
- Updated the Windows app icon for the packaged executable.
- Improved overall startup clarity, webhook privacy, fishing stability, and button-click stability.

---

## v1.8.1

- Added per-Pokémon ball override support through `pokemon_pokeball_mapping` in `settings.yml`.
- Added default Pokémon-specific ball rules for `Shieldon`, `Machoke`, and `Magikarp` to use `greatball`.
- Updated hunting ball selection priority:
  - Legendary, Shiny, and Golden encounters keep their rarity-based ball preference first.
  - Normal Pokémon can now use a Pokémon-specific ball override.
  - Held-item encounters use `hunt_item_ball` after Pokémon-specific overrides.
  - Other encounters fall back to rarity-based ball selection.
- Updated fishing ball selection to support Pokémon-specific ball overrides while keeping Legendary/Shiny/Golden protection.
- Reworked auto-buy ball budgeting from remaining-budget percentages to scaled budget ratios.
- Replaced `ball_percentage` with `ball_budget_ratio` in `settings.yml`.
- Auto-buy ball ratios no longer need to add up to `100`; the client now scales ratios automatically.
- Changed skipped ball behavior from `-1` to `0` for clearer configuration.
- Auto-buy now calculates each ball purchase from the same total shop budget instead of reducing the budget after each ball type.
- Auto-buy continues to respect `max_budget` and skips any ball type whose scaled budget cannot buy at least one ball.
- Updated README configuration notes to describe the new scaled ball purchase ratio system.

---

## v1.8.0

- Updated the client tool version to `1.8.0`.
- Improved the startup status panel with session name, license state, expiry time, remaining time, total solved captcha count, client version, service version, and update notice handling.
- Kept the existing Discord-token based activation and redeem flow used by the old client.
- Reworked captcha solving inside the client: the tool now downloads the captcha image from the PokéMeow embed, stores it in the local `captchas/` folder, converts it to base64, submits it for solving, and sends the returned answer back to Discord.
- Added multi-attempt captcha retry support when PokéMeow replaces the captcha image after a wrong answer.
- Added temporary-ban detection before solving a captcha and after submitting a captcha answer, so the client stops safely when PokéMeow blocks further attempts.
- Added a startup captcha guard that checks for an existing PokéMeow captcha before the scheduler starts running tasks.
- Added active gameplay captcha guards after hunting and fishing button clicks, reducing cases where the tool misses a captcha prompt during an encounter.
- Added a refresh fallback action that checks the latest PokéMeow message and solves a captcha if the previous command timed out.
- Added captcha encounter counting to the in-session statistics.
- Improved human-like scheduler behavior with randomized task order, fatigue-based delays, distraction pauses, work sessions, and long breaks.
- Added periodic license verification while the scheduler is running.
- Added runtime hotkeys for pausing, showing statistics, and toggling hunting, fishing, or battle tasks while the client is running.
- Improved sleep/hotkey handling so Windows keyboard hotkeys use `msvcrt` only when available, avoiding crashes on non-Windows environments.
- Improved hunting automation by waiting for message/button updates, parsing encounter name, rarity, held-item status, and available balls, then choosing the best usable ball automatically.
- Improved hunting ball fallback: if the configured ball is unavailable, the client downgrades to the best available lower-tier ball instead of failing the encounter immediately.
- Improved hunting result handling with catch/fail parsing, encounter indexing, coin/item tracking, rarity statistics, and Legendary/Shiny/Golden webhook notifications.
- Improved fishing automation with pull handling, no-nibble detection, encounter parsing, local rarity lookup from `data/pokemon_info.json`, ball fallback, and result waiting.
- Improved fishing result handling with caught/failed parsing, fishing token tracking, rarity statistics, and Legendary/Shiny/Golden webhook notifications.
- Improved CatchBot automation with clearer returned/started/no-money/already-running state parsing and catchbot Pokémon statistics.
- Improved lootbox parsing and statistics for opened lootboxes, PokéCoins, and received items.
- Expanded in-session statistics for coins, fish tokens, hunt encounters, fish encounters, battle wins, captcha encounters, catchbot returns, lootboxes, item drops, rarity counts, egg hatches, released Pokémon, Grazz usage, and Repel usage.
- Improved response validation for cooldowns, daily limits, missing fishing rod, out-of-ball states, battle requirements, vote requirements, new-account warnings, permanent bans, temporary bans, and captcha prompts.
- Fixed the scheduler indentation bug that caused `helpers/scheduler.py` to fail parsing.
- Reduced duplicate daily-limit warning logs in response validation.

---

## v1.7.2

- Updated the public app version to `1.7.2`.
- Improved the paid public app startup experience.
- Added a cleaner app status panel showing session name, captcha solve count, client version, and service version.
- Added update notice support for newer public builds.
- Improved captcha handling with automatic detection, download, solve submission, and retry behavior.
- Added temporary-ban checks before captcha solving and after captcha submission.
- Added remote webhook queue support in addition to optional direct Discord webhook notifications.
- Improved Legendary, Shiny, and Golden catch/fail webhook notifications.
- Added human-behavior mode with randomized task delays, warm-up delays, distraction breaks, fatigue-based sessions, and long breaks.
- Added runtime hotkeys to pause, show statistics, and toggle hunting, fishing, or battle tasks.
- Added expanded session statistics for catches, rarity counts, coins, items, lootbox rewards, eggs, fish tokens, battles, captcha count, Grazz usage, Repel usage, released Pokémon, and catchbot returns.
- Improved hunting automation with rarity-based ball selection, held-item ball preference, and automatic ball downgrade when the preferred ball is unavailable.
- Improved fishing automation with pull handling, encounter parsing, rarity lookup, ball selection, no-nibble handling, fishing token tracking, and result logging.
- Improved battle automation with configurable battle mode, random target selection, and configurable skill rotation.
- Improved checklist automation for daily rewards, catchbot, swap, and hunt actions.
- Improved inventory automation across multiple inventory pages.
- Improved egg automation for ready-to-hatch eggs and holding a new egg when available.
- Improved lootbox, Grazz, Repel, quest reroll, duplicate release, and ball shop automation.
- Improved external `settings.yml` configuration for shop budget, ball purchase percentages, item thresholds, quest filters, battle settings, webhook URLs, and rarity-to-ball mapping.
- Improved app stability and response handling for cooldowns, daily limits, missing requirements, bans, captcha prompts, and unavailable resources.

---

## v1.7.0 / v1.7.1

- Added app version display and update notice support.
- Improved webhook handling for important catch notifications.
- Improved captcha flow so the app stops when a temporary ban is detected instead of continuing to solve.
- Kept `settings.yml` as an external editable file beside the public app executable.
- Improved general stability and logging.

---

## v1.6.0

- Switched the public configuration format to `settings.yml`.
- Removed proxy configuration from the public app package.
- Removed the old custom captcha prediction URL option.
- Improved settings readability and app stability.

---

## v1.5.0 and earlier

- Added multi-session launcher support through separate `.bat` files.
- Added auto captcha solving integration.
- Added webhook notification support.
- Added human-behavior simulation support.
- Added early core PokéMeow automation features such as hunting, fishing, battling, checklist actions, inventory actions, and automatic utility commands.
