# 🔥 EmberWatch

**Understand the fire, smoke, air-quality and weather conditions around you — in about five seconds.**

EmberWatch is a mobile-first local environmental safety app. Open it and one plain-language status tells you what you need to know right now; the detail is there if you want it. Built for people living in wildfire-prone communities to open every morning during fire season.

**➡️ Live:** https://swoloszyn79.github.io/EmberWatch/

---

## What it does

- **One clear status** — 🟢 CLEAR · 🟡 WATCH · 🟠 CONCERN · 🔴 ACT NOW — with a plain sentence and an explainable **“Why you're on …”**.
- **Official alerts always win** — real BC evacuation orders/alerts are shown above everything and override EmberWatch's own assessment. Official vs. EmberWatch classifications are kept clearly separate.
- **NOW / TONIGHT / TOMORROW** — human-readable interpretation, not raw numbers, each with a confidence level.
- **Can I go outside?** — simple guidance for Kids, Exercise, Walking, Boating and Smoke-sensitive people, with “good until ~X”.
- **Air quality made simple** — leads with a plain category, then AQHI / US AQI / PM2.5, a worsening/stable/improving trend, and an hourly color timeline so you can pick *when* to go out.
- **Nearby Fire Concern** — Low / Elevated / High / Critical, driven by a fire's **size**, **stage of control**, **distance** and whether **wind** is carrying conditions toward you (bearing vs. wind direction).
- **Saved Places** — 🏠 Home, 🏕 Cabin, 👵 Parents… each showing its own live status, stored in your browser (localStorage). Plus “use my current location” (only after you allow it).
- **Map** (secondary tab) — active fires, perimeters, evacuation polygons and your location, with a clean info card per fire.
- **Forecast** tab — 7-day weather, smoke/air outlook and a dryness-driven fire-weather outlook.
- **Learn** tab — what AQHI/AQI/PM2.5 mean, how fire-weather works, and the disclaimer + official links.
- **Installable PWA** — add to your home screen; opens full-screen like a native app.

## Architecture

Single self-contained `index.html` (keeps GitHub Pages publishing to one file), internally organized into clean layers:

- **`Data`** — all API access, with an in-memory TTL cache, per-source timestamps, and null-safe normalization.
- **`Engine`** — pure decision logic: AQHI, air interpretation, fire severity, evacuation point-in-polygon, master status, Now/Tonight/Tomorrow, activities.
- **`UI`** — render components + tab router + loading/error states.
- **`Store`** — saved places & selection in localStorage.

## Data sources (all free, no API keys)

| Layer | Source |
|-------|--------|
| Active wildfires & perimeters | [BC Wildfire Service](https://wildfiresituation.nrs.gov.bc.ca/map) open ArcGIS feeds (BC) |
| Official evacuation orders & alerts | BC **Evacuation Orders and Alerts** ArcGIS feed (BC) |
| Weather / rain / heat / storms / visibility | [Open-Meteo](https://open-meteo.com) forecast API |
| Air quality & smoke (AQHI/AQI/PM2.5) | [Open-Meteo Air Quality API](https://open-meteo.com/en/docs/air-quality-api) |
| Place search | Open-Meteo Geocoding API |
| Map tiles | © OpenStreetMap © CARTO |

Everything runs client-side — no server, no keys. Weather/air/search work anywhere; live wildfire and evacuation data cover British Columbia.

## Republish an update to GitHub Pages

Replace the files in your repo (drag them into **Add file → Upload files**, or `git push`). Only `index.html` and `sw.js` usually change. Pages redeploys automatically; if you still see the old version it's cache — hard-refresh, or on the installed app close it fully and reopen (the cache version is bumped each release).

## ⚠️ Disclaimer

EmberWatch combines publicly available environmental and wildfire information to help you understand conditions around your location. It is **not** an emergency service and does not replace official evacuation notices or information from BC Wildfire Service, EmergencyInfoBC, Environment and Climate Change Canada, or local authorities. Conditions can change rapidly. In an emergency call **911**.

## License

MIT — see [LICENSE](LICENSE). Data remains subject to the terms of its providers.
