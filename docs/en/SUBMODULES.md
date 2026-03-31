# Git submodule conventions

This aggregate repository references upstream Wi-Fi / Bluetooth Linux drivers (or related trees) via **Git submodules**. **Each submodule’s license is defined in that repository’s root**—see the root `NOTICE` and [LICENSE_POLICY.md](LICENSE_POLICY.md).

## Recommended paths (match repo layout)

| Path | Intended content |
| ---- | ---------------- |
| `wifi-driver/` | Wi-Fi host driver source tree |
| `bluetooth-driver/` | Bluetooth host driver source tree |

When using `git submodule add`, prefer these paths to stay consistent with docs and CI.

## Drivers are not limited to “ESP32E22 only”

Submodules may point to **family-level or generic Linux driver** repositories. This repo pins **ESP32E22** support via:

- Documented **validated commit/tag** and **kernel range** in release notes;
- **Firmware ↔ driver** compatibility in `firmware/` and [FIRMWARE.md](FIRMWARE.md).

## Workflow summary

1. **First clone (with submodules)**  
   ```bash
   git clone --recurse-submodules <this repo URL>
   ```
   If you already cloned without submodules:
   ```bash
   git submodule update --init --recursive
   ```

2. **Move a submodule to a new upstream commit**  
   Inside the submodule, `git fetch` / `git checkout` the target, then commit the **submodule pointer change** in the aggregate repo.

3. **Pin versions**  
   For releases, point submodules to an explicit **tag or SHA** and record it in release notes; avoid “floating branch HEAD” for reproducible builds.

## Relationship to generic upstream driver repos

- Upstream may serve multiple chips or modules; this repo **does not fork** that logic—it uses submodule pointers plus a **support matrix** in docs.
- Bugs/features in the driver itself should be tracked in the **submodule’s repository**; this repo may keep meta-issues for alignment and release coordination.

*中文: [docs/zh/SUBMODULES.md](../zh/SUBMODULES.md)*
