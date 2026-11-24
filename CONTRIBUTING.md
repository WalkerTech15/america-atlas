# Contributing to America Atlas

Thanks for helping improve America Atlas. The repository is currently a static foundation; proposed features and data should follow the project specification and roadmap.

## How to contribute

1. Open an issue or discussion for substantial changes so scope and data needs are clear.
2. Fork the repository and create a focused branch from `main`.
3. Make a small, cohesive change and update relevant documentation.
4. Run the checks that apply and describe their results in your pull request.
5. Submit a pull request with context, screenshots for visual changes, and any data-source details.

## Development workflow

Serve the project over HTTP, for example with `python -m http.server 8000`, and open `http://localhost:8000`. The foundation has no build or dependency installation step. If a future change adds tooling, document the supported runtime and exact commands before relying on it.

## Coding conventions

- Use semantic HTML and accessible labels.
- Use vanilla JavaScript ES modules and focused modules; avoid adding a framework without an architecture proposal.
- Use descriptive CSS class names and keep styles in the relevant stylesheet.
- Prefer explicit error and empty states over silent failure.
- Keep historical and modern geography separate.
- Do not commit API keys, credentials, personal location data, generated build output, or undocumented datasets.

## Data and sourcing

Every contributed dataset or factual profile must include its source URL, publisher, license/attribution text, retrieval or version date, coverage, and any transformations. Historical material must represent uncertainty and context responsibly. Do not submit fabricated historical data or boundaries. Review source terms before redistributing content.

## Commit messages

Use a short imperative subject, optionally prefixed by a conventional type, such as `docs: clarify data attribution` or `feat: add accessible state selection`. Keep unrelated changes in separate commits.

## Pull request requirements

A pull request should explain the problem, summarize the change, link related discussion, identify data/API impacts, and list checks actually run. UI changes should include screenshots when useful. Resolve review feedback and keep the diff focused. Do not claim checks or features that were not verified.

## Documentation expectations

Update README, specification, architecture, or roadmap when behavior, data contracts, dependencies, setup, or project status changes. Clearly label planned, experimental, and implemented capabilities.
