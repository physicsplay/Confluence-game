# Confluence

A cross-border water-intelligence game for the eTwinning project **Guardians of our Waters**.

**[▶ Play live](https://physicsplay.github.io/Confluence-game/)** — works in any modern browser, on phone, tablet or laptop. No installation, no accounts, no downloads.

---

## What it is

Teams of students from Italy, Spain, Greece, France, Slovakia and Bulgaria each run a **national water-monitoring station** on a map of Europe. Each round, an incident hits the watershed — a chemical spill, algal bloom, sediment pulse, microbial outbreak. The epicenter team sees the strongest signal; downstream teams see weaker echoes; other teams see normal readings.

But teams only see **their own data**. To correctly classify the pressure and respond, they must **trade intelligence across borders** using Intel Credits. All four decisions per round are scored against objective, deterministic criteria — no teacher judging, no voting, no style points.

Designed for ages 14–19. Playing time: ~35 minutes. 2–6 teams.

---

## How to play

### Setup
1. One team opens the live link and clicks **Create a room** → enters a team name → picks their country station.
2. Other teams join using the 4-letter room code (or by scanning the QR code). Each team joins from its own device.
3. Once at least 2 teams are in the lobby, any team can press **Start game**.

### Each round (6 rounds total)
Your station has 8 real-time water-quality parameters (pH, dissolved oxygen, turbidity, nitrate, phosphate, conductivity, temperature, coliforms). Some readings will be in the safe range, some will exceed thresholds. One of your parameters may be **hidden** (sensor offline).

You have two finite resources per game:
- **5 Intel Credits** — spend 1 to see any single parameter from any other team's station.
- **2 Verification Tokens** — spend 1 to unmask a hidden reading on your own station.

You submit four answers:
| Question | Worth |
|---|---|
| **Q1.** Classify the pressure (5 plausible options) | 3 pts |
| **Q2.** Which parameters exceed safe thresholds? (multi-select) | 2 pts |
| **Q3.** Best first intervention | 3 pts |
| **Q4.** Community advisory | 2 pts |
| **Bonus.** Cross-border: downstream team classifies correctly AND traded data | +1 pt |

**10 points available per round. 60+ points total across 6 rounds.**

Rounds auto-resolve when every team has submitted. After a 20-second review of the results, the game advances to the next round.

### Design principles
- **Simple rules, strategic depth.** Hidden information plus scarce resources force real trade-offs about what to reveal and whom to trust.
- **Fully objective scoring.** Every point is deterministic. No teacher arbitration, no audience voting, no points for style.
- **Embedded educational goals.** Data literacy, international collaboration, environmental advocacy and European citizenship are mechanics, not decoration.

---

## For teachers who want to run it in their own classroom

The live link works out of the box. Teams just need internet and a modern browser.

### To fork this and run your own Firebase backend

1. **Fork this repository** (top right → Fork).
2. **Create your own Firebase project** at [console.firebase.google.com](https://console.firebase.google.com).
3. **Enable Anonymous Authentication** (Authentication → Sign-in method → Anonymous → Enable).
4. **Create a Realtime Database** (Build → Realtime Database → Create database, region `europe-west1` recommended).
5. **Set the security rules** to:
   ```json
   {
     "rules": {
       "rooms": {
         "$roomId": {
           ".read": "auth != null",
           ".write": "auth != null"
         }
       }
     }
   }
   ```
6. **Add your GitHub Pages domain** to Authentication → Settings → Authorized domains (e.g. `yourname.github.io`).
7. **Copy your Firebase Web App config** and paste it into the `FIREBASE_CONFIG` object near the top of the `<script type="module">` block in `index.html`.
8. **Enable GitHub Pages** on your fork (Settings → Pages → Deploy from `main` branch, `/` root).

Full step-by-step guide (in Greek): see `ΟΔΗΓΟΣ_FIREBASE_SETUP.md`.

### Offline / single-device version

If your school has unreliable internet, there's also a single-device version that runs entirely locally — one computer, one projector, physical turn-taking. It's in `confluence_guardians_of_our_waters.html`.

---

## Project context

Confluence was built for the eTwinning project **Guardians of our Waters**, which connects secondary schools across six European countries to monitor local water quality, share findings, and develop environmental advocacy.

The game's six educational goals are embedded in its mechanics:

1. **Scientific inquiry & data literacy** — students read and interpret real water-quality parameters against regulatory thresholds.
2. **International collaboration** — cross-border intel exchange is mathematically required to reach high scores.
3. **Environmental advocacy** — every round ends with a real-world intervention and community advisory decision.
4. **Curriculum integration** — science, civics and digital literacy in a single 35-minute session.
5. **Geospatial thinking** — the European map, upstream/downstream propagation, and epicenter dynamics are visible and central.
6. **European citizenship** — cooperation between six countries is the game's core loop, not a theme painted on top.

---

## License

Released under the **MIT License** — see [`LICENSE`](./LICENSE).

You're welcome to fork, modify, translate, or adapt this for your own school or project. If you build something interesting with it, a note back would be appreciated but is not required.

---

## Credits

Designed and built as part of the eTwinning project *Guardians of our Waters* (2025–26). 
