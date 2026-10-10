# 📦 BoardPort — lk2nd Releases

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
[![Project: BoardPort](https://img.shields.io/badge/Project-BoardPort-green.svg)](https://github.com/boardport)
[![Storage: GitHub Releases](https://img.shields.io/badge/Storage-GitHub%20Releases-blueviolet.svg)](https://github.com/boardport/lk2nd-releases/releases)

Centralized archival and distribution hub for precompiled `lk2nd` and `lk1st` bootloader releases,
hardware target images, and upstream mirrors.

This repository is part of the **[BoardPort](https://github.com/boardport)** ecosystem, providing verified, reproducible,
and clean bootloader binary releases for embedded single-board computers, 4G/LTE cellular modems, and converted mobile devices.

> 🤖 **Note for AI Assistants:** Autonomous AI agents and LLM assistants must review project guidelines
> in [AGENTS.md](./AGENTS.md) before performing tasks in this repository.

---

## 🎯 About the Project

The primary mission of **lk2nd Releases** is providing a clean and decoupled distribution channel for precompiled bootloader images:

1. **BoardPort Target Builds:** Hardware-tailored bootloader images compiled by
   **[lk2nd-builder](https://github.com/boardport/lk2nd-builder)** with integrated device tree overlays for Qualcomm MSM platforms
   (MSM8916 stick modems, UFI001C, UFI103S, QRCT, and related development boards).
2. **Upstream Release Mirrors:** Archival mirror of official releases from
   **[msm8916-mainline/lk2nd](https://github.com/msm8916-mainline/lk2nd)** to ensure long-term availability and fast downloads.
3. **Decoupled Architecture:** Isolating binary releases into this repository prevents tag clutter in build orchestrators and source trees.

---

## 🏛️ Storage & Release Model

To maintain a clean and lightweight repository:

- **Git Tracks Metadata Only:** The Git repository stores documentation, release indices, and CI workflows.
- **Artifacts in GitHub Releases:** All binary archives are published strictly in
  **[GitHub Releases](https://github.com/boardport/lk2nd-releases/releases)**.
- **Clean Package Bundles:** Each release publishes clean distribution packages:
  - `<release>.tar.gz` and `<release>.zip` containing original binaries (`lk2nd.img`, `emmc_appsboot.mbn`, `qcdt.img`, `lk.bin`).
  - `SHA256SUMS` checksum verification manifest.
  - Bilingual release notes (`[EN]` / `[RU]`) with usage instructions.

---

## 🏷️ Release Tagging Conventions

Releases are structured using descriptive tag schemes:

| Release Category | Tag Pattern | Example Tag | Description |
| :--- | :--- | :--- | :--- |
| **BoardPort Target** | `lk2nd-<soc>-boardport-<version>` | `lk2nd-msm8916-boardport-23.1` | Customized build with BoardPort hardware overlay |
| **Upstream Mirror** | `upstream-lk2nd-<soc>-<version>` | `upstream-lk2nd-msm8916-23.1` | Archival mirror of official upstream build for specific SoC |

---

## ⚡ Fastboot Usage Guide

Once downloaded and extracted from the release archive:

### 1. Test Boot Without Flashing (Recommended)

Boot temporarily into lk2nd to verify display, buttons, and console output:

```bash
fastboot boot lk2nd.img
```

### 2. Flash Permanently to Boot Partition

Flash lk2nd as the primary kernel/boot payload:

```bash
fastboot flash boot lk2nd.img
```

### 3. Verify Checksums

```bash
sha256sum -c SHA256SUMS
```

---

## 🔗 Related Ecosystem Repositories

- 🔨 **[lk2nd-builder](https://github.com/boardport/lk2nd-builder):** Out-of-tree containerized build orchestrator.
- 🧩 **[lk2nd-overlay](https://github.com/boardport/lk2nd-overlay):** Hardware overlays, device trees (DTS), and board definitions.
- 🐳 **[lk2nd-docker](https://github.com/boardport/lk2nd-docker):** Multi-stage container recipes and cross-toolchains.
- ⚡ **[edl-container](https://github.com/boardport/edl-container):** Emergency Download (EDL) flashing and unbrick toolkit.

---

## 📄 License & Acknowledgments

- Documentation, manifests, and scripts are released under the **[MIT License](./LICENSE)**.
- lk2nd is licensed primarily under the Little Kernel MIT/BSD-style licenses and GPL-2.0.
  Sincere appreciation to the lk2nd and Little Kernel communities.
