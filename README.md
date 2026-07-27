# 🌗 Abhaya Swara

**A Swara Yoga (Svarodaya Śāstra) companion — know which nāḍī is breathing, right now.**

Abhaya Swara tells you whether your **Iḍā (left / lunar / cooling)** or **Piṅgalā (right / solar / warming)** swara is active at any moment, computed from real sunrise/sunset astronomy for your location — and suggests the activities best suited to that flow.

[![License: MIT](https://img.shields.io/badge/License-MIT-e2c97e.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Android%20%7C%20Web%20%7C%20PWA-38bdf8.svg)]()
[![No backend](https://img.shields.io/badge/backend-none-22c55e.svg)]()
[![Made by Astrogaami](https://img.shields.io/badge/by-Astrogaami-92400e.svg)](https://astrogaami.com)

[**⬇ Download APK**](https://github.com/<your-username>/abhaya-swara/releases/latest) · [**🌐 Live Web App**](https://<your-username>.github.io/abhaya-swara/) · [**Report a bug**](https://github.com/<your-username>/abhaya-swara/issues)

</div>

---

## 📸 Screenshots

<!-- Drop your images in docs/screenshots/ and update these -->
| Home (dark) | Day Schedule | Settings |
|:-----------:|:------------:|:--------:|
| ![Home](docs/screenshots/home-dark.png) | ![Schedule](docs/screenshots/schedule.png) | ![Settings](docs/screenshots/settings.png) |

---

## 🪔 What is Swara Yoga?

Swara Yoga (from the classical text *Śiva Svarodaya*) is the science of the breath as it alternates between the two nostrils through the day and night. The tradition holds that the dominant nostril reflects which nāḍī is active:

- **Iḍā (left nostril)** — lunar, cooling, receptive. Favourable for calm, nourishing, inward, and auspicious "sthira" (steady) work.
- **Piṅgalā (right nostril)** — solar, warming, active. Favourable for effort, movement, transactions, and assertive "chara" (dynamic) work.

Traditionally the swara alternates roughly every ~1 hour, anchored to sunrise, and its pattern shifts across the lunar fortnights (śukla/kṛṣṇa pakṣa). Abhaya Swara models this so you can align your daily actions with the flow of your breath.

> **Abhaya Swara is a traditional-practice and educational tool, not medical or professional advice.** See the [disclaimer](#-disclaimer) below.

---

## ✨ Features

- **Live swara indicator** — shows the currently active nāḍī (Iḍā / Piṅgalā), how much time is left in the current swara, and when it ends.
- **Real astronomy** — computes local sunrise/sunset (Julian Day, ΔT, equation of time, altitude correction) rather than assuming a fixed clock.
- **Tithi tracking** — lunar day at sunrise and at the current moment, with a boundary warning when a tithi is about to change.
- **Full day/night schedule** — the complete Iḍā/Piṅgalā timetable from sunrise to next sunrise (Table A / Table B by fortnight).
- **Activity guidance** — curated activity chips for each swara (e.g. Iḍā → *rest, study, heal, prayer*; Piṅgalā → *exercise, travel, transact, decide*).
- **Location aware** — 7 built-in city presets (Hyderabad, Delhi, Mumbai, Bengaluru, Chennai, Kolkata, Pune), GPS, or manual coordinates.
- **Configurable swara interval** — default 110 min, adjustable to your own tradition/lineage.
- **Target-date planning** — check the swara schedule for any future date.
- **Auto / light / dark theme** — the theme follows your real sunrise/sunset by default.
- **100% offline & private** — a single HTML file, no server, no accounts, no tracking. Settings live only in your browser's local storage.

---

## 📥 Install

### Option 1 — Android APK
1. Go to the [**Releases**](https://github.com/<your-username>/abhaya-swara/releases/latest) page.
2. Download `abhaya-swara-vX.X.apk`.
3. On your phone, allow *Install unknown apps* for your browser/file manager, then open the APK.

> The APK is an offline wrapper around the same single HTML file — nothing is sent anywhere.

### Option 2 — Web / PWA
Open the [live web app](https://<your-username>.github.io/abhaya-swara/) and use your browser's **"Add to Home Screen"** to install it as a Progressive Web App.

### Option 3 — Run locally
No build step, no dependencies:
```bash
git clone https://github.com/<your-username>/abhaya-swara.git
cd abhaya-swara
# just open the file in a browser:
xdg-open index.html      # Linux
open index.html          # macOS
start index.html         # Windows
```
Or serve it (recommended so GPS/geolocation works):
```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

---

## 🧭 Usage

1. **Set your location** in *Settings* — pick a city, tap **Use GPS**, or enter latitude/longitude manually.
2. The **home screen** shows your active swara, the % remaining, and its end time.
3. Open **Schedule** to see the full Iḍā/Piṅgalā timetable for the day (and any target date).
4. Use the **activity chips** as a guide for aligning tasks with the active nāḍī.
5. Adjust the **swara interval** in Settings if your lineage uses a value other than 110 minutes.

---

## ⚙️ How it works

Abhaya Swara is a pure client-side app. The core engines:

| Engine | What it does |
|--------|--------------|
| **Solar geometry** | Julian Day, ΔT polynomial, equation of time, and sunrise/sunset with altitude correction for your coordinates. |
| **Tithi engine** | Sun–Moon elongation to derive the lunar day at sunrise and now. |
| **Swara alternation** | Alternates Iḍā/Piṅgalā from sunrise across a configurable interval, flipping the anchor by fortnight (Table A / B). |
| **Theme engine** | Switches light/dark automatically at your real sunrise/sunset. |

All state (location, interval, theme, target date) is stored in `localStorage`. There is **no backend and no network dependency** at runtime — fonts are the only external fetch, and the app degrades gracefully offline.

---

## 🛠️ Tech

- Single self-contained `index.html` (HTML + CSS + vanilla JS, ~900 lines).
- No frameworks, no build tooling, no npm.
- APK produced via a WebView wrapper (see [Building the APK](#-building-the-apk)).

### 📦 Building the APK
The APK is a thin WebView wrapper around `index.html`. Common approaches:
- **[Median.co](https://median.co/) / GoNative**, **Capacitor**, or **Bubblewrap (TWA)** — point the wrapper at the local `index.html` or the hosted PWA URL.

<!-- TODO: document the exact tool + steps you used so others can reproduce the build -->

---

## 🗺️ Roadmap

- [ ] Nakshatra & yoga display alongside tithi
- [ ] Panchabhuta (tattva) sub-cycle within each swara
- [ ] Notifications at swara change
- [ ] Multi-language UI (Telugu / Tamil / Hindi)
- [ ] Export day schedule as image / PDF

Have an idea? [Open a feature request](https://github.com/<your-username>/abhaya-swara/issues/new?template=feature_request.md).

---

## 🤝 Contributing

Contributions are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md). For bugs, please include your location settings and the time so the swara/tithi values can be reproduced.

---

## ⚠️ Disclaimer

Abhaya Swara is offered as a **spiritual, traditional-practice, and educational** tool grounded in classical Svarodaya Śāstra. It is **not** medical, psychological, financial, or professional advice, and makes no guarantee of outcomes. Astronomical values are computed with good-faith approximations and may differ slightly from ephemeris-grade sources. Use your own discernment.

---

## 📜 License

Released under the [MIT License](LICENSE).

> **Note on licensing:** MIT is a permissive, truly open-source license (anyone may reuse, including commercially). If you'd rather keep this a *free-for-personal-use, non-commercial* community gift, swap `LICENSE` for a non-commercial one (e.g. **PolyForm Noncommercial** or **CC BY-NC 4.0**) and say so here. Ask and this can be regenerated for you.

---

## 🙏 Acknowledgements & Credits

- Based on the classical **Śiva Svarodaya** tradition of Swara Yoga.
- Designed, built, and offered as a gift to the community by **Astrogaami** — [astrogaami.com](https://astrogaami.com).

### Contact
- 🌐 [astrogaami.com](https://astrogaami.com)

<div align="center">

*ॐ · May your breath and your actions move as one.*

</div>
