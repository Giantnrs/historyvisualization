# History Visualization Project

**World Important Dates Explorer** — a single-page visualization app powered by CSV historical event data, with an interactive timeline, map comparison, and Wikipedia details.

## Overview

This project renders events from `World_Important_Dates_8_Sectors.csv` through an interactive timeline, map, and event list. By default it presents global history from a China-centric perspective; you can select a country on the map to enter a China ↔ country comparison mode.

**Stack:** plain HTML + Tailwind CSS (CDN) + Leaflet + PapaParse — no build step required.

## Features

- **Interactive timeline:** scroll to zoom the viewport, drag to pan, dual vertical handles to select a time range
- **Historical period bands:** period labels plus a colored segment bar that updates with the viewport
- **Event list:** default **🇨🇳 China** / **🌍 World** sections; linked events in compare mode
- **Map visualization:** country dots; directional dashed arcs on event selection (color-coded by initiator)
- **Country compare mode:** click a country on the map to switch its historical periods and compare related events with China
- **Category filter**, **Wikipedia sidebar**, and **numeric time-range inputs**

## Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/Giantnrs/historyvisualization.git
   cd historyvisualization
   ```

2. **Start a local server** (opening the HTML file directly may fail to load the CSV due to CORS)
   ```bash
   python -m http.server 8080
   ```

3. **Open in your browser**
   ```
   http://localhost:8080
   ```

4. **Dependencies:** an internet connection is required for CDN resources (Leaflet, Tailwind, PapaParse, etc.).

## Usage

| Action | Description |
|--------|-------------|
| Scroll wheel | Zoom the year viewport on the timeline |
| Drag empty area | Pan the timeline viewport |
| Drag orange handles | Adjust the start/end of the selected time range |
| Drag blue selection | Move the entire selected range |
| Click a country dot | Enter or switch China ↔ country compare mode |
| Click an event | Focus on the map, highlight connections, and open the Wikipedia summary |

## Recent Changes (June 2026)

> Main updates to `index.html` in this round of work.

### Timeline & Periods

- Rebuilt the footer timeline: period labels sit above a colored segment bar; labels show full names (no single-letter truncation)
- Simplified world periods: merged **World Wars** and **Cold War** into a single **Modern Era** (1914–2050)
- Dimmed areas outside the selection; highlighted event spikes inside it; thicker orange dual handles + blue selection bracket
- Added **arrow hints** on both sides of the timeline (pointing inward); hidden after the first handle drag

### Event List

- Default view (no country selected) shows all **China + World** AD events in two sections, not only China-tagged events
- In compare mode, the list stays in sync with the map and shows linked events plus same-year neighbors

### Map & Connections

- Compare map: countries shown as dots with selection highlight
- Directional event lines use **dashed strokes + arrows** with a **slow grow animation** (~2.8s); colors distinguish China-initiated, foreign-initiated, and neutral flows

### Interaction & Layout

- Removed the old parallel timeline overlay; unified into a single track plus a year axis below
- Sidebar uses a China column plus an optional compare column; header shows `🇨🇳 CHINA · 🌍 WORLD`
- Only AD events from year 1 onward are shown (`AD_MIN_YEAR = 1`)

## Contributing

Contributions are welcome! Please open a pull request or issue.

## License

MIT License — see the LICENSE file for details.
