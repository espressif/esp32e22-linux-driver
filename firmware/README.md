# Prebuilt Firmware (TODO: add submodule)

This directory is reserved for the **prebuilt firmware** Git submodule ([esp32e22-fw](../esp32e22-fw)), containing firmware binaries and release notes related to **ESP32E22** connectivity.

To add the submodule (run from the repository root):

```bash
git rm -rf firmware/
git submodule add ../esp32e22-fw firmware
```

A relative URL (`../esp32e22-fw`) is used so that the submodule resolves correctly on both GitLab and GitHub mirrors.

## License & Distribution

The license terms for **binaries in this submodule** may differ from the repository-root **Apache-2.0** license. Refer to the `LICENSE` or EULA in the firmware submodule's own repository.

See [docs/en/LICENSE_POLICY.md](../docs/en/LICENSE_POLICY.md) / [docs/zh/LICENSE_POLICY.md](../docs/zh/LICENSE_POLICY.md) for details.
