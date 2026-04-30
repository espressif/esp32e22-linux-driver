# esp32e22-linux-driver

**Current release: v0.5**

Linux-side **aggregate repository** for **ESP32E22**: Wi-Fi / Bluetooth host drivers and prebuilt firmware (all via Git submodules), plus documentation for version pinning and release orchestration.

## Chip Capabilities (Summary)

- **Wi-Fi 6E**, **Bluetooth 5.4**
- The chip runs a **unified firmware**; the host may expose separate Wi-Fi and Bluetooth driver stacks, coordinated by the chip-side firmware and ROM download/arbitration mechanism (see architecture docs for details).

## Feature Status (v0.5)

| Feature | Interface | Status |
| ------- | --------- | ------ |
| Wi-Fi (STA) | PCIe | Supported |
| Wi-Fi (STA) | SDIO | Not yet |
| Wi-Fi (AP) | PCIe | Not yet |
| Wi-Fi (AP) | SDIO | Not yet |
| Bluetooth (BR/EDR) | USB | Supported |
| Bluetooth (BLE) | USB | Supported |
| Bluetooth | UART | Not yet |
| Firmware download | PCIe | Supported |
| Firmware download | USB | Supported |
| Secure Download | -- | Not yet |
| Wi-Fi/BT coexistence | -- | Not yet |
| Suspend/Resume (sleep) | -- | Not yet |

Features marked "Not yet" are planned for future releases.

## Repository Layout

| Component | Description |
| --------- | ----------- |
| `wifi-driver/` | Wi-Fi host driver submodule ([esp-wifi-drv](https://github.com/espressif/esp-wifi-drv)) |
| `bluetooth-driver/` | Bluetooth host driver submodule ([esp-btdm-linux-drv](https://github.com/espressif/esp-btdm-linux-drv)) |
| `firmware/` | Prebuilt firmware submodule ([esp32e22-fw](https://github.com/espressif/esp32e22-fw)) |
| `docs/` | Documentation in Chinese and English: architecture, submodule conventions, firmware–driver version contracts, etc. |

## Documentation

- **Hub**: [docs/README.md](docs/README.md)
- **中文**: [docs/zh/README.md](docs/zh/README.md) — 架构、子模块、固件、许可证策略、贡献
- **English**: [docs/en/README.md](docs/en/README.md) — architecture, submodules, firmware, license policy, contributing

## Build & Installation

This aggregate repository does not build driver modules directly. Use the
submodule documentation for component-specific build and integration steps:

- Wi-Fi driver: [wifi-driver/README.md](https://github.com/espressif/esp-wifi-drv#readme)
- Bluetooth driver: [bluetooth-driver/README.md](https://github.com/espressif/esp-btdm-linux-drv#readme)
- Firmware packaging and versioning: [firmware/README.md](https://github.com/espressif/esp32e22-fw#readme)

## License (Layered Overview)

1. **Root `LICENSE` (Apache-2.0)**
   Covers documentation, scripts, build helpers, and metadata **owned by this repository** that are not part of any submodule. Consistent with the license family used by many Espressif open-source projects; see [LICENSE_POLICY (English)](docs/en/LICENSE_POLICY.md) / [LICENSE_POLICY（中文）](docs/zh/LICENSE_POLICY.md) for details.

2. **Git Submodules**
   Each sub-repo is governed by **its own root license**; do not assume a single license applies to the entire tree.

3. **Prebuilt Firmware (`firmware/`)**
   Referenced as a Git submodule; may be licensed **differently** from the root repository source code. Refer to the `README`, `LICENSE`, or EULA in the firmware submodule's own repository.

---
