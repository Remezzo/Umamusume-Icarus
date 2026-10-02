<div align="center">

<img src="https://raw.githubusercontent.com/Remezzo/Umamusume-Icarus/main/icarus.png" alt="Icarus" width="120" />

# Icarus

### The original headless API bot for Umamusume.

#### Every scenario. Every account. Start to bank, hands-free.

**Icarus plays Umamusume: Pretty Derby for you — through the game's own protocol, not your screen.**
It signs in, picks up the career, trains every turn against your model, races your schedule, answers every event, buys the right skills, banks the parent, clears the box, runs your dailies, fields your Team Trials team, runs your club, tidies your friend list and starts the next career. Then it does it again. And again.

<!--DEVONLY:START-->
[![Download](https://img.shields.io/badge/Download-Icarus.exe-D4A017?style=for-the-badge)](https://github.com/Remezzo/Umamusume-Icarus/releases/latest)
&nbsp;
[![Discord](https://img.shields.io/badge/Discord-Join_the_Icarus_hub-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/wpbd3hTBDc)

![Platform](https://img.shields.io/badge/platform-Windows-0078D6)
![Version](https://img.shields.io/badge/release-5.4-D4A017)
![Signed updates](https://img.shields.io/badge/updates-Ed25519_signed-1f7a4d)
![Scenarios](https://img.shields.io/badge/scenarios-URA_%C2%B7_Unity_Cup_%C2%B7_MANT_%C2%B7_Grand_Live-2b2b2b)
![Accounts](https://img.shields.io/badge/accounts-up_to_12-2b2b2b)
![License](https://img.shields.io/badge/license-Proprietary-c02626)
<!--DEVONLY:END-->
<!--PUBLICONLY
[![Download](https://img.shields.io/badge/Download-Icarus.exe-D4A017?style=for-the-badge)](https://github.com/Remezzo/Umamusume-Icarus/releases/latest)
&nbsp;
[![Discord](https://img.shields.io/badge/Discord-Join_the_Icarus_hub-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/wpbd3hTBDc)

![Platform](https://img.shields.io/badge/platform-Windows-0078D6)
![Version](https://img.shields.io/badge/release-5.4-D4A017)
![Signed updates](https://img.shields.io/badge/updates-Ed25519_signed-1f7a4d)
![Scenarios](https://img.shields.io/badge/scenarios-URA_%C2%B7_Unity_Cup_%C2%B7_MANT_%C2%B7_Grand_Live-2b2b2b)
![Accounts](https://img.shields.io/badge/accounts-up_to_12-2b2b2b)
![License](https://img.shields.io/badge/license-Proprietary-c02626)
PUBLICONLY-->

<sub>Windows · Steam · Global client · part of the Icarus Suite</sub>

</div>

---

## At a glance

| | |
|---|---|
| **Scenarios** | URA Finals · Unity Cup · Make a New Track · Grand Live — each with its own strategy, not one approximation stretched over four |
| **Two ways to train** | Icarus plays every turn itself, **or** keeps the game's own Independent Training running back to back |
| **Speed** | A full URA, Unity Cup or Grand Live career in about **17 minutes** — no cutscenes, no results screens, no animations, at a pace that still looks human |
| **Accounts** | Up to **12** game accounts behind one Steam sign-in, each with its own settings, setup and history |
| **Beyond careers** | Dailies, Team Trials team, **whole-club management**, friend-list cleanup, inventory, vouchers, support-card upgrades, reward claims |
| **How it plays** | The game's own API. **No OCR. No screenshots. No clicks. No game window.** |
| **Hands-off** | Weekly schedule, character rotation, dailies between careers, box-full cleanup, self-healing sessions |
| **Trust** | Human-like pacing calibrated from 58 real careers · signed updates · local-only dashboard · credentials encrypted by Windows |
| **Quality** | 11,600+ automated checks on every release, and a verifier that boots the real executable before anything ships |

---

<!--DEVONLY:START-->
> [!IMPORTANT]
> ### Quick start — double-click `Start Icarus.bat`
>
> First launch builds an isolated Python environment, installs every dependency from **prebuilt wheels** (no Visual C++ Build Tools required), fetches **Node.js** if it's missing, then starts the bot and opens the dashboard. Every launch after that is instant.
>
> Needs internet on the first run. If Python isn't installed and `winget` is available, the launcher handles it; otherwise grab Python 3.10–3.13 from [python.org](https://www.python.org/downloads/) and tick **"Add python.exe to PATH"**.
<!--DEVONLY:END-->
<!--PUBLICONLY
> [!IMPORTANT]
> ### Quick start — double-click `Icarus.exe`
>
> That is the whole setup. Everything Icarus needs is inside that one file —
> nothing to install, nothing to extract. The dashboard opens in your browser
> at <http://127.0.0.1:1717>.
>
> 1. Put `Icarus.exe` in a folder of its own (not Downloads — it keeps your
>    settings, sign-in and run history beside itself).
> 2. Double-click it. Windows may warn you the first time: the build is signed,
>    but with our own certificate rather than one Microsoft already knows, so
>    SmartScreen has no reputation to go on. **More info → Run anyway.** If
>    your antivirus quarantines it, add the folder to its exclusions and
>    download it again.
> 3. **Sign in to Steam once** with the account that owns Umamusume. The game
>    doesn't need to be open, and Icarus keeps the session — every later
>    sign-in is unattended.
> 4. Open your account, pick the deck, friend card, trainee and parents, choose
>    a preset, and press **Start**.
PUBLICONLY-->

---

## Why the game's own API changes everything

Most automation for this game watches the screen: screenshots, template matching, OCR, simulated taps. It breaks on a resolution change, a UI patch, a slow animation, a different language, or a window that lost focus — and it can only ever *guess* what the game is showing.

Icarus has **no OCR, no image recognition and no synthetic input anywhere in it.** It talks to the game servers in the same protocol the game client uses, and reads cards, skills, races and events straight from your own installed game data. It doesn't guess what's on the screen. It knows what the server said.

| | Screen automation | Icarus |
|---|---|---|
| Resolution, DPI, language | Must match its templates | Irrelevant |
| Game window | Must stay open and in front | Not needed — the game doesn't even have to be running |
| Your PC while it runs | Taken over | Free — use it, game on it, close the browser tab |
| Career speed | Bound to animations and cutscenes | Bound only to human-like pacing |
| Reading a stat | "probably 1,240 Speed" | Exactly 1,240 |
| Failure rate on a training | Read off a tooltip, maybe | The server's own number |
| A new card, skill or race | Broken until someone re-templates it | Read from the game's own data |
| A game update | Often a week of fixes | Icarus picks up the new version itself |

---

## Everything it does

### Two ways to train

- **Algorithmic Training** — Icarus plays every turn itself: training, rest, recreation, infirmary, races, events, items and skills. You choose the preset; it makes the calls, turn after turn, career after career.
- **Independent Training** — the game's own mode, kept running back to back. Icarus starts a session, the game's server plays the career, and Icarus banks it and starts the next — with your race schedule and skill lists applied. If your chosen friend card isn't on offer it keeps looking until it is; if the parents you picked are gone, it picks your best pair rather than stopping.
- **When to stop** — after a number of careers, at a fan total, or never.
- **Restore TP** with drinks, carats or both (drinks first) the moment it runs dry, so the loop never idles on an empty bar.

### A training brain you control

- **Five boxes, one preset** — **Training**, **Scenario mechanics**, **Skills**, **Racing** and **Events**. Every change saves as you make it.
- **Generate** builds a preset for the trainee you picked; **Export** and **Import** share them as files.
- **Scoring model** — stat weights and caps, per-year mood and energy thresholds, failure-risk limits, rest and summer-camp policy, friendship and bond value, hint value, support-card synergy.
- **Watch it think** — the live **Training evaluation** shows every facility's score and why the winner won; **Decision reasoning** explains every move, turn by turn.
- **Events** — a full event-outcome database picks the best choice for your build, with per-preset overrides.

### Every scenario, done properly

- **URA Finals** — the classic, finals included.
- **Unity Cup** — team roster, divisions and team races.
- **Make a New Track (MANT)** — the item shop with per-item priorities and budget floors, and a dedicated scorer for the last two turns.
- **Grand Live** — songs follow the **Hype gauge** so concerts land as **Great Successes**; techniques once the gauge is full; in the Senior year it buys toward **18 songs by turn 70** for the rare scenario skill. Songs follow the Game8 tier list, lessons follow uma.guide's ratings, and energy lessons are taken only when energy is low enough to need them.

### Racing that protects the career

- **Your schedule is in charge.** Nothing ever skips a race you booked — Icarus warns you about a risky plan, it never overrides it.
- **Objectives** — it enters the right race for every career goal, including turns where more than one race satisfies it, and never burns a turn on the wrong one.
- **Fan farming** — every free turn after the debut gets the best G1, G2 or G3 she's suited for: G1 first, then the most fans. Algorithmic careers leave summer camp to training.
- **Fan support** — suited G1s on free turns in years 1–2, so fan goals are met without you planning them.
- **Run every suited G1** — or build the schedule by hand, filtered by surface, distance and running style.
- **Clocks** — retry a lost race with an Alarm Clock on the races you mark, or spend them freely.
- **Back-to-back racing** — the game's hidden streak penalty is flagged before it costs you stats.

### Skills it buys like an expert would

- **Your list, top to bottom.** Skills you list are bought before anything Icarus would choose — and a bare name takes the whole ○ → ◎ ladder.
- **Then, in a proven order:** the scenario's own skills (the best rating per SP on the shelf), then skills that work in any race, then style and distance skills she's B or better at, then debuffs, then greens, and last anything for a style or distance she can't run. Inside a tier, the most rating per SP wins; a ◎ is valued at what it *adds* over the ○.
- **Mid-career, at your threshold** (say 400 SP) it buys only useful skills — your list, or the top tiers — never junk just to spend points. **At the career end it spends everything.**
- **Every skill the shop really sells.** Icarus knows the exact shop for each career — the skills the deck hinted plus the trainee's own set at her potential — and never sends a skill the game would refuse.
- **Suggest from deck & uma** fills the list with everything this career can actually offer, in the order the buyer would take it, narrowed by surface, distance and style.
- **23 skill groups** — buy or ban a whole category at once: by what a skill *is* (gold, green, unique, debuff, ◎), what it *does* (speed, acceleration, recovery, start, positioning, vision), where it applies, and the style, distance or surface it's tied to. Want no golds? Tick one box.
- **Total transparency** — at every career end the log says what was bought, what the game refused, how many skill points were left, and why.

### Decks, friends and parents

- **Recommend from card data** — proposes a deck from the cards' own effects, before you've run a single career.
- **Suggest from run history** — ranks your cards by the careers they actually produced and names the weakest link in your current deck. **Save as new deck** writes it to the slot you pick.
- **Smart pickers** — search, sort and filter trainees by aptitude grade; filter friend cards by type, rarity, limit break or the people you follow; a card the career can't start with is greyed out *with the reason*.
- **Friend support done right** — automatic picks only ever borrow an **SSR at max limit break**. Pick a specific friend's card and Icarus keeps it across refreshes, re-rolling the list until that card turns up.
- **Parents** — owned or borrowed, sorted four ways, with a spark filter whose thresholds count the stars across the parent *and* both of its parents. Every spark the game can roll is searchable.
- **Inheritance preview** — projected aptitudes at career start, with both lineages pooled.
- **Borrowed parents** — a backup swaps in automatically when a borrow is refused, and the daily borrow limit is tracked for you.
- **Parents in use are untouchable.** Nothing Icarus deletes can ever be a parent you're running.
- **Hover anything** — a skill shows the game's description, cost and rating; a parent shows its stats and the sparks of it and both its parents.

### Veterans that manage themselves

- **Every trained uma scored 0–100 as a parent.** Drag the keep score and flag everything below it in one move.
- **Box full? Handled.** With auto-delete on, Icarus clears the weakest unprotected veterans and retries the start — on the very first start of a run too. No more waking up to a loop stopped at "storage full".
- **Protected, always:** favourites, locked umas, Team Trials members, parents in use, parents of other veterans, and the last of each kind.

### Up to 12 accounts, one dashboard

- **Sign in to Steam once.** Every other game account is reached with its own Data Link password — add them one at a time, or **paste a whole list** and Icarus checks each password with the game as it adds it.
- **Every account keeps its own setup** — preset, deck, trainee, parents, rotation — saved when you switch and restored when you come back.
- **Visit now** refreshes any account and comes straight back; **Claim on all** visits every account and collects everything.
- **Safe by design** — Icarus refuses any switch that would strand an account without its Data Link password.

### Run your whole club

From any account in a club, Icarus handles the club work for you:

- **Invite trainers** by pasting Trainer IDs — it skips members and people already invited — and withdraw invites.
- **Fans this month** for every member, tracked from the first reading of the month.
- **Leader controls** — promote, demote, remove members, hand over the club, and edit its name, intro, join rules and playstyle.
- **Not in a club yet?** See your invites and accept one, ask to join a club by its ID, or found your own.
- **Donations on autopilot** — donate to members' open requests automatically (up to the game's daily limit, oldest request first, only items you hold, never to your own request), or by hand.
- **Item requests** — request what you need and **keep it requested**: Icarus asks again each time the last request closes.
- Club and Team Trials steps run between careers for the running account, paced and spaced out.

### Friends, inventory and cards

- **Friends** — follow by pasting Trainer IDs; see who follows the account and who it follows, with last logins and mutuals marked.
- **Clean up** — remove inactive followers or unfollow inactive accounts after the period you choose. Mutuals are protected, it stops at the first refusal, and someone whose last login can't be seen is never counted as inactive.
- **Inventory** — everything the account holds, with Monies, Carats and Support Points up top; **sell** what the game buys back at the game's own price.
- **Vouchers** — redeem a brand-new account's Head Start 3★ Voucher for the trainee you want.
- **Support cards** — your collection as card art with copies, level and limit breaks; **limit break**, **level up** or both, up to five at a time, each showing its cost first — and save them straight to a deck.

### Team Trials, handled

- **Auto-select your team** — the strongest veteran in every slot of all five races, one per character, each on her best running style. Run it now or once a day before Team Trials; the team is only saved when it beats the one you have.
- **Spend RP your way** — wait for a full bar and race it in one sitting, or race each point as it comes back. Choose the opponent: strongest, medium or weakest.

### Dailies, without lifting a finger

- **Reward collection**, **Team Trials**, **Daily Races** (Moonlight Sho by default, or pick by reward), **Legend Races** against the boss you choose, and the **Daily Shop**.
- **Between careers** — with **Run between careers** on, any ticked daily that's ready runs between two careers, after a short human-like wait.
- **Counted against the game's own daily reset** (11:00 US Eastern), so an interrupted day picks up where it stopped. A Legend race a previous run left half-entered is finished without a new entry.
- Independent Training is never held up by dailies — starting and banking always come first.

### Character rotation

Queue trainees per account — Oguri Cap ×5, Vodka ×4, Fine Motion ×6 — and drag them into the order you want. Icarus only queues trainees the account owns, switches between them as careers finish, and repairs the queue itself if something goes wrong. Restart mid-queue and it picks up on the same trainee.

### A weekly schedule that's always in charge

- **Time windows per day of the week** that start and stop Icarus, with dailies and breaks built in, plus saved **templates**.
- **Master switch with exceptions** — turn Icarus off but keep, say, the dailies or Independent Training alive.
- **Stop means stop** — press Stop inside a window and it stays stopped until the next window, even across a restart. The schedule only ever stops a run it started.

### A dashboard built for watching it work

- **Dashboard** — what Icarus is doing right now with Start, Pause, Resume and Stop; the live career; what happens next; History and Trends for every finished career; and your **Roster** — every trainee with her Bond level, her careers and her place in the queue.
- **The live rail** — right now, what needs attention, what's next, **Today** across every account (Independent Training runs, fans, carats, claims), her condition and the next race. Stats, training evaluation, decisions, races run, skills and purchases, finished careers and recent activity update as she plays.
- **Accounts** — each card shows what that account is doing; open one for Overview, Training, Dailies, Veterans, Support Cards, Clubs, Friends, Inventory and Activity.
- **Statistics** — finished careers by range (today, 7 days, 30 days, all time), scenario, outcome or text; per account; leaderboards and a Hall of Fame.
- **Logs** — Activity as readable cards and the full Console, filterable, with one-click export. Whatever goes wrong, the log explains it in plain language: what it tried, what the game answered, and what to do.
- **Help, built in** — getting started, how the loop behaves, which skills it buys, clubs and friends, troubleshooting, an **error-code lookup that filters as you type** (every error the game can answer with, in the game's own words, plus what Icarus does about it), **every function** explained, and a glossary.
- **What's New** for every build, health checks, game-data tools, and a diagnostics bundle with passwords, tokens, webhook URLs and Trainer IDs masked.

### Discord notifications

Rich posts when a career finishes or the bot stops: grade, rank, final stats, fans, **every skill bought by name**, races run, inheritance sparks and session timing. As many endpoints as you like, you choose what goes in each post, and **Mention on errors** pings you only when something needs you.

### It heals itself

- **A health check every turn.** A career the game won't advance is recorded, abandoned and started fresh.
- **Session recovery** — an expired session is renewed and the career carries on.
- **Steam hiccups** never cost you your sign-in; only a genuinely expired login asks you again.
- **Busy servers and maintenance** are waited out and retried, never hammered — maintenance never counts as a failure.
- **Game updates** — Icarus picks up the new game version itself and adopts a server data update mid-run instead of stalling.
- **Never stuck "running"** — every way a run can end is reported, on the dashboard and in Discord.

### Comfortable to use

- **Accessibility** — text size, colour-vision palettes (protanopia, deuteranopia, tritanopia), high contrast and reduced motion.
- **Saves as you change** — no Save buttons to forget.
- **Remote access (optional, off by default)** — reach your dashboard through your own tunnel by allowing its hostname.

---

## Built to be trusted

- **Human-like pacing, calibrated from 58 real careers.** Every request is paced like a person tapping through the game, with natural variation and short pauses between races. The pacing is part of the build: it can't be dialled down to something that looks mechanical — so no Icarus user's shortcuts put everyone else at risk.
- **Your credentials stay on your PC.** The Steam session and Data Link passwords are encrypted with Windows' own protection for your user account. Nothing goes anywhere except the game's and Steam's own servers.
- **Local by default.** The dashboard listens on your own machine only, and refuses requests from other websites.
- **Signed updates.** Every release is signed; both the in-app updater and the manual updater install only a release whose signature and checksum verify.
- **Tamper-proof.** The build is compiled and obfuscated, its settings are sealed, and a modified build refuses to run. One copy per PC, so two instances can never fight over one account.
- **Scrubbed logs.** Exports and diagnostics leave out tokens, passwords and personal paths.

---

## Requirements

- **Windows 10 or 11**, and a Steam account that owns Umamusume: Pretty Derby (Global) — Linux works too via Wine, see below
<!--DEVONLY:START-->
- **Python 3.10–3.13** and **Node.js** — the launcher installs both if they're missing
<!--DEVONLY:END-->
<!--PUBLICONLY
- **Nothing else to install.** Everything ships inside `Icarus.exe`.
PUBLICONLY-->
- Internet access

## Using it

<!--DEVONLY:START-->
1. Double-click **`Start Icarus.bat`**. The dashboard opens at <http://127.0.0.1:1616>.
<!--DEVONLY:END-->
<!--PUBLICONLY
1. Double-click **`Icarus.exe`**. The dashboard opens at <http://127.0.0.1:1717>.
PUBLICONLY-->
2. **Sign in to Steam** once — on the Accounts page, or Settings → Game access. Add your other game accounts with their Data Link passwords.
3. Open an account → **Training**: pick the deck, the friend card, the trainee and two parents, then the scenario and the training type.
4. Tune the preset in its five boxes, or press **Generate**.
5. Press **Run now** — or set up the **Schedule**, **Character rotation** and **dailies between careers**, and walk away.

The console window *is* Icarus — closing it stops everything. Closing the browser tab changes nothing; reopen the address and you're back.

## Updating

When a new version is out: **Settings → Updates → Check for updates → Download & install**, then restart. Accounts, presets and history are kept — only the program is replaced — and only a signed release is ever installed. If Icarus can't start at all, `Update Icarus.bat` beside it does the same, with the same signature check.

<!--DEVONLY:START-->
## Manual setup

```bash
# Python 3.10–3.13 and Node.js already installed
pip install --prefer-binary -r requirements.txt   # --prefer-binary avoids needing a C++ compiler
npm install
python main.py
```
<!--DEVONLY:END-->

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
5. **Run Icarus.** Open a terminal *in the folder containing the executable*, then:

   ```bash
   wine Icarus.exe
   ```

   Sign in to Steam as usual — the dashboard opens at the address Icarus prints in its console.

> [!TIP]
> **"Node.js is only supported on Windows 8.1, Windows Server 2012 R2, or higher"** — open the Wine registry editor with `wine regedit`, go to `HKEY_CURRENT_USER\Environment`, create a **String Value** named `NODE_SKIP_PLATFORM_CHECK` with value `1`, then restart everything running under Wine (Icarus included).

---

## FAQ

**Does the game have to be open?**
No. Icarus talks to the servers directly — the game doesn't need to be running, or even in front of you.

**Can I play on the account while Icarus is running it?**
Stop Icarus first. The game and Icarus share one device seat, so signing in to the game on that account signs one of them out.

**How many accounts can it run?**
Up to 12 saved accounts, one running at a time. Visits, claims, rotation and dailies move between them for you.

**How long does a career take?**
About 17 minutes for URA, Unity Cup or Grand Live, and about half an hour for MANT, at the built-in human-like pace. In Independent Training the game's own server plays the career (about 50 minutes) and Icarus starts and banks it.

**What happens after a game update?**
Open the game once so it downloads the new data. Icarus picks up the new version itself; new cards and races appear after a restart, or straight away with **Regenerate** in Settings.

**Will it ever bank a career with skill points left?**
Only when there's genuinely nothing left in the shop for that trainee — and the log says so.

**Where's my data?**
In the folder beside `Icarus.exe`. Nothing is stored anywhere else, and nothing leaves your PC except requests to the game and to Steam.

**Something went wrong — how do I get help?**
Logs → Console → **Export** gives a credential-free file; Settings → Data & health → **Save bundle** gives a deeper, masked one. Post it in the [Icarus Discord](https://discord.gg/wpbd3hTBDc).

---

## Honest notes

- **Automating the game is against Cygames' Terms of Service and carries real account risk.** Human-like pacing makes the traffic look like a person's, but nothing makes automation undetectable, and nobody should tell you otherwise. Use it in moderation, at your own risk.
- **Keep the dashboard to yourself.** It's local-only by default. If you turn on Remote access, anyone who can reach that address controls Icarus — only do it behind a tunnel you trust.
- **The game has no undo.** Club actions, sales, deletions and voucher redemptions are real; Icarus shows the cost first and queues them, but once they run, they're done.

---

## The Icarus Suite

Every tool in the suite speaks the game's own API — the same protocol work underneath, a different job on top. All of them are available now.

| Tool | What it does |
|---|---|
| **[Icarus](https://github.com/Remezzo/Umamusume-Icarus)** | Career automation — this one. Every scenario, every turn, start to bank. |
| **[Sundial](https://github.com/Remezzo/Umamusume-Sundial)** | A multi-account manager. Runs every account you own from one dashboard: rewards, dailies, and an Independent Training loop that starts, watches and banks careers on its own. Fully headless. |
| **[Overseer](https://github.com/Remezzo/Umamusume-Overseer)** | A companion overlay: live translation in 25+ languages, Hyper Skip, performance enhancements, Team Trials tools, career tracking, and event, training and race prediction before you click. |
| **[Fortuna](https://github.com/Remezzo/Umamusume-Fortuna)** | A fully headless account reroller for Global: accounts minted through pure API calls, presents claimed, the banner of your choice pulled, a transfer password published and the history recorded. |
| **[Un-Follower](https://github.com/Remezzo/Umamusume-Un-Follower)** | Cleans up your follow list: finds inactive trainers and one-way follows, and unfollows them safely through the game's own API. |
| **[Club Manager](https://github.com/Remezzo/Umamusume-Fan-Tracker)** | Tracks every club you care about and posts a leaderboard to Discord on its own schedule — quotas, month-end projections, roster changes, milestones and trainer lookups. |
| **Navigator** | The research rig that captures and replays the game's wire protocol. Everything above is built on what it finds. |

-----

<div align="center">

**[Download Icarus](https://github.com/Remezzo/Umamusume-Icarus/releases/latest)** · **[Join the Discord](https://discord.gg/wpbd3hTBDc)**

</div>
