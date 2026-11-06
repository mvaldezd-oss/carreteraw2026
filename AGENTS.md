# AGENTS.md

## Project overview

This repository is a single-file interactive network visualization for Mexican road connectivity. The app loads in the browser from [index.html](index.html) and uses D3.js plus Tailwind via CDN. There is no framework, package manager, or build step in this project.

## Key facts for AI coding agents

- Primary entry point: [index.html](index.html)
- Rendering library: D3.js (`d3`)
- Styling: Tailwind via CDN (`https://cdn.tailwindcss.com`)
- Runtime model: plain browser JavaScript, no module bundler
- Data input: CSV files for nodes and links, with custom upload handlers and export templates
- Modes: `map`, `force`, `radial`, `chord`, `concentric`, `arc`, and `bipartite`

## Working conventions

- Keep changes in [index.html](index.html) unless there is a clear reason to add a new asset.
- Prefer vanilla JavaScript and direct DOM manipulation over introducing a framework or build tooling.
- Preserve the existing single-page state model (`state` object) and the current SVG/D3 rendering flow.
- Maintain compatibility with the existing UI hooks and IDs such as `network-svg`, `categories-list`, and the toggle buttons.
- If you change filters, categories, or CSV parsing behavior, keep the exported/imported data contract consistent.
- Use the existing dark theme and Tailwind utility classes unless the change clearly requires custom CSS.

## Data and behavior expectations

- Nodes and links are represented as structured arrays in the app state.
- Category colors and node/link styling are centralized in constants near the top of the script.
- CSV upload logic should continue to support the current schema and remain tolerant of missing fields.
- When adding new layouts or visual modes, follow the same pattern as the existing setMode logic and keep mode switching consistent.

## Verification

Because this is a static front-end project, validation is browser-based:

1. From the project root, run a local static server:
   `python3 -m http.server 8000`
2. Open `http://localhost:8000` in a browser.
3. Check the page loads without JavaScript errors and that the main controls still work.

No automated test suite or package scripts are present in this repository.

## Agent guidance

- Prefer minimal, targeted edits over broad refactors.
- Reuse the existing structure and naming patterns instead of introducing new conventions.
- If a new feature is added, keep it compatible with the current static HTML architecture and browser-only execution model.
- Before changing visualization logic, confirm whether the behavior belongs to the D3 rendering layer, the CSV import layer, or the UI state layer.
