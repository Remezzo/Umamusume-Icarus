<div align="center">

# Icarus

### The complete automation platform for **Umamusume: Pretty Derby**

*Icarus plays your entire careers — start to finish, across every scenario — by speaking the game's own API. No screen-scraping, no clicking, no babysitting. Set your strategy, press **Run**, and wake up to a bench full of trained umas.*

[![Version](https://img.shields.io/badge/release-5.3.0-e8e8e8?style=for-the-badge)](../../releases/latest)
[![Platform](https://img.shields.io/badge/Windows-10%20%7C%2011-2b2b2b?style=for-the-badge&logo=windows&logoColor=white)](../../releases/latest)
[![Discord](https://img.shields.io/badge/Discord-join%20the%20Icarus%20hub-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/wpbd3hTBDc)

![Native API](https://img.shields.io/badge/native%20API-zero%20OCR-e8e8e8)
![Updates](https://img.shields.io/badge/updates-Ed25519%20signed-1f7a4d)
![Runs headless](https://img.shields.io/badge/runs-headless%20%C2%B7%20unattended-2b2b2b)
![Local only](https://img.shields.io/badge/data-100%25%20local-e8e8e8)

**[⬇ Download](../../releases/latest) · [💬 Discord](https://discord.gg/wpbd3hTBDc) · [📖 Why it's different](#-why-icarus-is-different) · [✨ What it does](#-what-it-does) · [🛡 Is it safe?](#-honest-notes)**

</div>

---

Icarus plays your careers. Not by watching pixels and clicking at them — **by speaking the game's own protocol.** It logs in, starts a career, scores every training against your model, races the schedule you set, answers events with the right choice, buys skills at the end, banks the trained uma into your inheritance pool, and starts the next one. Then it does that **four hundred times while you sleep.**

Everything runs behind a local dashboard in your browser. Nothing touches the network, and no credentials ever leave your machine.

> [!IMPORTANT]
> ### ⚡ Quick start
>
> 1. **[Download `Icarus.zip`](../../releases/latest)** and extract it — keep the whole folder together.
> 2. **Double-click `Icarus.exe`.** That's the entire setup: Python, Node.js and every dependency are already inside — nothing to install, nothing downloaded.
> 3. The dashboard opens at **<http://127.0.0.1:1717>**. Sign in, pick your trainee and deck, press **Run Career**.
>
> First launch shows a splash while the single exe unpacks itself (once); after that it's instant and signs you back in on its own. Windows may warn you the first time — the build is signed with our own certificate, so **More info → Run anyway**.

> **✨ New in 5.3.0** — a completely rebuilt interface, a **humanlike pacing engine** calibrated against 58 real careers, a single signed `.exe` that keeps you signed in, and a new suite of race-planning, scheduling and deck tools. → [Full release notes](../../releases/latest)

---

## 📖 Why Icarus is different

Most automation for this game **drives the UI**: screenshots, template matching, OCR, simulated taps. That approach breaks on a resolution change, a UI patch, a localisation, a slow animation, or a window that lost focus. It's slow, fragile, and obvious.

**Icarus does none of that.** There is no OCR, no image recognition and no synthetic input anywhere in the codebase. It talks to the exact same msgpack API the game client talks to, and reads card, skill, race and event data straight out of your own local `master.mdb`.

<div align="center">

|  | Screen-scraping bots | **Icarus** |
|---|:---:|:---:|
| How it plays | 📷 screenshots + OCR + taps | ⚡ **the game's own API** |
| Resolution / DPI | must match templates | ✅ **irrelevant** |
| Game language | needs per-language assets | ✅ **irrelevant** |
| Window focus | must stay foreground | ✅ **runs headless** |
| Reading a stat | *"probably 1,240 speed"* | ✅ **exactly 1,240** |
| A new support card | broken until re-templated | ✅ **read from `master.mdb`** |
| Career pace | bounded by animation speed | ✅ **calibrated to look human** |
| A whole career | one at a time, watched | ✅ **hundreds, unattended** |

</div>

The result: **complete, hands-off careers at protocol speed** — every scenario, every mechanic, paced to look exactly like a person tapping through the client, browsable in a dashboard you leave running while you do anything else.

---

## ✨ What it does

### 🏆 Full career automation — every scenario, done properly
Complete, unattended careers across **URA Finals**, **Unity Cup**, **Make a New Track** and **Grand Live (Grand Concert)** — each with its own real strategy, not a shared approximation.

- **Training decisions** from a scoring model *you* control: stat caps and weights, mood and energy thresholds, rest and summer policy, support-card and bond scoring, hint value, double-circle handling.
- **Race planning** — your schedule plus aptitude filtering, with **fan-goal protection** that spots a goal about to be missed and enters an eligible race in the closing turns to save the career.
- **Event handling** from a full event-outcome database, with per-preset preferred outcomes and learning from what it sees.
- **Skill purchasing** with a priority list, a never-buy blacklist, and buy-as-you-go or bank-it-for-the-end.
- **Scenario mechanics in full** — MANT's item shop with per-item priorities and budget floors; Unity Cup's roster, divisions and team races; Grand Live's token economy, board and song queue aimed at Great Success lives.
- **Inheritance** — succession-affinity scoring, borrowed-parent handling with a daily counter, and automatic fallback to your own backup parent when a borrow is refused.

### 🕐 Humanlike pacing *(new in 5.3.0)*
Icarus no longer paces every call at one flat tempo. It draws each pause from a **per-action profile calibrated against 58 real careers** — a quick "is there an event here?" check takes a fraction of a second, a training decision takes the few seconds a person would, with the occasional longer pause the way a real player gets distracted. The pacing floor is **fixed and can't be lowered** by any setting.

### ⚡ Hyper Skip
Careers advance at protocol speed — no cutscenes, no results screens, no animations to wait out. Only the pacing you deliberately configure.

### 🔁 Character Rotation
Queue trainees with a run count each — Oguri Cap ×5, Vodka ×4, Tokai Teio ×3 — and Icarus switches between them as careers complete. Loop forever or stop at the end. Restart mid-queue and it resumes on the same trainee with the same progress.

### 🧠 Live Advisor
A running commentary on the bot's own reasoning: which facility it chose and by how much, what the runner-up was, why it rested, what it expects from a race. For tuning a preset — and for trusting one.

### 👪 Parent Suggestions
Scores every valid pair of your veterans against the trainee and preset you've picked: white/pink/blue sparks weighted toward the skills you actually want, aptitude fixes that clear a real letter grade, and true succession affinity. Always two different characters.

### 🎴 Deck & inheritance tools *(new in 5.3.0)*
A card-data recommender that reaches the Deck panel, lender discovery, and the ability to borrow a **max limit-break** support card — not just whichever listed first.

### 📅 Scheduler
Start on a chosen day and time, run your dailies, run a set number of careers, then idle or shut down — reusing your last setup, or resuming a career already in progress.

### 🎯 Independent Training
Runs the game's own idle career mode on a loop — the preset you pick governs the whole run (its races become the agenda, its skill list drives what's bought), banking a fresh parent into your pool career after career.

### ⏸ Pause & Resume
Hold a career at the next safe point without ending it — do your dailies, clear veterans, take a manual action — then resume exactly where it left off. No restart, no lost progress.

### ☀ Dailies
Team Trials until RP runs out (with an optional parfait for team mood), Daily Races to the cap, Legend Races against a boss you pick, and a Daily Shop sweep within a gold budget.

### 👥 Veteran Management
Browse, filter and bulk-delete trained characters — by grade, by sparks with star minimums, by favourites, or by *trained this session* — then select everything the filter matched in one click. Locked veterans are protected.

### 🔔 Discord Webhooks
Rich embeds when a career finishes and when the bot stops: grade, rank points, final stats, fans, skills bought, races run, inheritance sparks, session runtime, and where the run placed in the current session's ranking.

### 🔑 Steam & session automation
Handles the Steam side end to end — active-user switching, ticket generation with 2FA, refresh-token reuse, and exponential backoff when Steam rate-limits. An expired session is refreshed and the career carries on **without human input**, and a relaunch signs you back in from the saved capture on its own.

### 📊 Statistics
Every completed career recorded — grade, rank score, stats, fans, wins, races, skills, sparks, deck, and true wall-clock duration measured start to finish. Feeds the run-history dashboard, leaderboards, a Hall of Fame, deck forecasting and a weekly digest.

### 🎨 A rebuilt interface *(new in 5.3.0)*
A matte-black dashboard built for information density: a **"Why this move"** rail that shows the real reason for the current turn, live stat bars measured against each trainee's own ceilings, a per-turn decision log, a filterable console with one-click export, colour-vision-deficiency palettes, high-contrast mode and adjustable text size.

---

## 💻 Requirements

- **Windows**, with the Umamusume (Steam) client installed and running at first sign-in — Linux works too via Wine, see [Running on Linux (Wine)](#-running-on-linux-wine).
- **Nothing else.** Python, Node.js and every dependency ship inside the folder.
- Internet for first-time setup and updates.

## ▶ Using it

1. Double-click **`Icarus.exe`** — the dashboard opens at <http://127.0.0.1:1717>.
2. **Sign in**, then pick your trainee, support deck and inheritance on **Setup**.
3. Tune your preset across **Training**, **Racing**, **Scenario** and **Skills**.
4. Press **Run Career** — or configure **Auto Restart**, **Character Rotation** or the **Scheduler** and walk away.

> The control panel binds to **localhost only**. It is never exposed to your network.

## 🔄 Updating

Icarus checks for new releases and updates itself from the dashboard (**Update available → Update Now**). It downloads the new signed exe, **verifies the signature before touching your install**, and keeps your presets, settings and history. Restart when it finishes.

## 🐧 Running on Linux (Wine)

Icarus targets Windows but runs well under [Wine](https://www.winehq.org/). Steps are written for Arch-based distros; on Debian/Ubuntu substitute `sudo apt install` for `sudo pacman -S`.

1. **Get the files.** Download the release zip and extract it into a dedicated folder.
2. **Install Wine and Winetricks.**
   ```bash
   sudo pacman -S wine winetricks        # Arch
   # sudo apt install wine winetricks    # Debian/Ubuntu
   ```
3. **Install the common Windows dependencies:**
   ```bash
   winetricks vcrun2019 dotnet48 corefonts
   ```
4. **Configure Wine.** Run `winecfg` and set the Windows version to **Windows 10**.
5. **Run Icarus.** Open a terminal *in the folder containing the executable*, then:
   ```bash
   wine Icarus.exe
   ```
   Complete the normal first-run setup and the dashboard opens at the address Icarus prints in its console.

> [!TIP]
> **"Node.js is only supported on Windows 8.1 … or higher"** — open `wine regedit`, go to `HKEY_CURRENT_USER\Environment`, add a **String Value** named `NODE_SKIP_PLATFORM_CHECK` set to `1`, then restart everything under Wine.

## 🛠 Running from source (developers)

The packaged `Icarus.exe` needs none of this — it is only for building from the source tree.

```bash
# Python 3.10–3.13 and Node.js already installed
pip install --prefer-binary -r requirements.txt
npm install
python main.py
```

---

## 🛡 Honest notes

- **Automating the game is against Cygames' Terms of Service and carries real account risk.** Humanlike pacing, randomised delays and step-away breaks make the traffic look less mechanical — but nothing makes automation undetectable, and no one should tell you otherwise. Use in moderation, at your own risk.
- **Don't expose the control panel.** The local API has no authentication because it's designed to be local-only. Don't change the bind host and don't port-forward it.
- **Card and race data comes from your own game files.** After a game update, launch the game once so it patches `master.mdb`, then reload master data in Icarus — new support cards and races appear automatically.

---

## 🧭 The Icarus Suite

Icarus is one tool in a family. Every one speaks the game's own API — the same protocol work underneath, a different job on top.

|  |  |
|:--:|:--:|
| [![Fortuna — headless Global account reroller](docs/promo/fortuna.png)](https://github.com/Remezzo/Umamusume-Fortuna) | [![Overseer — companion overlay with live translation and Hyper Skip](docs/promo/overseer.png)](https://github.com/Remezzo/Umamusume-Overseer) |
| [![Un-Follower — prunes inactive followers through the game's own API](docs/promo/unfollower.png)](https://github.com/Remezzo/Umamusume-Un-Follower) | ![Navigator — captures and decodes the game's native API traffic](docs/promo/navigator.png) |

- **[Fortuna](https://github.com/Remezzo/Umamusume-Fortuna)** — a fully headless Global account reroller: pure API mint, no game client, no plugin. ~1 account a minute, each with its full pull history and recovery password.
- **[Sundial](https://github.com/Remezzo/Umamusume-Sundial)** — perpetual **Independent Training** across up to twelve accounts in parallel: start a career, bank the parent, buy the skills, run the races, repeat — a parent factory that never clocks out.
- **[Overseer](https://github.com/Remezzo/Umamusume-Overseer)** — a companion overlay with **live translation** in 25+ languages, Hyper Skip, performance enhancements, Team Trials tools, career tracking and event/training/race prediction. For both Global and Japanese Steam clients.
- **[Un-Follower](https://github.com/Remezzo/Umamusume-Un-Follower)** — reads your follower list from the Cygames server, works out who's inactive, and removes them through the game's own `friend/un_follower` API.
- **[Club Manager](https://github.com/Remezzo/Umamusume-Club-Manager)** — circle management over the game's own API. *(Confirm URL & blurb — placeholder.)*
- **[Navigator](https://github.com/Remezzo/Umamusume-Navigator)** — the developer tool that captures and decodes the game's native API traffic. It's what the rest of the suite is built on.

---

<div align="center">

**Made by the Icarus team · [Join us on Discord](https://discord.gg/wpbd3hTBDc)**

</div>

