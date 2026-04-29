# License and distribution policy (root repository)

This document records the **intended policy** for this aggregate repository, aligned with common Espressif open-source practice and internal legal review. If a conflict arises with a formal legal decision, **the legal decision shall prevail**. Update this file and the root legal text accordingly.

## Root repository (content owned by this repo)

- **License**: **Apache License 2.0** (see root `LICENSE`).
- **Scope**: Non-submodule, non-prebuilt-binary content, e.g. documentation under `docs/`, scripts, build helpers, placeholders.
- **Espressif alignment**: Many Espressif open-source projects use Apache-2.0; using the same family here keeps compliance narratives consistent.

## Git submodules (`wifi-driver/`, `bluetooth-driver/`, `firmware/`, ...)

- **Each upstream repo's root `LICENSE` applies**; this aggregate repo **does not** re-license those trees.
- The Wi-Fi and Bluetooth host driver submodules are licensed under **GPL-2.0**, as is standard for Linux kernel modules. The root repo's Apache-2.0 and the drivers' GPL-2.0 do not conflict because they apply to separate, independent components connected only by submodule pointers (no derivative work is created).
- Driver submodules may target **chip families or generic Linux drivers**, not only a single ESP32E22 SKU; this repo defines and documents the support matrix via version references and associated documentation (see [SUBMODULES.md](SUBMODULES.md)).
- Scripts or build helpers in the root repo must **not** incorporate or derive from GPL-licensed driver source code; otherwise those files would need to be re-licensed under GPL.

### Submodule license summary

| Submodule | License (SPDX) | Copyright holder |
| --------- | -------------- | ---------------- |
| `wifi-driver/` | GPL-2.0-only | Espressif Systems (Shanghai) CO LTD |
| `bluetooth-driver/` | <!-- TODO: confirm SPDX license --> | <!-- TODO: confirm copyright holder --> |
| `firmware/` | <!-- TODO: confirm license --> | <!-- TODO: confirm copyright holder --> |

## Firmware submodule (`firmware/`)

- The `firmware/` directory is a **Git submodule** pointing to an upstream firmware repository.
- **Separate from root source licensing**: prebuilt firmware may be under different terms (dedicated EULA, closed-binary redistribution rules). The applicable license is defined in the firmware submodule's own repository root.
- **At release**, the firmware submodule must contain clear terms: `README.md`, and `LICENSE` / EULA / `NOTICE` snippets as needed.
- Before terms are final, placeholders are acceptable if marked "update before release"; **product and legal stakeholders must review and approve** prior to General Availability (GA).

## SPDX copyright header requirements

All **scripts, build helpers, and source files** owned by this repository must include an [SPDX](https://spdx.dev/) copyright header. Use the following format:

```
// SPDX-FileCopyrightText: 2026 Espressif Systems (Shanghai) CO LTD
// SPDX-License-Identifier: Apache-2.0
```

Adapt the comment style to the file type (e.g. `#` for shell/Python, `/* */` for C).

- Files in **Git submodules** follow each upstream repo's own header conventions.
- Files in **`firmware/`** (prebuilt binaries) are exempt from source headers; their terms are covered by the submodule-level `LICENSE` / EULA.

<!-- TODO: Add CI check for copyright headers (e.g. `tools/ci/check_copyright_config.yaml` similar to esp-idf). -->
<!-- TODO: Confirm the exact Espressif legal entity name and copyright year range with legal. -->

## Change log

| Date | Notes |
| ---- | ----- |
| 2026-04-14 | Root Apache-2.0; layered submodule/firmware policy; SPDX header requirements; firmware as submodule. |

*中文: [docs/zh/LICENSE_POLICY.md](../zh/LICENSE_POLICY.md)*
