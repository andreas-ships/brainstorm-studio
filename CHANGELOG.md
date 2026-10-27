# Changelog

All notable changes to this project are documented here.
The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project uses [Semantic Versioning](https://semver.org/).

## [Unreleased]

## [1.0.0] - 2026-10-27
### Added
- Brainstorming skill with three stances: Facilitator, Creative Partner and Ideate for me.
- Library of 108 techniques in 13 categories, served on demand by `scripts/brain.py`.
- Offline technique-composer web page (`brain.py html`) to pick a stance and techniques.
- Append-only, resumable session log (`scripts/memlog.py`).
- Converge phase (affinity clustering, impact-effort, NUF, ranking, PMI, MoSCoW).
- Wrap-up artifacts: HTML keepsake and an intent document.
- `customize.toml` for favourite and extra techniques, output folder and hooks.
- Headless mode for runs without a human.

### Changed
- Restored the full MIT licence text in `LICENSE` (the modified copy only had the modifications notice).
