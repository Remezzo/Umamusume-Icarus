<div align="center">

<img src="public/icarus.png" alt="Icarus" width="120" />

# Icarus

### Complete careers, run for you. Every scenario. All night. Forever.

**Icarus is a headless bot that plays Umamusume: Pretty Derby through the game's own API — it signs in, starts a career, scores every training against your model, races your schedule, answers events, spends the skill points, banks the parent, and starts the next one.** No screen-scraping, no OCR, no window to babysit: it speaks msgpack to the servers directly and reads your own `master.mdb` for card, skill, race and event data.

[![Download](https://img.shields.io/badge/Download-Icarus.exe-D4A017?style=for-the-badge)](https://github.com/Remezzo/Umamusume-Icarus/releases/latest)
&nbsp;
[![Discord](https://img.shields.io/badge/Discord-Join_the_Icarus_hub-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/wpbd3hTBDc)

![Platform](https://img.shields.io/badge/platform-Windows-0078D6)
![Version](https://img.shields.io/badge/release-5.3.2-D4A017)
![Signed updates](https://img.shields.io/badge/updates-Ed25519_signed-1f7a4d)
![Scenarios](https://img.shields.io/badge/scenarios-URA_%C2%B7_Unity_Cup_%C2%B7_MANT_%C2%B7_Grand_Live-2b2b2b)
![License](https://img.shields.io/badge/license-Proprietary-c02626)

<sub>Windows · Steam · Global client · part of the Icarus Suite</sub>

</div>

---

Icarus plays your careers. Not by watching pixels and clicking at them — by speaking the game's own protocol. It logs in, starts a career, evaluates every training against your scoring model, races the schedule you set, answers events with the right choice, buys skills at the end, and starts the next one. Then it does that four hundred times while you sleep.

Everything runs behind a local dashboard in your browser. Nothing is exposed to the network, and no account credentials leave your machine.

> [!IMPORTANT]
> ### Quick start — double-click `Icarus.exe`
>
> That is the whole setup. Python, Node.js and every dependency are already
> inside that one file — there is nothing to install and nothing to extract.
> The dashboard opens in your browser at <http://127.0.0.1:1717>.
>
> Windows will warn you the first time — the build is signed, but with our own
> certificate rather than one Microsoft trusts, so SmartScreen has no reputation
> to go on. **More info → Run anyway.** If your antivirus quarantines it, add
> the file to your exclusions and download it again.
>
> Give it a folder of its own before the first run. Icarus unpacks `data`,
> `public`, `node` and `node_modules` beside itself and keeps your presets,
> sign-in and run history there — so put it somewhere it can live, rather
> than your Downloads folder.

---

## Why native API automation matters

Most automation for this game drives the UI: screenshots, template matching, OCR, simulated taps. That approach breaks on a resolution change, a UI patch, a localisation, a slow animation, or a window that lost focus.

Icarus does none of that. **There is no OCR, no image recognition and no synthetic input anywhere in the codebase.** It talks to the same msgpack API the game client talks to, and reads card, skill, race and event data straight out of your own local `master.mdb`. The practical consequences:

| | Screen automation | Icarus |
|---|---|---|
| Resolution / DPI | Must match templates | Irrelevant |
| Game language | Needs per-language assets | Irrelevant |
| Window focus | Must stay foreground | Runs headless |
| Career pace | Bounded by animation speed | Bounded by pacing you choose |
| Reading a stat | "probably 1,240 speed" | Exactly 1,240 |
| A new support card | Broken until re-templated | Picked up from `master.mdb` |

---

## What it does

### Career Automation
Complete, unattended careers across every scenario — **URA Finals**, **Unity Cup**, **Make a New Track** and **Grand Live (Grand Concert)** — each with its own strategy, not a shared approximation.

- **Training decisions** from a scoring model you control: stat caps and weights, mood and energy thresholds, rest and summer policy, support-card and friendship-bond scoring, hint value, double-circle handling.
- **Race planning** — your own schedule plus aptitude filtering, with **fan-goal protection** that spots a goal about to be missed and enters an eligible race in the closing turns to save the career.
- **Event handling** driven by a full event-outcome database, with per-preset overrides and learning from what it sees.
- **Skill purchasing** with a priority list, a blacklist, and a choice of buying as you go or banking it for the end. Your list is honoured whether or not the game hinted a skill — a hint is a discount, not a permission — and a career never banks with points it could still have spent: the list is bought to exhaustion first, then the balance goes on skills that suit the trainee's own distance and style, until nothing on offer is affordable. A one-off game refusal never bans a skill for the whole session, bundled skills are retried one by one, and every listed skill that is not bought is named in the log with the reason.
- **Scenario mechanics done properly** — MANT's item shop with per-item priorities and budget floors; Unity Cup's team roster, divisions and team races; Grand Live's token economy, square board and song queue aimed at Great Success lives.
- **Inheritance** — succession affinity scoring, borrowed-parent handling with a daily-borrow counter, and an automatic fallback to your own backup parent when a borrow is refused.

### Auto Training
Keeps the game's **native Auto Training** running around the clock: detect completion, collect the rewards, return to the screen, start the next session, repeat until you stop it.

### Hyper Skip
Careers advance at protocol speed. No cutscenes to sit through, no results screens to dismiss, no animations to wait out — only the pacing you deliberately configure.

### Character Rotation
Queue trainees with a run count each — Oguri Cap ×5, Vodka ×4, Fine Motion ×6, Tokai Teio ×3 — and Icarus switches between them automatically as careers complete. Loop the list forever or stop after the last trainee. Restart Icarus mid-queue and it resumes on the same trainee with the same progress.

### Live Advisor
A running commentary on the bot's own reasoning: which facility it chose and by how much, what the runner-up was, why it rested, what it expects from a race. Useful for tuning a preset — and for trusting one.

### Parent Suggestions
Scores every valid pair of your veterans against the trainee and preset you've chosen: white/pink/blue sparks weighted toward the skills you actually want, aptitude fixes that clear a real letter grade, and true succession affinity. Always two different characters.

### Veteran Management
Browse, filter and bulk-delete trained characters. Filter by grade, by sparks with exact-name star minimums, by favourites, or by **trained during the current session** — then select everything the filter matched in one click and delete it in one pass (Icarus batches around the game's 50-per-request limit). Deletes are per item: one locked, favourited or stale veteran never cancels the rest, and the review names what was deleted, what was skipped and why. A padlock means locked in the game itself; a shield means one of Icarus's own keep rules — favourites, lineage parents, last-of-kind, unique 3-stars and your top quartile are never deleted by the optional **auto-cull**, at any threshold.

### Scheduler
Start on a chosen day and time, run your dailies, optionally auto-cull the veteran box below a score you choose, run a set number of careers, then idle or shut down — reusing your last setup, or resuming a career already in progress. The scheduler will not start a career loop over a live Auto Training session, and its internet check does not mistake a DNS-blocked network for "offline".

### Pause & Resume
Hold a career at the next safe point without ending it. Do your dailies, clear out veterans, delete a career, take a manual action — then resume exactly where the run left off. No restart, no lost progress.


### Discord Webhooks
Rich embeds when a career finishes and when the bot stops: grade, rank points, final stats, fans, skills bought, races run, inheritance sparks, session runtime, session start and end times, and where the run placed in the **current session's** ranking.

### Steam Automation
Handles the Steam side end to end — active-user switching, ticket generation with 2FA, refresh-token reuse, and automatic exponential backoff when Steam rate-limits logins. Session recovery is automatic: an expired token is refreshed and the career carries on without human input.

### Emulator & Game Automation
Launches the game against the right account, captures a fresh session when one is needed, and closes the client again when it's done — so an unattended overnight run survives an expired session, a game update, or an account switch.

### Dailies
Team Trials until RP runs out, Daily Races to the cap, Legend Races against a boss you pick, and a Daily Shop sweep within a gold budget.

Daily Races pick by **reward** — Moonlight Sho for gold, Jupiter Cup for Support Points — with difficulty set separately. Legend Races cover the permanent bosses and the limited event when one is running, each with its own per-day allowance. Every mode runs once per game day, measured against the game's own 11:00 ET reset rather than the wall clock, so an interrupted session resumes where it stopped instead of starting over.

### Statistics
Every completed career is recorded: grade, rank score, stats, fans, wins, races, skills, sparks, deck, and true wall-clock duration measured career start to career completion — pauses, breaks and recoveries included. Feeds the run-history dashboard, leaderboards, a Hall of Fame, deck forecasting and a weekly digest.

### Accessibility
Colour-vision-deficiency palettes, a high-contrast mode, adjustable text size and reduced motion — applied before first paint and remembered between sessions.

### Modern UI
A matte-black dashboard built for information density: live resource HUD (TP · RP · Carrots · Gold · Clocks), per-turn decision log with reasoning, run dashboard, bond levels, and a filterable console with one-click export.

### Reliability and verification
Every release ships with a regression suite of more than 7,600 checks, and the packaged build is not signed until it passes a verifier chain that boots the real executable: 198 build-parity checks, 140 non-negotiables run three times (sign-in failure modes, pacing lock, auth capture bundled and functional), and a 168-check sweep of every page and endpoint. Destructive actions have hard guards — a manual delete can never remove an in-game favourite, auto-cull skips any veteran whose rank did not load, a data regeneration can never blank the skill table, and a retried purchase can never spend twice.

---

## Requirements

- **Windows**, with the Umamusume (Steam) client installed and running at first login — Linux works too via Wine, see [Running on Linux (Wine)](#running-on-linux-wine)
- **Nothing else.** Python, Node.js and every dependency ship inside the exe.
- Internet for first-time setup and updates


## Using it

1. Double-click **`Icarus.exe`**. The dashboard opens at <http://127.0.0.1:1717>.
2. **Log in**, then pick your trainee, support deck and inheritance on **Setup**.
3. Tune your preset across **Training**, **Racing**, **Scenario** and **Skills**.
4. Press **Run Career** — or configure **Auto Restart**, **Character Rotation** or the **Scheduler** and walk away.

> The control panel binds to **localhost only**. It is never exposed to your network.

## Updating

Icarus checks this repository for releases and updates itself from the dashboard (**Update available → Update Now**). Presets, environment, `node_modules` and runtime data are preserved, and a backup is written first. Restart when it finishes.

## Manual setup

```bash
# Python 3.10–3.13 and Node.js already installed
pip install --prefer-binary -r requirements.txt   # --prefer-binary avoids needing a C++ compiler
npm install
python main.py
```


## Running on Linux (Wine)

Icarus targets Windows, but it runs well under [Wine](https://www.winehq.org/). The steps below are written for Arch-based distros; on Debian/Ubuntu substitute `sudo apt install` for `sudo pacman -S`.

1. **Get the file.** Download `Icarus.exe` from the Releases page and put it in a folder of its own — it unpacks what it needs beside itself on the first run.

2. **Install Wine and Winetricks.**

   ```bash
   sudo pacman -S wine winetricks        # Arch
   # sudo apt install wine winetricks    # Debian/Ubuntu
   ```

3. **Install the common Windows dependencies** through Winetricks:

   ```bash
   winetricks vcrun2019 dotnet48 corefonts
   ```

4. **Configure Wine.** Run `winecfg` and set the Windows version to **Windows 10** (recommended) or Windows 11.

5. **Run Icarus.** Open a terminal *in the folder containing the executable* (most file managers offer "Open Terminal Here", or `cd` into it), confirm with `ls` that you're in the right place, then:

   ```bash
   wine Icarus.exe
   ```

   Complete the normal first-run setup (Steam details, 2FA) and you're set — the dashboard opens at the address Icarus prints in its console.

> [!TIP]
> **"Node.js is only supported on Windows 8.1, Windows Server 2012 R2, or higher"** — if you hit this error, open the Wine registry editor with `wine regedit`, navigate to `HKEY_CURRENT_USER\Environment`, create a new **String Value** named `NODE_SKIP_PLATFORM_CHECK` with value data `1`, then restart everything running under Wine (Icarus included).

---

## Honest notes

- **Automating the game is against Cygames' Terms of Service and carries real account risk.** Human-like pacing, randomised delays and step-away breaks make the traffic look less mechanical, but nothing makes automation undetectable and no one should tell you otherwise. Use in moderation, at your own risk.
- **Don't expose the control panel.** The API has no authentication because it is designed to be local-only. Don't change the bind host and don't port-forward it.
- **Card and race data comes from your own game files.** After a game update, launch the game once so it patches `master.mdb`, then reload master data in Icarus — new support cards and races appear automatically.

---

## The Icarus Suite

Icarus is one tool in a family. Every one of them speaks the game's own API — the same protocol work underneath, a different job on top.

|  |  |
|:--:|:--:|
| [![Fortuna — headless Global account reroller](docs/promo/fortuna.png)](https://github.com/Remezzo/Umamusume-Fortuna) | [![Un-Follower — prunes inactive followers through the game's own API](docs/promo/unfollower.png)](https://github.com/Remezzo/Umamusume-Un-Follower) |
| ![Overseer — companion overlay with live translation and Hyper Skip](docs/promo/overseer.png) | ![Navigator — captures and decodes the game's native API traffic](docs/promo/navigator.png) |

- **[Fortuna](https://github.com/Remezzo/Umamusume-Fortuna)** — a fully headless Global account reroller: pure API mint, no game client, no plugin.
- **[Un-Follower](https://github.com/Remezzo/Umamusume-Un-Follower)** — reads your follower list straight from the Cygames server, works out who's inactive, and removes them through the game's own `friend/un_follower` API.
- **Overseer** *(coming soon)* — a companion overlay with live translation in 25+ languages, Hyper Skip, performance enhancements, Team Trials tools, career tracking, and event/training/race prediction. For both Global and Japanese Steam clients.
- **Navigator** — the developer tool that captures and decodes the game's native API traffic. It's what the rest of the suite is built on.

---

<div align="center">


**[Discord](https://discord.gg/wpbd3hTBDc)**

</div>
