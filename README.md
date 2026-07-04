# 🎮 Nexus Arena

**The Future of Browser Gaming.**

A single-file, zero-dependency gaming platform with 7 games, a genuine AI opponent in three difficulty tiers, a reactive robot companion, and a distinct visual world for every game — all in one `index.html`.

🔗 **Live:** [ai-tictactoe-olive.vercel.app](https://ai-tictactoe-olive.vercel.app)

---

## Games

| Game | Mechanic | AI | Theme |
|---|---|---|---|
| **Tic-Tac-Toe** | Positional, adversarial | Full minimax (perfect play at Grandmaster) | Cyber violet/cyan, hex board |
| **Connect 4** | Positional, adversarial | Alpha-beta + heuristic eval | Arcade cabinet — steel frame, marquee header, rivets |
| **Gomoku** | Positional, adversarial (11×11, 5-in-row) | Candidate-restricted alpha-beta | Zen ink — wood board, black/cream stones |
| **Rock Paper Scissors** | Hidden-information, simultaneous | Pattern-reads your last 3 picks (Markov) at Grandmaster | Vintage — aged paper, wax-seal medallions |
| **Memory Match** | Turn-passing recall | Simulated imperfect memory (recall % scales by difficulty) | Old Japan — washi paper, ink stones, hanko red |
| **Dragon's Path (Snake)** | Real-time, single-player | — (no adversary) | Samurai dojo — synthesized dragon roar on death |
| **Puzzle Atelier** | Rearrange-to-solve | — (no adversary) | Gallery/museum — 6 original illustrations across 3 categories |

Every game shares one generic engine contract (`emptyBoard / legalMoves / applyMove / checkWin / checkDraw / evaluate`) where it genuinely fits (the 3 positional games). RPS, Memory, Snake, and Puzzle are intentionally **not** forced into that contract — they're different genres and get their own small state machines instead of a fake abstraction.

## Screenshots

![Tic-Tac-Toe](screenshots/01-tictactoe.png)
![Connect 4](screenshots/02-connect4.png)
![Gomoku](screenshots/03-gomoku.png)
![Rock Paper Scissors](screenshots/04-rock-paper-scissors.png)
![Memory Match](screenshots/05-memory-match.png)
![Dragon's Path](screenshots/06-dragons-path.png)
![Puzzle Atelier](screenshots/07-puzzle-atelier.png)

## Platform features

- **AI Coach** — re-runs your moves through the same search engine used by the AI to flag real mistakes and show the actual better move (Tic-Tac-Toe, Connect 4, Gomoku)
- **Companion** — a robot face with wandering eyes, mood-reactive mouth, and real browser text-to-speech (toggle-able)
- **Local pass-and-play** — every applicable game supports two humans on one device, no account needed
- **Achievements** — real triggers (streaks, flawless games, beating Grandmaster, fastest possible win), toast notifications
- **Settings** — Graphics (particle count/blur), Animation Speed, Language (English / Español / Français)
- **Per-game ambient world** — background color, particle shape, texture pattern, and even the page's base color shift per game tab
- **Accessibility** — full keyboard navigation, visible focus states, `prefers-reduced-motion` respected, ARIA live regions

## Tech

Pure HTML/CSS/JS. No build step, no framework, no dependencies except Google Fonts (Space Grotesk, Inter, JetBrains Mono, Playfair Display) and the browser's native Web Audio / Web Speech APIs.

- Game boards render as inline SVG
- Snake renders to `<canvas>` with a real-time tick loop
- Puzzle pieces use CSS `background-position` slicing over original SVG illustrations
- Sound effects (tones, the dragon roar) are synthesized with Web Audio — no audio files

## Running it

Just open `index.html` in a browser. That's it.

## Deploying it

Any static host works — Netlify, Vercel, GitHub Pages, Cloudflare Pages:

1. Make sure the file is named `index.html` at the root (not in a subfolder)
2. Upload / push it
3. Done — no build command, no environment variables

## Known limitations (honest, not hidden)

- **No persistence** — refreshing the page resets all stats, streaks, and achievements. Everything lives in memory for the session.
- **No accounts / no real online multiplayer** — "local pass-and-play" only. Real multiplayer needs a backend.
- **Puzzle Atelier has 6 images**, not a full 16-image collection — a real starter set, not placeholders faking a bigger number.
- **Coach analysis** doesn't apply to RPS, Memory, Snake, or Puzzle — those games have no board position to evaluate, and the app says so honestly rather than faking a report.

## Roadmap (not built yet)

- Supabase integration for real accounts and persistent stats across sessions/devices
- More puzzle images / categories
- Real online multiplayer (needs backend + realtime sync)

---

Built iteratively, one real feature at a time — no placeholder code, no fake abstractions.
