# Git 子模块约定

本聚合仓库通过 **Git 子模块** 引用上游 Wi-Fi / Bluetooth Linux 驱动及预编译固件。**许可证以各子仓库根目录文件为准**，见 [LICENSE_POLICY.md](LICENSE_POLICY.md)。

## 推荐路径名（与仓库目录一致）

| 路径 | 预期内容 |
| ---- | -------- |
| `wifi-driver/` | Wi-Fi 主机驱动源码树 |
| `bluetooth-driver/` | Bluetooth 主机驱动源码树 |
| `firmware/` | 预编译固件二进制、发布说明及相关许可/EULA |

后续若使用 `git submodule add`，请优先使用上述路径，避免与已有文档和 CI 约定冲突。所有子模块均使用**相对 URL**（如 `../esp32e22-fw`），确保在 GitLab 和 GitHub 镜像上都能正确解析。

| 子模块 | 相对 URL |
| ------ | -------- |
| `firmware/` | `../esp32e22-fw` |
| `wifi-driver/` | `../esp-wifi-drv` |
| `bluetooth-driver/` | TODO |

## 驱动不限于「仅 ESP32E22」

子模块可能指向 **芯片族级或通用 Linux 驱动** 仓库；本仓通过以下方式锁定 **ESP32E22** 支持矩阵：

- 在文档与发布说明中明确 **已验证的 commit/tag** 与 **内核版本范围**；
- 在 `firmware/` 子模块与 [FIRMWARE.md](FIRMWARE.md) 中声明 **固件与驱动的匹配关系**。

## 工作流摘要

1. **首次克隆（含子模块）**  
   ```bash
   git clone --recurse-submodules <本仓库 URL>
   ```
   若已克隆未带子模块：
   ```bash
   git submodule update --init --recursive
   ```

2. **更新子模块到上游新提交**  
   在子模块目录内 `git fetch` / `git checkout` 到目标提交后，回到聚合仓根目录提交 **子模块指针变更**。

3. **固定版本**  
   发布时建议将子模块指向 **明确 tag 或 SHA**，并在 Release 说明中记录；避免「悬浮在分支 HEAD」导致不可复现构建。

## 与上游通用驱动仓库的关系

- 上游可能同时服务多款芯片或模块；本仓 **不 fork 业务逻辑**，以子模块指针 + 文档矩阵表达「对本芯片组合的支持声明」。
- 缺陷与功能请求：若问题属于上游驱动，应在 **对应子模块仓库** 跟踪；本仓可保留元 issue 用于版本对齐与发布协调。

*English: [docs/en/SUBMODULES.md](../en/SUBMODULES.md)*
