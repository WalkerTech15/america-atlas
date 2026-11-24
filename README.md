# America Atlas

> **Explore America's Past, Present and Future.**

America Atlas is an interactive digital atlas of the United States, designed to connect historical geography with modern places, public information, weather, and the changing light of day.

> **Project status:** Foundation. The repository currently contains a small static landing page and project documentation. Map rendering, historical layers, state and city profiles, weather, and day/night visualization are planned; they are not implemented yet.

## Contents

- [Vision](#vision)
- [Features and status](#features-and-status)
- [Technology](#technology)
- [Architecture and structure](#architecture-and-structure)
- [Getting started](#getting-started)
- [Configuration and APIs](#configuration-and-apis)
- [Data sources and attribution](#data-sources-and-attribution)
- [Performance](#performance)
- [Accessibility](#accessibility)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)

## Vision

America Atlas will let visitors explore the United States through two connected perspectives:

- **Historical America:** territorial expansion, historical borders, Indigenous nations and homelands, wars and conflicts, battles, acquisitions, treaties, annexations, timelines, and geographic comparisons.
- **Modern America:** an interactive map of all 50 states, state and city profiles, population and demographic context, economy and industries, tourism and landmarks, geography, weather, and day/night conditions.

The project aims to make geographic context understandable, keep historical claims traceable to sources, and work well across screen sizes and input methods.

## Features and status

| Capability | Status |
| --- | --- |
| Semantic landing page and responsive foundation | Implemented |
| Interactive MapLibre map and state boundaries | Planned |
| Historical map layers and timeline | Planned |
| State and city profiles | Planned |
| Open-Meteo weather | Planned |
| SunCalc day/night calculations and city illumination | Planned |
| Verified historical and geographic datasets | Not yet included |

No historical or geographical dataset is bundled in this initial foundation.

## Technology

The intended stack is HTML5, CSS3, vanilla JavaScript (ES modules), JSON, and GeoJSON. MapLibre GL JS will provide interactive WebGL maps; Open-Meteo is the planned weather source; SunCalc is the planned solar-position library. These runtime integrations are **not yet installed or active**. The project currently has no package manager or build step.

## Architecture and structure

The application is organized as a static site with separate stylesheets and JavaScript modules. `app.js` initializes the current page; dedicated modules are reserved for maps, historical exploration, weather, daylight, state and city data, and data loading. See [ARCHITECTURE.md](ARCHITECTURE.md) for intended module responsibilities and [SPECIFICATION.md](SPECIFICATION.md) for requirements.

```text
america-atlas/
├── index.html
├── README.md
├── SPECIFICATION.md
├── ARCHITECTURE.md
├── ROADMAP.md
├── CONTRIBUTING.md
├── LICENSE
├── .gitignore
├── assets/{images,icons,maps}/
├── css/{main,map,history,responsive}.css
├── js/{app,map,history,weather,day-night,states,cities,data-manager}.js
└── data/{states,cities,historical-events,territorial-expansion}.json
```

## Getting started

Requirements: a modern browser and a local static HTTP server. No build tools or dependencies are required for the foundation.

```sh
git clone https://github.com/WalkerTech15/america-atlas.git
cd america-atlas
python -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000). Any static server that serves ES modules with the correct MIME types can be used. Opening `index.html` directly with `file://` may prevent module loading in some browsers.

## Configuration and APIs

There is no API key or runtime configuration in the initial foundation. Do not add secrets to source control. When weather is implemented, use Open-Meteo's documented endpoints and terms, request only the fields and locations needed, handle network and rate-limit errors, and identify the data source in the interface. Map tiles and geocoding services will require separate provider and attribution review before use.

## Data sources and attribution

No external dataset, map tile, or image is currently included. Before publishing data, document its provider, source URL, license, attribution text, date/version, geographic and temporal coverage, and any transformations. Historical boundaries and Indigenous territories require careful sourcing and context; do not imply that a boundary is definitive or timeless. Keep historical and present-day geographies distinct. See [CONTRIBUTING.md](CONTRIBUTING.md) for data contribution expectations.

## Performance

Keep the initial page dependency-free. Load mapping code and large geographic data only when needed, simplify and validate GeoJSON while preserving meaningful geometry, avoid unnecessary network requests, and measure rendering on representative mobile hardware. Cache only where provider terms and data freshness permit.

## Accessibility

Use semantic HTML, visible keyboard focus, adequate contrast, reduced-motion support, and text alternatives for map information. A map must not be the sole way to reach essential content: provide an accessible list or equivalent controls for selected features and timeline events. The foundation uses headings, landmarks, and a live status message; full application accessibility remains future work.

## Roadmap

The planned milestones and completion criteria are in [ROADMAP.md](ROADMAP.md). The detailed product and technical requirements are in [SPECIFICATION.md](SPECIFICATION.md).

## Contributing

Contributions are welcome. Read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request. Historical or geographic content contributions should include reliable sources and licensing information.

## License

The project is released under the MIT License. See [LICENSE](LICENSE). The copyright holder is identified as `WalkerTech15`, the GitHub account under which this repository was created.
