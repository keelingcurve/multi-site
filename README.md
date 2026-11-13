# Keeling Curve Foundation data tools: multi-site viewer

**Live:** https://keelingcurve.github.io/multi-site/

This page puts ten data tools side by side so you can see them together and move between them without juggling browser tabs. Each tool is its own website, built and maintained in its own repository. The viewer only frames them: it holds no data of its own and needs no server.

## How to use it

On a desktop screen the tools appear in a grid of two columns and five rows. You can work inside any panel directly. Scroll the page to reach the lower rows.

- **Expand** fills the window with one tool. A row of buttons across the top lets you jump to any other tool, and **Show all ten** (or the Esc key) returns you to the grid.
- **Open in new tab** opens the tool on its own site. Use this when a tool needs the full window or when you want to share its address.
- Each expanded tool has its own link, for example `https://keelingcurve.github.io/multi-site/#pull-the-plug`, so you can bookmark or send a specific tool.

On a phone, the panels stack in a single column: column 1 from top to bottom, then column 2.

## The ten tools

| Position | Tool | What it does | Source repository | Site |
|---|---|---|---|---|
| Column 1, row 1 | KCF hero mockup | A design mockup of a Keeling Curve Foundation landing page, with the Mauna Loa CO₂ record and live ocean maps | [sdiggs/kcf](https://github.com/sdiggs/kcf) | [sdiggs.github.io/kcf](https://sdiggs.github.io/kcf/) |
| Column 1, row 2 | Climate & Ocean Data (KCF LTO) | The Keeling Curve Foundation's Long-Term Observations inventory: 287 climate and ocean datasets (v2.2) | [sdiggs/kcf-lto-data](https://github.com/sdiggs/kcf-lto-data) | [sdiggs.github.io/kcf-lto-data](https://sdiggs.github.io/kcf-lto-data/) |
| Column 1, row 3 | Pull the Plug | You cut funding to one link in a U.S. environmental observing chain and watch what stops working downstream | [keelingcurve/pull-the-plug](https://github.com/keelingcurve/pull-the-plug) | [keelingcurve.github.io/pull-the-plug](https://keelingcurve.github.io/pull-the-plug/) |
| Column 1, row 4 | Climate Data Stewardship Landscape | A network map of about 100 organizations responding to the 2025 to 2026 U.S. climate data crisis (v2.0) | [sdiggs/climate_data_players](https://github.com/sdiggs/climate_data_players) | [sdiggs.github.io/climate_data_players](https://sdiggs.github.io/climate_data_players/) |
| Column 1, row 5 | LTER Network | The NSF Long Term Ecological Research network, as a reference table and map | [keelingcurve/lter](https://github.com/keelingcurve/lter) | [keelingcurve.github.io/lter](https://keelingcurve.github.io/lter/) |
| Column 2, row 1 | Argo Knowledge Graph | A knowledge graph of how the OneArgo float program's data is used | [sdiggs/argo_kg_explorer](https://github.com/sdiggs/argo_kg_explorer) | [sdiggs.github.io/argo_kg_explorer](https://sdiggs.github.io/argo_kg_explorer/) |
| Column 2, row 2 | IOOS Plankton Knowledge Graph | A knowledge graph built from the IOOS Plankton Data and User Needs Workshop (April 2026) | [sdiggs/ioos-plankton-kg](https://github.com/sdiggs/ioos-plankton-kg) | [sdiggs.github.io/ioos-plankton-kg](https://sdiggs.github.io/ioos-plankton-kg/) |
| Column 2, row 3 | R* calculator | Scores how likely we are to lose a dataset, with a recommended triage action (R* Composite Priority Index) | [sdiggs/rstar-calculator](https://github.com/sdiggs/rstar-calculator) | [sdiggs.github.io/rstar-calculator](https://sdiggs.github.io/rstar-calculator/) |
| Column 2, row 4 | UReDI calculator | Scores how much a dataset is worth and how hard it would be to recover (Tom Karl's UReDI v3 framework: Urgency, Recoverability Difficulty, Importance) | [sdiggs/uredi-calculator](https://github.com/sdiggs/uredi-calculator) | [sdiggs.github.io/uredi-calculator](https://sdiggs.github.io/uredi-calculator/) |
| Column 2, row 5 | Parsons Matrix | A 3D map of research data stewardship initiatives by discipline, stakeholder, and function | [nyce-data/parsons-matrix](https://github.com/nyce-data/parsons-matrix) | [nyce-data.github.io/parsons-matrix](https://nyce-data.github.io/parsons-matrix/) |

Three of these tools work together as an ensemble for climate data preservation. UReDI tells you how much a dataset is worth and how hard it would be to recover, R* tells you how likely we are to lose it, and the KCF LTO inventory tells you which measurement series must keep running.

The tools live under three GitHub accounts: `keelingcurve` (the Keeling Curve Foundation), `sdiggs` (Stephen C. Diggs), and `nyce-data` (New York Climate Exchange). The Parsons Matrix is an NYCE project and is labeled that way in the viewer.

## Adding, removing, or moving a tool

Everything about the ten tools sits in one list near the bottom of `index.html`, called `SITES`. Each entry has:

- `id`: a short name used in the link (`#rstar`). Use letters, digits, and hyphens only.
- `col` and `row`: the tool's position in the desktop grid.
- `title`: the name shown on the panel.
- `url`: the tool's address.
- `note` (optional): a short tag shown next to the title, such as the owning organization.

To change the grid, edit that list and keep the `col` and `row` values unique. If you add an eleventh tool, also change `repeat(5, ...)` in the `.grid` style to the new number of rows. The order of the list sets the stacking order on phones.

## How it is built and deployed

The viewer is one static HTML file with no build step, no framework, and no backend. GitHub Pages serves it from the `main` branch of this repository. The `.nojekyll` file tells GitHub Pages to serve the files as they are.

Each panel is an `iframe` pointing at the tool's own site. Panels below the fold load only when you scroll to them, so the page doesn't fetch all ten tools at once. A tool that changes on its own site changes here automatically; nothing in this repository needs updating.

## Known caveats

- **Each tool is maintained separately.** If a tool breaks or moves, fix it in its own repository, or update its `url` here.
- **The KCF hero mockup is a design mockup.** Several of its figures (the CO₂ value, SST anomaly, chlorophyll reading, and sea-ice extent) appear as current conditions. Until they are wired to a live source or labeled as illustrative, treat them as placeholders. Its live map embeds and the Scripps CO₂ chart are real.
- **The KCF LTO page has a generic browser title** ("Bundled Page"). The viewer labels it correctly, but the tool's own tab and link previews will show the generic name until the title is fixed in `sdiggs/kcf-lto-data`.
- **Two "climate data players" repositories exist.** This viewer uses `sdiggs/climate_data_players` (underscore), which holds v2.0. The older `sdiggs/climate-data-players` (hyphen) is retained but not shown here.
- **Small panels.** At two columns by five rows, each panel is small on a laptop screen. Use **Expand** for real work in any one tool.

## Predecessor

This viewer replaces the six-panel [sdiggs/6sites](https://github.com/sdiggs/6sites) viewer, which remains online at its original address. The panel and focus pattern here follows that design.

## Change log

| Date | Change |
|---|---|
| 2026-11-12 | First release: ten tools in a 2 × 5 grid, with expand mode, per-tool links, and a single-column phone layout. |

## Credits

Built by Stephen C. Diggs, Chief Data Officer, Keeling Curve Foundation ([sdiggs.github.io](https://sdiggs.github.io)). Each tool is credited on its own site.
