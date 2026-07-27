<div align="center">

# Icarus

### The complete automation platform for Umamusume: Pretty Derby

**Full career automation · Native game API · Multi-account · Multi-instance · Zero screen-scraping**


</div>

---

Icarus plays your careers. Not by watching pixels and clicking at them — by speaking the game's own protocol. It logs in, starts a career, evaluates every training against your scoring model, races the schedule you set, answers events with the right choice, buys skills at the end, and starts the next one. Then it does that four hundred times while you sleep.

Everything runs behind a local dashboard in your browser. Nothing is exposed to the network, and no account credentials leave your machine.

> [!IMPORTANT]
> ### Quick start — double-click `Start Icarus.bat`
>
> First launch builds an isolated Python environment, installs every dependency from **prebuilt wheels** (no Visual C++ Build Tools required), fetches **Node.js** if it's missing, then starts the bot and opens the dashboard. Every launch after that is instant.
>
> Needs internet on the first run. If Python isn't installed and `winget` is available, the launcher handles it; otherwise grab Python 3.10–3.13 from [python.org](https://www.python.org/downloads/) and tick **"Add python.exe to PATH"**.

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
- **Skill purchasing** with a priority list, a blacklist, and a choice of buying as you go or banking it for the end.
- **Scenario mechanics done properly** — MANT's item shop with per-item priorities and budget floors; Unity Cup's team roster, divisions and team races; Grand Live's token economy, square board and song queue aimed at Great Success lives.
- **Inheritance** — succession affinity scoring, borrowed-parent handling with a daily-borrow counter, and an automatic fallback to your own backup parent when a borrow is refused.

### Auto Training
Keeps the game's **native Auto Training** running around the clock: detect completion, collect the rewards, return to the screen, start the next session, repeat until you stop it.

### Hyper Skip
Careers advance at protocol speed. No cutscenes to sit through, no results screens to dismiss, no animations to wait out — only the pacing you deliberately configure.

### Character Rotation
Queue trainees with a run count each — Oguri Cap ×5, Vodka ×4, Fine Motion ×6, Tokai Teio ×3 — and Icarus switches between them automatically as careers complete. Loop the list forever or stop at the end. Restart Icarus mid-queue and it resumes on the same trainee with the same progress.

### Live Advisor
A running commentary on the bot's own reasoning: which facility it chose and by how much, what the runner-up was, why it rested, what it expects from a race. Useful for tuning a preset — and for trusting one.

### Parent Suggestions
Scores every valid pair of your veterans against the trainee and preset you've chosen: white/pink/blue sparks weighted toward the skills you actually want, aptitude fixes that clear a real letter grade, and true succession affinity. Always two different characters.

### Veteran Management
Browse, filter and bulk-delete trained characters. Filter by grade, by sparks with star minimums, by favourites, or by **trained during the current session** — then select everything the filter matched in one click. Locked veterans are protected.

### Scheduler
Start on a chosen day and time, run your dailies, run a set number of careers, then idle or shut down — reusing your last setup, or resuming a career already in progress.

### Pause & Resume
Hold a career at the next safe point without ending it. Do your dailies, clear out veterans, delete a career, take a manual action — then resume exactly where the run left off. No restart, no lost progress.

### Multi-Account
Save any number of Steam accounts and switch the active one from the dashboard. Login, game save and per-account state travel together, and a switch that would leave the wrong session behind is refused rather than half-applied.

### Multi-Instance
Run several profiles side by side, each with its own port, config, presets, run history and account — plus a Fleet view that watches all of them at once.

### Discord Webhooks
Rich embeds when a career finishes and when the bot stops: grade, rank points, final stats, fans, skills bought, races run, inheritance sparks, session runtime, session start and end times, and where the run placed in the **current session's** ranking.

### Steam Automation
Handles the Steam side end to end — active-user switching, ticket generation with 2FA, refresh-token reuse, and automatic exponential backoff when Steam rate-limits logins. Session recovery is automatic: an expired token is refreshed and the career carries on without human input.

### Emulator & Game Automation
Launches the game against the right account, captures a fresh session when one is needed, and closes the client again when it's done — so an unattended overnight run survives an expired session, a game update, or an account switch.

### Dailies
Team Trials until RP runs out, Daily Races to the cap, Legend Races against a boss you pick, and a Daily Shop sweep within a gold budget.

### Statistics
Every completed career is recorded: grade, rank score, stats, fans, wins, races, skills, sparks, deck, and true wall-clock duration measured career start to career completion — pauses, breaks and recoveries included. Feeds the run-history dashboard, leaderboards, a Hall of Fame, deck forecasting and a weekly digest.

### Accessibility
Colour-vision-deficiency palettes, a high-contrast mode, adjustable text size and reduced motion — applied before first paint and remembered between sessions.

### Modern UI
A matte-black dashboard built for information density: live resource HUD (TP · RP · Carrots · Gold · Clocks), per-turn decision log with reasoning, run dashboard, bond levels, a filterable console with one-click export, and themes.

---

## Requirements

- **Windows**, with the Umamusume (Steam) client installed and running at first login
- **Python 3.10–3.13** and **Node.js** — the launcher installs both if they're missing
- Internet for first-time setup and updates

## Using it

1. Double-click **`Start Icarus.bat`**. The dashboard opens at <http://127.0.0.1:1616>.
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

---

## Honest notes

- **Automating the game is against Cygames' Terms of Service and carries real account risk.** Human-like pacing, randomised delays and step-away breaks make the traffic look less mechanical, but nothing makes automation undetectable and no one should tell you otherwise. Use in moderation, at your own risk.
- **Don't expose the control panel.** The API has no authentication because it is designed to be local-only. Don't change the bind host and don't port-forward it.
- **Card and race data comes from your own game files.** After a game update, launch the game once so it patches `master.mdb`, then reload master data in Icarus — new support cards and races appear automatically.

---

<div align="center">

**[Discord](https://discord.gg/wpbd3hTBDc)**

</div>
