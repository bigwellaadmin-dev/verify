# Changelog

All notable changes to this project are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Framework content changes are noted distinctly from tool / skill / repo-infrastructure changes. The framework text in `guide/` is canonical. Any change to it is treated as a breaking change to the citable artefact and triggers at least a minor version bump.

## [Unreleased]

Repository security and supply-chain hardening. No framework, tool, or skill content changes — the v1.0.0 citable artefact is untouched.

### Added

- `.github/dependabot.yml` — weekly GitHub Actions version watch
- `.github/workflows/scorecard.yml` — OpenSSF Scorecard analysis with SARIF upload to the Security tab
- `.github/workflows/codeql.yml` — CodeQL static analysis of the tool's inline JavaScript
- OpenSSF Scorecard badge in `README.md`
- Explicit response-time SLA in `SECURITY.md` (7 / 30 / 90 days)
- Supported-versions matrix in `SECURITY.md`

### Changed

- `SECURITY.md` opening line updated — fonts are now self-hosted, so the "no third-party scripts beyond Google Fonts" caveat no longer applies

## [1.0.0] - 2026-05-22

Initial public release.

### Added

- **Teacher Guide** (Parts 1 to 4 plus Appendix) converted from source `.docx` files to markdown:
  - `guide/00-overview.md`
  - `guide/01-the-problem.md` (Part 1)
  - `guide/02-the-framework.md` (Part 2)
  - `guide/03-in-practice.md` (Part 3)
  - `guide/04-assessment.md` (Part 4)
  - `guide/appendix-research.md` (Appendix)
- **Standalone rubrics**: `rubrics/verify-rubric-a-to-e.md`, `rubrics/verify-rubric-four-level.md`
- **Interactive companion tool**: `tool/index.html`, a single-file HTML walk-through for use alongside the learner's AI work
- **Claude skill file**: `skill/VERIFY_skill.md` with three application modes, pedagogical breaks, and the feedback-language matrix
- **Build specifications**: `docs/FRAMEWORK.md`, `docs/TOOL_SPEC.md`, `docs/SKILL_SPEC.md`
- **Repo infrastructure**: `README.md`, `LICENSE` (CC BY 4.0), `CITATION.cff`, `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`, `.gitignore`, `.github/` issue and PR templates
- **Screenshot**: `assets/screenshot.png`

---

[1.0.0]: https://github.com/bigwellaadmin-dev/verify/releases/tag/v1.0.0
