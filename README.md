# ☕ Kedai Senja — A Cozy Cafe Manager Game

> Serve customers, craft their orders, and grow your little cafe under a drifting sunset sky.

**Kedai Senja** ("Sunset Café") is a fast, cozy cafe-management game. The frontend is a single static HTML file hosted on **GitHub Pages**, and an optional **Supabase** backend adds a global leaderboard (no login required) — a full-stack game with zero servers to maintain.

## ✨ Features

- **Real-time service loop** — customers arrive, order, and lose patience. Be quick, be accurate.
- **Hands-on drink crafting** — pick ingredients, brew, then serve. Wrong recipe? The ingredients are wasted.
- **Combo & tip system** — chain happy customers for streak bonuses and better tips.
- **Kitchen upgrades** — faster espresso machine, bigger serving rack, extra seats, and new recipes (Iced Milk Coffee, Hot Chocolate, Toast).
- **Decorations** — plants, lamps, posters, an aquarium, a piano, and a cafe cat. Each one makes customers more patient and generous, and appears in your cafe.
- **Daily goals** — hit the daily revenue target for a cash bonus; **VIP customers** 👑 pay double but are less patient.
- **13 achievements** — from *First Customer* to *Dream Cafe*.
- **Chiptune music & SFX** (mutable), a pause menu (`Esc`), and auto-pause when you switch tabs.
- **Save codes** — export/import your progress to move between devices (no account needed).
- **Installable PWA** — add it to your home screen; works offline after the first visit.
- **Dynamic day cycle** — the sky shifts from golden hour to dusk, with a rush hour mid-day.
- **Built-in interactive tutorial** — a spotlight walkthrough for first-time players (re-open any time with ❓).
- **Cartoon pixel-art look** — chunky outlines, a pixel sunset window with a day/night sky, and procedurally generated pixel-art customers (every visitor looks different).
- **Global leaderboard** — top-10 baristas with custom names, powered by Supabase. Optional and fully invisible to players: no sign-up, no login.
- **No login, ever** — open the page and play. Progress is saved in `localStorage`; the leaderboard is an optional extra.
- **Sound effects** (WebAudio, mutable), keyboard shortcuts, responsive layout for desktop and mobile, and reduced-motion support.

## 🎮 How to Play

1. **Watch the seats.** Each customer shows an order bubble (e.g. 🥤) and a patience bar. If the bar empties, they leave and your rating drops.
2. **Pick ingredients.** Tap ingredients to fill the cup (max 3), or tap a recipe in the Recipe Book to auto-fill it.
3. **Brew.** When the cup matches a recipe, its name appears. Press **Brew** and wait for the progress bar.
4. **Serve.** Finished drinks appear in the serving rack. Tap one to hand it to the customer who ordered it (the most impatient one is served first).
5. **Earn & upgrade.** After each day, spend your money in the 🛒 Shop on kitchen upgrades and decorations.

### Starter recipes

| Drink | Ingredients | Price |
|---|---|---|
| Black Coffee ☕ | Coffee | Rp12k |
| Milk Coffee 🥤 | Coffee + Milk | Rp18k |
| Sweet Tea 🍵 | Tea + Sugar | Rp14k |

Unlockable in the shop: Iced Milk Coffee 🧋 (Coffee + Milk + Ice), Hot Chocolate 🍫 (Milk + Chocolate), Toast 🍞 (Bread).

### Tips

- Keep your **combo 🔥** alive — each consecutive happy customer adds a bigger bonus.
- Buy the **Espresso Machine** and **Serving Rack** first; they remove the biggest bottlenecks.
- During **rush hour**, pre-brew drinks you know will be ordered and keep them in the rack.
- **VIP customers** 👑 are worth double — serve them first.
- Reach the 🎯 daily goal (shown in the top bar) for a Rp40k bonus.

### Controls

| Input | Action |
|---|---|
| `1`–`7` | Add ingredient |
| `Enter` / `Space` | Brew |
| `Backspace` | Clear cup |
| `Esc` | Pause / menu |
| Mouse / Touch | Everything else |

## 🏗️ Architecture

```
GitHub Pages (static)            Supabase (free tier, optional)
┌────────────────────┐  HTTPS   ┌──────────────────────────────┐
│ index.html + JS    │ ───────▶ │ Postgres + Row Level Security │
│ config.js          │  REST    │  ├ scores  (public read)      │
└────────────────────┘          │  └ submit_score() RPC (write) │
                                └──────────────────────────────┘
```

GitHub Pages only serves static files, so the optional "back end" is Supabase's REST API called straight from the browser (plain `fetch`, no SDK). There is **no login**: each browser generates a random player id and secret. Tables are write-protected; scores are sent through the `submit_score()` function, which checks the secret (stored only as a hash), and caps how fast a score can grow.

| Path | Purpose |
|---|---|
| `index.html` | The whole game (UI, logic, leaderboard client) |
| `config.js` | Supabase URL + public anon key |
| `supabase/schema.sql` | Tables, RLS policies, `submit_score()` function |
| `manifest.webmanifest`, `sw.js`, `icon*.png/svg` | PWA: install + offline support |
| `og.png` | Social preview image |
| `LICENSE` | MIT license |
| `.github/workflows/pages.yml` | Auto-deploy to GitHub Pages on push to `main` |

## 🚀 Setup & Deploy

1. **Create a Supabase project** (free) at [supabase.com](https://supabase.com).
2. Open **SQL Editor**, paste `supabase/schema.sql`, and run it. (No auth settings needed.)
3. In **Project Settings → API**, copy the **Project URL** and **anon public key** into `config.js`.
4. Push everything to your GitHub repo (`main` branch).
5. In **Settings → Pages**, set **Source** to **GitHub Actions**. Every push redeploys to `https://<your-username>.github.io/<repo-name>/`.

Skip steps 1–3 to play fully offline, or just open `index.html` locally.

### Notes

- Never commit the Supabase `service_role` key — only the public anon key.
- In `index.html`, replace `https://YOUR-USERNAME.github.io/YOUR-REPO/og.png` (the `og:image` meta tag) with your real URL so link previews show the banner. Also put your name in `LICENSE`.
- After changing game files, bump `V` in `sw.js` if players report seeing stale versions.
- Without logins, clearing browser storage starts a new player; the old leaderboard row stays.
- Anti-cheat is basic (server-side caps per submission). For stricter validation, add a Supabase Edge Function.

## 🗺️ Ideas for Contributions

- More recipes, customer types, and random events
- Daily goals and achievements
- Weekly leaderboards and friend codes
- Staff members (barista, cashier)
- Localization (the UI is currently in Indonesian)

## 📄 License

MIT — see [`LICENSE`](LICENSE).
