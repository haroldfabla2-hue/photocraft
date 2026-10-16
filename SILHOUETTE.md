# Photocraft — Silhouette Fork

This is the Silhouette Agency OS fork of [storytold/photocraft](https://github.com/storytold/photocraft) (Apache-2.0/MIT — see LICENSE-APACHE, LICENSE-MIT, NOTICE and ATTRIBUTION.md). It is the engine of Silhouette's Visual Cortex: local, zero-cost, CPU-only composition and edition of visual assets, driven programmatically by the Silhouette agent.

## Branches

- `main` — exact mirror of `upstream/main`. Never committed to directly; updated only by sync from upstream.
- `silhouette/main` — integration branch: upstream + Silhouette adaptations. Releases are cut from here as `silhouette-v<upstream-version>.<n>`.
- `silhouette/*` — feature branches for adaptations, always via PR with green CI.

## Sync strategy

Monthly (or on relevant upstream fixes): merge `upstream/main` into `silhouette/main`, full test suite, smoke test on the Silhouette server (headless 1080x1080 gradient+text → PNG), then bump the pinned version in `scripts/install-photocraft.sh` of the Silhouette repo. Deploys always use a pinned release binary — never a moving branch.

## Adaptation roadmap (driven by what the Visual Cortex needs)

- **P0** Machine-readable param schemas per command (stronger validation for arbitrary `visual_execute` calls).
- **P0** Whatever real agent usage surfaces.
- **P1** PSD write fidelity (~73-87% per upstream's oracle) and the 12 missing UI tools from upstream's gaps doc.
- **P2** Generative hooks (`generate.*` commands) for the MiniMax integration.

Upstream's CI (`.github/workflows/ci.yml`, `release.yml`) runs free on this public fork; adaptations must keep it green. Contributions flow back upstream when they are generally useful.

Full design rationale: `docs/visual-cortex-fork.md` in the [Silhouette-Agency-OS-OpenSource](https://github.com/haroldfabla2-hue/Silhouette-Agency-OS-OpenSource) repo.
