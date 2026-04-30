# Firmware binaries

This page describes the **current layout, naming, and version contract** for
prebuilt firmware. The `firmware/` directory is a **Git submodule** pointing to
[`esp32e22-fw`](https://github.com/espressif/esp32e22-fw#readme), the upstream firmware delivery
repository.

## Layout and naming

| Item | Notes |
| ---- | ----- |
| Directory | `firmware/` submodule in this repo; see that submodule's `README.md` |
| Repository firmware artifact | `esp32e22-fw.bin` inside the firmware submodule; this is the current repository-side name used to keep a single firmware binary in the firmware repository |
| Linux runtime install path | Current Linux drivers request `/lib/firmware/espressif/esp32e22.bin`; packaging or installation must map the repository artifact to that runtime filename |
| Manifest | `manifest.json` records firmware version, build date, size, SHA-256, source commit, feature flags, and Secure Download support |
| Versioning | `firmware/VERSIONING.md` defines the versioning rules, release workflow, and manifest schema |
| Checksums | The SHA-256 checksum is recorded in `manifest.json` |

The repository artifact name and the Linux runtime filename are intentionally
separate. The firmware submodule keeps one canonical binary for versioning and
release tracking, while each host-side packaging flow may install or rename that
binary to the filename expected by the corresponding driver. For the current
Linux drivers, that installed filename is `espressif/esp32e22.bin`.

## Firmware–driver compatibility requirements

- Drivers and firmware have **ABI/protocol** dependencies; **mismatched pairs** may fail enumeration, firmware load, or at runtime.
- **Early versions**: each driver release targets **exactly one firmware version** (1:1 pairing). Multi-firmware-version support within a single driver is not planned for the initial releases.
- Each release must include a compatibility table mapping **driver version (or submodule SHA) ↔ required firmware version ↔ tested kernel range**.

## Where to get binaries

- Clone this aggregate repository with submodules, or update submodules after
  cloning:
  ```bash
  git submodule update --init --recursive
  ```
- Official release pages or internal artifact stores may also provide packaged
  binaries. When such distribution channels are used, they must stay aligned
  with the `firmware/` submodule commit pinned by this repository.

## Legal and redistribution

- Binary terms may differ from the root repo **Apache-2.0**; follow the `LICENSE`, any EULA, and `README.md` in the firmware submodule's own repository. See [LICENSE_POLICY.md](LICENSE_POLICY.md).

*中文: [docs/zh/FIRMWARE.md](../zh/FIRMWARE.md)*
