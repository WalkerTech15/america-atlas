# America Atlas — Architecture

**Status:** Intended architecture. The current implementation is a static landing page with a small ES module initializer; the services and features below are planned.

## Application structure

The project uses a static HTML entry point, small CSS files separated by concern, and vanilla JavaScript ES modules. Avoid a framework or build system until a measured need justifies one. The browser loads `js/app.js`; feature modules should initialize only when their UI is present and needed.

## JavaScript modules

- `app.js`: application startup, shared UI state, and feature initialization.
- `map.js`: MapLibre lifecycle, map controls, layer visibility, feature selection, and map error handling.
- `history.js`: timeline controls and historical layer selection.
- `states.js`, `cities.js`: accessors and profile rendering for modern geography.
- `weather.js`: Open-Meteo request construction, response normalization, caching, and user-facing error states.
- `day-night.js`: solar calculations using SunCalc and synchronization with selected map time/location.
- `data-manager.js`: schema-aware data loading, validation, provenance, and shared cache policy.

Keep modules focused and expose small functions rather than relying on shared mutable globals. Historical and modern geographic data remain separate.

## Map rendering

MapLibre GL JS is the planned renderer. Use a style and tile provider whose terms and attribution are understood. Initialize the map lazily, handle unavailable WebGL, and keep controls operable without pointer input. Use vector tiles or generalized GeoJSON for broad views; load detailed data only at appropriate zoom. Every map source must have provenance and license metadata.

## Geographic data management

Store small structured records in JSON and suitable vector geometry in GeoJSON. Distinguish source data from transformed data. Validate features and properties before rendering, assign stable IDs, document simplification and coordinate reference assumptions, and partition datasets to limit initial transfer and parse costs. Never derive historical claims from modern boundaries without an explicitly documented source and method.

## Weather API integration

`weather.js` will request only needed fields from Open-Meteo using validated coordinates. Normalize provider responses before they enter the UI. Add bounded caching and request deduplication based on measured needs and provider terms; surface timestamps, units, attribution, and failures. Do not place secret credentials in browser code.

## Historical data management

Historical events and territorial periods should be source-cited records independent from the present-day state layer. Each record should carry dates, citation/provenance, context, and uncertainty where relevant. A timeline selection will choose the applicable data without overwriting modern geography. Indigenous territories and contested claims require careful descriptive context and source review.

## Day/night calculations

Use SunCalc with an explicit coordinate and timestamp. Convert the result into a display state such as day, twilight, or night, with timezone and timestamp available to users. Keep this modeled overlay separate from weather and any measured nighttime-lights dataset. Animation should be optional and respect reduced-motion preferences.

## Performance and resilience

- Keep the initial HTML/CSS/JS small and usable before map code loads.
- Lazy-load large dependencies and datasets.
- Measure transfer size, parse time, map frame time, and memory on representative devices.
- Use data simplification, partitioning, and caching only with documented provenance and freshness behavior.
- Make network/API failure local to the affected feature; preserve the rest of the interface.

## Future extensibility

Potential additions include search/geocoding, offline snapshots, richer data validation, and a typed build pipeline. Evaluate each against real complexity, accessibility, and performance needs. TypeScript or a bundler may be introduced later without changing the public data contracts unnecessarily.
