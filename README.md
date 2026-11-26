# ☕ Kedai Senja — A Cozy Cafe Manager Game

> Serve customers, craft their orders, and grow your little cafe under a drifting sunset sky.

**Kedai Senja** ("Sunset Café") is a fast, cozy cafe-management game that runs entirely in the browser. No build step, no dependencies, one HTML file.

## ✨ Features

- **Real-time service loop** — customers arrive, order, and lose patience. Be quick, be accurate.
- **Hands-on drink crafting** — pick ingredients, brew, then serve. Wrong recipe? The ingredients are wasted.
- **Combo & tip system** — chain happy customers for streak bonuses and better tips.
- **Kitchen upgrades** — faster espresso machine, bigger serving rack, extra seats, and new recipes (Iced Milk Coffee, Hot Chocolate, Toast).
- **Decorations** — plants, lamps, posters, an aquarium, a piano, and a cafe cat. Each one makes customers more patient and generous, and appears in your cafe.
- **Dynamic day cycle** — the sky shifts from golden hour to dusk, with a rush hour mid-day.
- **Built-in interactive tutorial** — a spotlight walkthrough for first-time players (re-open any time with ❓).
- **Auto-save** — progress is stored in `localStorage`.
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

### Controls

| Input | Action |
|---|---|
| `1`–`7` | Add ingredient |
| `Enter` / `Space` | Brew |
| `Backspace` | Clear cup |
| Mouse / Touch | Everything else |

## 🚀 Run It

Just open `index.html` in a browser. To host it for free with **GitHub Pages**:

1. Push `index.html` to your repo.
2. Go to **Settings → Pages**.
3. Set the source to your branch (`main`) and the `/ (root)` folder.
4. Your game will be live at `https://<your-username>.github.io/<repo-name>/`.

## 🧱 Tech

Vanilla HTML, CSS and JavaScript. Fonts are loaded from Google Fonts (with system fallbacks). Sound is generated with the Web Audio API — there are no external assets.

## 🗺️ Ideas for Contributions

- More recipes, customer types, and random events
- Daily goals and achievements
- Staff members (barista, cashier)
- Localization (the UI is currently in Indonesian)

## 📄 License

Choose a license for your repo (e.g. MIT) and add a `LICENSE` file.
