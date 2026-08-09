# 🔥 EmberWatch

A live, installable dashboard that shows the **wildfire, smoke, air-quality, lightning/storm, rain and heat risks** for any location — for **today and the next 7 days**, all on one screen.

Built to be dead-simple: open it, tap the map (or search / use your GPS), and instantly understand what the day's weather and environmental conditions mean for you. Installs to your phone's home screen like a native app.

**➡️ Live demo:** _add your GitHub Pages URL here once published_

> _Tip: once it's live, take a screenshot, save it as `screenshot.png` here, and add `![EmberWatch](screenshot.png)` to this file._

---

## What it shows

- **📍 Pick your location** — tap anywhere on the map, search a place, use your GPS, or jump to a community.
- **🔥 Wildfire** — active fires near you from the BC Wildfire Service. Risk is driven by each fire's **size** and **stage of control** (Out of Control → Being Held → Under Control), not just distance, so a small contained fire nearby stays low while a large out-of-control one raises the rating even from farther away. Perimeters are drawn on the map.
- **🌫️ Smoke & Air Quality** — current and next-24h US AQI + PM2.5, the **Canadian AQHI** (Environment Canada's health index), visibility distance, and smart **smoke-drift** context (whether the nearest fire is upwind of you).
- **🏃 "Can I Go Outside?"** — plain-language guidance for outdoor exercise, kids playing outside, going on the lake, and short outings — blending air quality, heat, storms/lightning, wind and UV.
- **⛈️ Lightning & Storms** — thunderstorm potential over the next 24h (instability/CAPE + storm codes), with timing.
- **🌡️ Rain, Heat & Cooling** — precipitation, highs/lows, feels-like, heat-warning range and UV.
- **📅 7-Day Outlook** — weather, air quality and storm risk per day.
- **🌫️ Smoke Outlook** — smoke level, PM2.5, AQI and visibility for the next several days.
- **🔥 Fire-Weather Outlook** — a per-day fire-danger index driven by **dryness** (low humidity + days since rain), heat and wind, with a dryness tag for each day.
- **📖 Understanding these conditions** — a built-in reference explaining AQHI vs AQI, fire-weather & dryness, lightning, visibility, heat and smoke-protection tips.
- **⚠️ Overall risk banner** — one glance tells you the day's top concern.

## Install it on your phone (PWA)

EmberWatch is a Progressive Web App — once it's hosted (e.g. GitHub Pages), it installs to your home screen and opens full-screen like a native app, no App Store needed.

- **iPhone / iPad (Safari):** open the site → tap **Share** → **Add to Home Screen**.
- **Android (Chrome):** open the site → tap the **⬇ Install app** button (or menu → **Install app / Add to Home screen**).

## Data sources (all free, no API keys)

| Layer | Source |
|-------|--------|
| Active wildfires & perimeters | [BC Wildfire Service](https://wildfiresituation.nrs.gov.bc.ca/map) open ArcGIS feed (British Columbia) |
| Weather / rain / heat / storms | [Open-Meteo](https://open-meteo.com) forecast API (Environment Canada models) |
| Air quality & smoke (PM2.5 / AQI) | [Open-Meteo Air Quality API](https://open-meteo.com/en/docs/air-quality-api) (CAMS) |
| Place search / geocoding | Open-Meteo Geocoding API |
| Map tiles | © OpenStreetMap © CARTO |

Everything runs **client-side in the browser** — no server, no API key — which is why it hosts for free on GitHub Pages. (Weather, air quality and search work worldwide; live wildfire data covers British Columbia.)

## Project structure

```
emberwatch/
├── index.html            ← the whole app (HTML + CSS + JS)
├── manifest.webmanifest  ← PWA metadata (name, icons, theme)
├── sw.js                 ← service worker (installable + offline shell)
├── icons/                ← app icons (192, 512, maskable, apple-touch, favicon)
├── LICENSE
└── README.md
```

## Run it locally

The PWA features (install / offline) need to be served over http(s), not opened as a `file://`:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

(You can also just double-click `index.html` to see the dashboard — install/offline just won't be active.)

## Publish to GitHub Pages

1. Create a new repository on GitHub (e.g. `emberwatch`).
2. Push these files:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: EmberWatch"
   git branch -M main
   git remote add origin https://github.com/<your-username>/emberwatch.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, pick `main` / `/ (root)`, Save.
4. Your app goes live at `https://<your-username>.github.io/emberwatch/` within a minute or two — and is installable from there.

## ⚠️ Disclaimer

EmberWatch is for **general awareness only**. It is **not** an official emergency source. Risk levels are automated estimates and can be wrong or delayed. For evacuation orders and alerts, always check [EmergencyInfoBC](https://www.emergencyinfobc.gov.bc.ca/), your local government, and the [BC Wildfire Service](https://wildfiresituation.nrs.gov.bc.ca/map). In an emergency call **911**. Report a wildfire: **1-800-663-5555** or **\*5555** from a cell.

## License

MIT — see [LICENSE](LICENSE). Data remains subject to the terms of its respective providers (BC Wildfire Service / Province of BC, Open-Meteo, OpenStreetMap, CARTO).
