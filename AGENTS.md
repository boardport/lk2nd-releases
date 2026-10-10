# Project Passport and Operational Guidelines for AI Agents: lk2nd Releases

> **Project:** BoardPort — lk2nd Releases  
> **Organization:** [BoardPort](https://github.com/boardport) | **Repository:** `boardport/lk2nd-releases`  
> **Mission:** Centralized distribution and archival hub for lk2nd/lk1st bootloader releases  
> **Target Ecosystem:** Embedded hardware, 4G/LTE modems, and mobile platforms | **License:** [MIT](./LICENSE)  

---

## 1. AI Context Organization

The root [`AGENTS.md`](./AGENTS.md) and [`AGENTS_RU.md`](./AGENTS_RU.md) files serve as the authoritative baseline guidelines for all AI assistants:

- **Specialized Directories (`.(gemini|claude|cursor|continue|qwen|etc)/`):** Individual context for specific AI assistants
  (prompts, skills, reports, session dumps). These directories are isolated and excluded from git indexing (`.gitignore`).
- **`.aiignore` File:** Defines resources strictly excluded from background indexing and scanning
  (firmware binaries, flash dumps, bootloader images, archives).

---

## 2. Architecture & Release Storage Model

- **Metadata Only in Git:** The Git repository stores documentation, release indices, manifests, and automation scripts.
- **Binary Assets in GitHub Releases:** All binary archives (`.tar.gz`, `.zip`) and checksums (`SHA256SUMS`) are hosted strictly
  in **[GitHub Releases](https://github.com/boardport/lk2nd-releases/releases)**.
- **Clean Git Tracking:** Binary firmware (`*.bin`, `*.img`, `*.mbn`), raw dumps (`dumps/`), temporary staging (`tmp/`), and download caches
  must never be committed to Git.
- **Decoupled Builder Integration:** Binaries are compiled and published from `boardport/lk2nd-builder` into this repository.

---

## 3. Markdown Documentation Standards

- **Formatting Rules:** Syntax and formatting constraints are governed by `.editorconfig` and `.markdownlint-cli2.jsonc`.
- **Mandatory Lint Command:** Run `npx markdownlint-cli2 "**/*.md"` (must return `0 issues in 0 files` before completing work).
- **Mirrored Bilingualism:** All public user documentation is maintained in parallel (`*.md` in English and `*_RU.md` in Russian).

---

## 4. Git and GitHub Standards (`.github/`)

- Organizational policies, issue templates, PR descriptions, and CI workflows reside in [`.github/`](./.github/).
- Commit message standards follow the Conventional Commits specification (e.g., `feat:`, `fix:`, `docs:`, `chore:`).
- **Git Commits Rule:** Creating Git commits is allowed **only upon direct user confirmation**.
