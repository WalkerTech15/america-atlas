# America Atlas — Roadmap

All phases below are planned. No phase beyond the initial static foundation is complete.

## Phase 1 — Repository and application foundation

**Objectives:** Establish repository conventions, responsive semantic shell, modular file layout, and project requirements.

**Completion criteria:** Documentation and license are present; app shell serves locally; empty data files validate as JSON; no fabricated datasets or credentials are included; contribution workflow is documented.

## Phase 2 — Interactive United States map

**Objectives:** Integrate MapLibre and a reviewed basemap, load sourced state boundaries, and add accessible map controls and selection details.

**Completion criteria:** State selection works by pointer and keyboard; layer attribution is visible; data source/license is documented; map failure/WebGL fallback and mobile layout are handled.

## Phase 3 — Historical America and territorial expansion

**Objectives:** Establish sourced historical records, dated layers, Indigenous geography context, and timeline interaction.

**Completion criteria:** Every displayed historical event/geometry has provenance and dates; timeline and event list remain usable without map interaction; historical and modern layers are distinct; uncertainty is represented.

## Phase 4 — State and city profiles

**Objectives:** Add state/city datasets and profile panels for geography, population, economy, tourism, and landmarks.

**Completion criteria:** Data fields include source and time context; profiles link to map locations; missing and outdated facts are clearly handled; records pass schema validation.

## Phase 5 — Weather integration

**Objectives:** Add Open-Meteo forecasts for selected places with timestamps, units, attribution, and resilient request handling.

**Completion criteria:** Requests use validated coordinates and minimal fields; timeout, rate-limit, offline, and malformed response states are handled; no secret is shipped to the client.

## Phase 6 — Day/night synchronization and city illumination

**Objectives:** Add SunCalc-based local solar visualization synchronized with map time and selected location.

**Completion criteria:** Timezone and selected time are clear; reduced motion is respected; visualization is distinguishable from measured data; illumination styling has accessible alternatives.

## Phase 7 — Advanced visualizations and optimization

**Objectives:** Explore comparisons, historical overlays, richer map styles, and optimize data and rendering based on measurement.

**Completion criteria:** Each added visualization has sourced inputs and documented interpretation; performance budgets are measured on representative devices; large data is lazy-loaded or partitioned.

## Phase 8 — Testing, accessibility, and release

**Objectives:** Validate behavior across browsers and devices, complete accessibility review, document operations, and prepare a stable release.

**Completion criteria:** Automated checks and manual keyboard/screen-reader review pass; compatibility matrix is recorded; attribution and licenses are reviewed; known limitations and release notes are published.
