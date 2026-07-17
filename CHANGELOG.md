# Changelog

All notable changes to Orrery. Versions follow semantic versioning.

## [2.3.1] — Rebrand to Orrery
- **Package-only distribution**: the released `.plugin` now ships the server bundled + minified (via esbuild) and the client chart files minified — runnable, but not the authored source. Release assets and history contain no source; source lives in a separate private repository.
- **Licensing**: added a proprietary end-user license (`LICENSE`); the software is distributed as a package only, not as source — free to download and use (incl. commercial); no redistribution or derivative works; Licensor may change terms for future versions. Governing law: Texas. Added Orrery logo/iconography assets under `docs/assets/`.
- **Renamed the entire project from Surface-StockChart to Orrery** — an orrery is a mechanical model of the heavens, fitting for a terminal that builds a working model of the market. This touches the brand text, the plugin id (`surface-stockchart` → `orrery`), the MCP server name (tools are now `mcp__orrery__*`), the on-disk store directory (`~/.surface-stockchart` → `~/.orrery`), environment-variable prefix (`STOCKCHART_*` → `ORRERY_*`), and the session token header (`x-scp-token` → `x-orrery-token`). Docs, release pipeline, and issue templates all point at the `pauljbernard` org.
- **Hardened `.gitignore`** so secrets (`config.json`, `*.env`, `*.key`), all `~/.orrery` runtime data stores, build artifacts (`*.plugin`, `dist/`), test reports, and local Claude Code state (`.claude/`) can never be pushed to the remote. Fixed an inert inline-comment rule that had left `config.json` unignored.

## [2.3.0] — Distribution & legal
- **Update channel**: `check_for_updates` tool and cockpit surfacing against a public version manifest; one-command `release.sh` pipeline emitting the `.plugin`, SHA-256 checksum, and manifest for GitHub Releases + Pages.
- **Documentation website** (GitHub Pages): screenshot-rich marketing landing, full user guide, changelog, and support/issues page.
- **Legal**: comprehensive disclaimer (repo `DISCLAIMER.md`, docs legal page); in-app first-run acceptance gate with persistent footer; `get_disclaimer` / `record_disclaimer_acceptance` tools. Not investment advice; user assumes full responsibility; as-is, no warranty/liability.
- Refreshed plugin metadata and README to the full capability set; FRED key passthrough in `.mcp.json`.

## [2.2.0] — Hardening
- Full test harness across **functional, non-functional (HTTP + security), and performance** categories with a `run-all.js` orchestrator producing JSON + Markdown reports; `run_test_suite` tool.
- **Secure code review** remediations: EDGAR SSRF allowlist (re-checked on redirects), API keys never embedded at rest, workbench XSS escaping, chart-save path containment, DNS-rebinding Host guard, timing-safe token comparison, expression DoS caps, store-corruption self-heal. `SECURITY.md` added.

## [2.1.0] — Worldview & thesis probability
- Structured **worldview** across eight domains; `propose_theses` macro signal engine over **FRED** + FMP data (the system forms its own theses from data).
- Thesis **probabilities** with a full **evidence ledger** and probability history; continuous reassessment; `get_worldview_refresh_bundle`.

## [2.0.0] — Company operating models
- Driver-based per-company **operating models** calibrated from filings + consensus; instant event→driver→EPS/fair-value shocks; elasticity tables; terminal Operating Model view.

## [1.9.0] — The fully-leveraged agent
- `get_workspace_state` cockpit, agent **inbox**, generalized **playbooks**, audit **journal**, API budget governor; filing-diff intelligence, thesis review / IC-memo bundles, event triage, macro context.

## [1.8.0] — Thesis engine
- Thesis → compiled screen → model portfolio pipeline; screener **expression DSL** (where/derive); 13F crowding fields; point-in-time snapshot archive; honest technical-factor backtester.

## [1.7.0] — Institutional portfolio operations
- Broker CSV import; dividend reconciliation; Carino-linked multi-period Brinson attribution; ETF-proxy ex-ante factor model with scenario shocks; mean-variance optimizer.

## [1.6.0] — Research memory
- Persistent research notes; alert playbooks + morning brief; pro-forma what-if; event-annotated charts; screen deltas; pre-earnings prep pack.

## [1.5.0] — Surveillance & relative analysis
- Watchlists + live monitor; edge-triggered alerts; events calendar; peer comps; 13F ownership; earnings surprises; Brinson attribution.

## [1.4.0] — Professional screener & portfolio analytics
- Cross-sectional factor screener (percentile / z-score, sector-neutral, Piotroski/Altman, 12-1 momentum); GIPS-style TWR/MWR, risk suite, FIFO tax lots, exposures, rebalancing.

## [1.3.0] — Foundation
- Clean-room canvas charting engine (~125 indicators, 39 drawing tools), multi-security research terminal, FMP-backed data, localhost server with agent control channel, packaged as an installable plugin.
