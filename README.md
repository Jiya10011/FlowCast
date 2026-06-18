# 🌊 FlowCast — Bengaluru Event Traffic Intelligence

> **Submitted by:** Jiya Jain  
> **Team Name:** Signal  
> **Hackathon:** Flipkart Gridlock 2.0 · Prototype Phase · Round 2  
> **Theme:** Event-Driven Congestion (Planned & Unplanned)

---

## 📌 Problem Statement

Events like political rallies, concerts, VIP movements, and religious processions cause sudden, unplanned traffic breakdowns on Bengaluru corridors. There is no proactive system to forecast congestion impact before the event starts — deployment is reactive, not predictive.

---

## 💡 Solution — FlowCast

FlowCast is an AI-powered event traffic intelligence platform that:

- Takes event metadata as input (cause, corridor, zone, hour, crowd size)
- Predicts **zone-level congestion impact** using a LightGBM scoring engine calibrated on **8,173 real Astram Bengaluru events**
- Outputs a complete **action plan** — officer count, barricade points, diversion routes
- Visualises impact on a **real interactive Bengaluru map** (Leaflet.js + real lat/lon coordinates)
- Provides **dataset insights** and **junction hotspot analysis** for traffic authorities

---

## 🗂 Project Structure

```
FlowCast/
├── index.html       ← Landing page (hero, features, how it works)
├── dashboard.html   ← Main prediction dashboard (3 views)
├── vercel.json      ← Vercel deployment config
├── package.json     ← Project metadata
└── README.md        ← This file
```

---

## 🖥️ Dashboard Views

| View | Description |
|---|---|
| **Predict Impact** | Enter event parameters → get impact score, zone analysis, action plan, forecast chart |
| **Dataset Insights** | EDA charts — events by cause, hourly distribution, corridor load, closure rates |
| **Hotspot Map** | 500 real events plotted on Bengaluru map with clustering + 15 junction hotspots |

---

## 📊 Dataset

- **Source:** Astram Bengaluru Traffic Event Data (HackerEarth)
- **Size:** 8,173 events · Nov 2023 – Apr 2024
- **Key features used:** event_cause, corridor, zone, hour, priority, vehicle_type, requires_road_closure
- **Key finding:** VIP movements have 80% road closure rate · Peak hour is 21:00 IST (810 events)

---

## 🧠 Scoring Engine

Impact score is computed using real weights derived from the dataset:

```
Score = (closure_risk × 42 + hour_load × 26 + corridor_load × 18)
        × priority_multiplier × duration_multiplier × vehicle_multiplier
```

| Factor | Source |
|---|---|
| Closure risk | Historical closure rate per cause from Astram data |
| Hour load | Events per hour normalized to peak (21:00 = 810 events) |
| Corridor load | Events per corridor normalized to busiest (Mysore Road = 743) |

**Round 1 Model Score: 90.97 R²** (LightGBM, v14 with geo_mean_d49 feature)

---

## 🚀 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5 · CSS3 · Vanilla JavaScript |
| Charts | Chart.js 4.4 |
| Maps | Leaflet.js 1.9 · CartoDB Dark/Light tiles · Marker Clustering |
| ML Model | LightGBM (scoring engine calibrated from Astram dataset) |
| Deployment | Vercel (static hosting) |
| Data | Astram Bengaluru Traffic Events (HackerEarth) |

---

## 🏃 Run Locally

```bash
# Option 1 — just open in browser
# Double-click index.html

# Option 2 — local server
npx serve . -p 3000
# Open http://localhost:3000
```

No installation, no API keys, no backend needed. Pure static site.

---

## 🌐 Deploy to Vercel

```bash
# Option A — Drag & drop folder at vercel.com (easiest)

# Option B — CLI
npm i -g vercel
vercel --prod
```

---

## 🎯 Key Features for Judges

1. **Load "VIP Movement" preset** → Run Prediction → shows 80% closure risk (real data)
2. **Dataset Insights tab** → explains the EDA behind every number
3. **Hotspot Map** → 500 real events clustered on actual Bengaluru map
4. **Light/Dark theme toggle** in the top bar
5. **Animated score ring** on every prediction result

---

## 📋 Hackathon Submission Checklist

- [x] Working prototype with live URL
- [x] Real dataset (Astram 8,173 events) used and visualised
- [x] Prediction engine calibrated from real data
- [x] Zone-level impact analysis
- [x] Actionable output (officers, barricades, diversions)
- [x] Interactive real map (Leaflet.js)
- [x] Dataset insights and EDA view
- [x] Deployed on Vercel

---

## 👩‍💻 Team

| | |
|---|---|
| **Team Name** | Signal |
| **Submitted by** | Jiya Jain |
| **Hackathon** | Flipkart Gridlock 2.0 |
| **Phase** | Prototype Phase · Round 2 |
| **Theme** | Event-Driven Congestion |

---

*FlowCast — Forecast the flow, before it breaks.*
