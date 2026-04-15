# esp32e22-linux-driver

Linux-side **aggregate repository** for **ESP32E22**: Wi-Fi / Bluetooth host drivers (via Git submodules), prebuilt firmware, and documentation for version pinning and release orchestration.

## Chip Capabilities (Summary)

- **Wi-Fi 6E**, **Bluetooth 5.4**
- The chip runs a **unified firmware**; the host may expose separate Wi-Fi and Bluetooth driver stacks, coordinated by the chip-side firmware and ROM download/arbitration mechanism (see architecture docs for details).

## Repository Layout

| Component | Description |
| --------- | ----------- |
| `wifi-driver/` | Wi-Fi host driver submodule (TODO: add submodule when upstream repo is ready) |
| `bluetooth-driver/` | Bluetooth host driver submodule (TODO: add submodule when upstream repo is ready) |
| `firmware/` | Prebuilt firmware binaries (TODO: add binaries and finalize distribution terms at release) |
| `docs/` | Documentation in Chinese and English: architecture, submodule conventions, firmware–driver version contracts, etc. |

## Documentation

- **Hub**: [docs/README.md](docs/README.md)
- **中文**: [docs/zh/README.md](docs/zh/README.md) — 架构、子模块、固件、许可证策略、贡献
- **English**: [docs/en/README.md](docs/en/README.md) — architecture, submodules, firmware, license policy, contributing

## Build & Installation

Detailed build and installation steps for drivers and firmware will be added once submodules and release artifacts are in place. For now the repository focuses on documentation and directory structure.

## License (Layered Overview)

1. **Root `LICENSE` (Apache-2.0)**
   Covers documentation, scripts, build helpers, and metadata **owned by this repository** that are not part of any submodule. Consistent with the license family used by many Espressif open-source projects; see [LICENSE_POLICY (English)](docs/en/LICENSE_POLICY.md) / [LICENSE_POLICY（中文）](docs/zh/LICENSE_POLICY.md) for details.

2. **Git Submodules**
   Each sub-repo is governed by **its own root license**; do not assume a single license applies to the entire tree.

3. **Prebuilt Firmware (`firmware/`)**
   May be licensed **differently** from the root repository source code; refer to the `README`, `LICENSE`, or EULA inside `firmware/`.

4. **Third-Party Notices**
   See the root `NOTICE` and `THIRD_PARTY_NOTICES` files; these will be updated as submodules and firmware releases are added.

---
