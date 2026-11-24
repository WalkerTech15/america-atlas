# America Atlas — Specification

**Status:** Requirements for future development. Unless explicitly marked implemented, these requirements are planned and do not describe existing functionality.

## 1. Product goals

America Atlas should provide an accessible, responsive way to explore United States geography across historical and present-day contexts. It should make sources visible, distinguish interpretation from sourced data, and remain useful when map or API services are unavailable.

## 2. Core functionality

- Present a navigable modern U.S. map and clearly distinguish its features from historical layers.
- Support a historical timeline linked to dated, sourced territorial and event layers.
- Provide state and city profiles from structured data.
- Offer optional weather and solar/daylight overlays with clear timestamps and source labels.
- Expose essential map content through non-map controls and text.

## 3. Map interaction

- Pan and zoom with pointer, touch, and keyboard-accessible controls.
- Provide a usable initial extent for the contiguous U.S.; Alaska, Hawaii, territories, and other scope decisions must be documented.
- Allow selecting states, cities, and enabled historical features; expose selection in a semantic details panel.
- Provide layer controls with labels, visible state, and keyboard operation.
- Keep map labels and boundaries legible at supported zoom levels. Respect source attribution requirements.
- Treat missing, invalid, or unavailable geometry as a recoverable data error.

## 4. Historical timeline and layers

- Support a chronological control that selects a documented date or interval and updates relevant layers.
- Every event and boundary record must have a stable identifier, date or date range, concise description, source citation, and uncertainty/context fields where appropriate.
- Represent disputed, overlapping, changing, and Indigenous geographies with explicit provenance and context; avoid presenting simplified borders as uncontested fact.
- Keep historical data separate from modern state/city datasets. Do not infer a boundary solely from a modern state outline.
- Provide event-list access equivalent to timeline and map interactions.

## 5. State and city profiles

- State records should use stable identifiers and include name, postal abbreviation, and source metadata for any additional facts.
- City records should include name, state relationship, coordinates with datum/precision documented, and source metadata.
- Optional population, demographic, economic, tourism, and landmark facts must identify the measurement year, unit, method, and source.
- Profiles must disclose absent or stale information rather than silently inventing or extrapolating values.

## 6. Weather integration

- Use Open-Meteo as the planned provider, subject to review of current API terms, attribution, and rate limits at implementation time.
- Request weather using validated coordinates and the smallest necessary field set.
- Show location, observation/forecast timestamp, timezone, units, provider attribution, and stale/unavailable state.
- Handle timeouts, HTTP failures, malformed responses, and rate limiting without breaking map interaction.
- Avoid exposing private data; no precise user location is required for the initial design.

## 7. Day/night synchronization

- Use SunCalc or a reviewed equivalent to calculate solar conditions from coordinates and time.
- Make the chosen date/time and timezone understandable; do not treat one national clock as local solar time.
- Clearly distinguish modeled solar illumination from observed weather or satellite imagery.
- Make animation optional, pauseable, and respectful of reduced-motion preferences.
- City illumination effects are a visualization, not a claim of measured light output unless backed by a cited dataset.

## 8. Data management

- Store structured, sourceable data as JSON and geometry as GeoJSON where suitable.
- Validate schemas, coordinate ranges, identifiers, required citations, and geometry before rendering.
- Keep raw/source records and generated/simplified geometry traceable; document transformations and dataset versions.
- Do not commit fabricated historical datasets, undocumented boundaries, API keys, or user-specific location data.
- Define update cadence, licensing, and cache policy per source.

## 9. Performance

- Keep the base page usable without mapping, weather, or history dependencies.
- Lazy-load map libraries, optional views, and large datasets.
- Set and measure performance budgets before adding detailed geometry; simplify geometry with documented tolerances.
- Avoid blocking the main thread with parsing or rendering large datasets; use workers or partitioning when measurement justifies them.
- Provide meaningful loading, empty, and error states.

## 10. Accessibility

- Use semantic structure, keyboard access, visible focus, sufficient contrast, and appropriately named controls.
- Do not communicate layer state or day/night solely through color.
- Provide text alternatives for map-selected data, timeline events, and weather.
- Respect reduced motion and browser zoom; support screen reader announcements without excessive updates.
- Test the interface manually with keyboard and assistive technology before release.

## 11. Browser compatibility

Target current stable versions of Chrome, Edge, Firefox, and Safari with ES module and WebGL support. Feature-detect WebGL and provide a clear fallback if unavailable. Define and test a support matrix before a public release; no browser compatibility matrix has been validated yet.

## 12. Security and privacy

- Use HTTPS for remote data and map services in deployed environments.
- Keep credentials and private configuration out of client code and Git history. Prefer public, keyless endpoints where suitable; any secret-bearing service requires a server-side design.
- Treat remote JSON and GeoJSON as untrusted input; validate shape, size, and coordinate ranges before use.
- Avoid unsafe HTML insertion, excessive requests, and collection of location data without a clear need and user control.
- Apply a restrictive Content Security Policy when deployment architecture is established.
