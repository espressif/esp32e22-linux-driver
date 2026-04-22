# Firmware binaries

This page describes the **expected layout, naming, and version contract** for prebuilt firmware. The `firmware/` directory is a **Git submodule** pointing to an upstream firmware repository. Shipped files will follow official releases; until such releases are available, treat this document as a target specification.

## Layout and naming (TODO: finalize at release)

| Item | Notes |
| ---- | ----- |
| Directory | `firmware/` submodule in this repo; see that submodule's `README.md` |
| Naming | Should include chip variant, interface form factor, version (semver or build ID); finalize rules at release and update this doc |
| Checksums | Prefer **SHA-256** (or similar) manifests on release pages or CI artifacts (future iteration) |

## Firmware–driver compatibility requirements

- Drivers and firmware have **ABI/protocol** dependencies; **mismatched pairs** may fail enumeration, firmware load, or at runtime.
- **Early versions**: each driver release targets **exactly one firmware version** (1:1 pairing). Multi-firmware-version support within a single driver is not planned for the initial releases.
- Each release must include a compatibility table mapping **driver version (or submodule SHA) ↔ required firmware version ↔ tested kernel range**.

## Where to get binaries (TODO: add URLs when available)

- Official release pages, internal artifact stores, CI artifacts, etc.—update this file and the root `README.md` when URLs and access models are known.

## Legal and redistribution

- Binary terms may differ from the root repo **Apache-2.0**; follow the `LICENSE`, any EULA, and `README.md` in the firmware submodule's own repository. See [LICENSE_POLICY.md](LICENSE_POLICY.md).

*中文: [docs/zh/FIRMWARE.md](../zh/FIRMWARE.md)*
