# Monopoly GO! Manual Card Tracker & Transfer Optimizer

A professional, mobile-first web application designed for Monopoly GO! players who manage multiple alternate accounts ("alts"). This tool allows you to manually track missing stickers across 2 to 5 accounts and instantly calculates the most optimal, load-balanced transfer routes to complete your sets.

---

## 🚀 Features

* **Dynamic Multi-Account Support:** Seamlessly manage between 2 and 5 alternate accounts with real-time profile tabs and custom status badges.
* **Smart Load-Balanced Optimizer:** The core calculation algorithm doesn't just find donors; it tracks `senderLoad` and balances the card-sending distribution so no single account maxes out its daily trade limits prematurely.
* **Persistent Local Storage:** Integrated with `localStorage` (key: `mgo_v3`). Your checked data, selected language, and account count are automatically saved and restored on page refresh.
* **Bilingual Interface:** Instant UI toggle between Bulgarian (🇧🇬) and English (🇬🇧) with dynamic string translation components.
* **Mobile-First UX/UI:** Designed with a sleek, native-app-like dark theme using the *Nunito* font, responsive grids, fast accordion toggles, and safe-area padding optimized for "Add to Home Screen" usage.
* **Batch Controls:** Quick toolbar selectors inside each album page to mark all cards as owned or missing with a single click.

---

## 🛠️ Technical Specifications

* **Architecture:** 100% Vanilla HTML5, CSS3 (Custom Variables), and JavaScript (ES6+). Zero external dependencies or heavy frameworks.
* **Album Matrix:** Configured for standard Monopoly GO! album layouts:
    * `N_PAGES = 21` (Total album pages)
    * `N_CARDS = 9` (Stickers per page)
* **Account Limits:** Safe range constraints set between `MIN_ACC = 2` and `MAX_ACC = 5`.

---

## 🧠 How the Algorithm Works

When you click **"Calculate Transfers"** (`calculate()`), the engine performs the following operations:
1. It flattens the matrix and maps out every card flagged as missing (`true`).
2. For every missing card, it evaluates all other accounts to build a potential donor pool (accounts where that card is marked as owned).
3. If no donors are found, it flags the card under a specific warning state (`unsolvable`).
4. If multiple donors exist, it **sorts them by their current sending load** and picks the donor with the least sent cards. This distributes the trade execution burden evenly.
5. Generates a beautifully formatted modal summarizing structural targets: *Total Missing*, *Can Be Transferred*, and *Unsolvable Cards*, grouped cleanly by receiving accounts.

---

## 💻 How to Run Locally or Deploy

Since this project is completely serverless and independent, running it is plug-and-play:

1. **Locally:** Clone the repository and simply double-click the `index.html` file to open it in any modern browser.
2. **GitHub Pages (Hosting):**
   * Go to your repository **Settings** -> **Pages**.
   * Under **Build and deployment**, set the source to `Deploy from a branch` and select `main` (root).
   * Your app will be live at `https://dadfafafsg.github.io/Monopoly/`.
3. **Install as a PWA (Mobile):** Open the live URL on your smartphone via Chrome or Safari, tap the browser menu (three dots / share button), and select **"Add to Home Screen"** for a full-screen, standalone app experience.
