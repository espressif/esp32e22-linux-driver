# Contributing

## What fits this aggregate repository

- **Documentation**: architecture, submodule workflow, firmware–driver version matrices, typos and link fixes.
- **Metadata and scripts**: build orchestration, checksum manifests, minimal CI helpers (with maintainer agreement).
- **Structure and placeholders**: paths and conventions aligned with submodules and releases.

## Where to file issues

Wi-Fi and Bluetooth cannot always be treated as fully independent — a chip-level crash affects both stacks, and coexistence problems are often hard to attribute to one side. Use the following guidelines:

- **Chip-level issues** (e.g. system crash, firmware hang, ROM/boot failures): file in **this repository**.
- **Driver-specific issues** (clearly limited to Wi-Fi or Bluetooth host driver code): file in the corresponding **upstream repo** referenced by `wifi-driver/` or `bluetooth-driver/`.
- **Cannot tell which side is at fault** (e.g. coexistence anomalies, unclear hangs): file in **this repository**; maintainers will triage and redirect if needed.
- **On-chip firmware source** (when out of scope here): follow that firmware/SDK project's process.

## Code changes

- **Wi-Fi / Bluetooth driver code**: submit changes to the **upstream repos** referenced by `wifi-driver/` and `bluetooth-driver/`. This repo bumps submodule pointers and maintains docs, metadata, and release orchestration.

## Contributor agreement

By submitting a contribution (pull request, patch, or other form) to this repository, you agree that:

1. Your contribution is your original work, or you have the right to submit it under the applicable license.
2. You grant Espressif Systems a perpetual, worldwide, non-exclusive, royalty-free, irrevocable license to use, reproduce, modify, and distribute your contribution under the terms of the **Apache License 2.0** (or the license applicable to the specific component).
3. You understand that your contribution may be incorporated into Espressif products and redistributed under the same or compatible terms.

If a formal CLA or DCO requirement is introduced, it will be documented before
external contributions are accepted under that process.

## Process notes

1. When changing submodule pointers, explain **why**, **what was tested**, and **matching firmware version** (if any) in the MR/PR.
2. License or third-party notice changes must update [LICENSE_POLICY.md](LICENSE_POLICY.md) together with [docs/zh/LICENSE_POLICY.md](../zh/LICENSE_POLICY.md). Keep both language versions in sync.

*中文: [docs/zh/CONTRIBUTING.md](../zh/CONTRIBUTING.md)*
