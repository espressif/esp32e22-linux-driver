# License and distribution policy (root repository)

This document records the **intended policy** for this aggregate repository, aligned with common Espressif open-source practice and internal legal review. If a conflict arises with a formal legal decision, **the legal decision shall prevail**. Update this file and the root legal text accordingly.

## Root repository (content owned by this repo)

- **License**: **Apache License 2.0** (see root `LICENSE`).
- **Scope**: Non-submodule, non-prebuilt-binary content, e.g. documentation under `docs/`, scripts, build helpers, placeholders.
- **Espressif alignment**: Many Espressif open-source projects use Apache-2.0; using the same family here keeps compliance narratives consistent.

## Git submodules (`wifi-driver/`, `bluetooth-driver/`, `firmware/`, ...)

- **Each upstream repo's root `LICENSE` applies**; this aggregate repo **does not** re-license those trees.
- The Wi-Fi and Bluetooth host driver submodules are dual-licensed under **GPL-2.0 OR BSD-3-Clause**, a common practice for Linux kernel drivers. The root repo's Apache-2.0 and the drivers' dual license do not conflict because they apply to separate, independent components connected only by submodule pointers (no derivative work is created).
- Driver submodules may target **chip families or generic Linux drivers**, not only a single ESP32E22 SKU; this repo defines and documents the support matrix via version references and associated documentation (see [SUBMODULES.md](SUBMODULES.md)).
- Scripts or build helpers in the root repo must **not** incorporate or derive from GPL-licensed driver source code; otherwise those files would need to be re-licensed under GPL.

### Submodule license summary

| Submodule | License (SPDX) | Copyright holder |
| --------- | -------------- | ---------------- |
| `wifi-driver/` | GPL-2.0 OR BSD-3-Clause | Espressif Systems (Shanghai) CO LTD |
| `bluetooth-driver/` | GPL-2.0 OR BSD-3-Clause | Espressif Systems (Shanghai) CO LTD |
| `firmware/` | Apache-2.0 | Espressif Systems (Shanghai) CO LTD |

## Firmware submodule (`firmware/`)

- The `firmware/` directory is a **Git submodule** pointing to an upstream firmware repository.
- **Separate from root source licensing**: the current firmware submodule is licensed under **Apache-2.0**, as shown in its root `LICENSE`.
- If a future firmware release changes terms (for example by adding a dedicated EULA, closed-binary redistribution rules, or `NOTICE` requirements), the applicable terms are defined by the firmware submodule's own repository root.
- **At release**, the firmware submodule must contain clear terms in `README.md`, `LICENSE`, and any required EULA / `NOTICE` files.

## SPDX copyright header requirements

All **scripts, build helpers, and source files** owned by this repository must include an [SPDX](https://spdx.dev/) copyright header. Use the following format:

```
// SPDX-FileCopyrightText: 2026 Espressif Systems (Shanghai) CO LTD
// SPDX-License-Identifier: Apache-2.0
```

Adapt the comment style to the file type (e.g. `#` for shell/Python, `/* */` for C).

- Files in **Git submodules** follow each upstream repo's own header conventions.
- Files in **`firmware/`** (prebuilt binaries) are exempt from source headers; their terms are covered by the submodule-level `LICENSE` / EULA.

## Change log

| Date | Notes |
| ---- | ----- |
| 2026-04-14 | Root Apache-2.0; layered submodule/firmware policy; SPDX header requirements; firmware as submodule. |

*中文: [docs/zh/LICENSE_POLICY.md](../zh/LICENSE_POLICY.md)*
