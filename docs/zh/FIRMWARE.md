# 固件二进制

本页描述预编译固件的**当前布局、命名与版本契约**。`firmware/` 目录为 **Git 子模块**，
指向上游固件交付仓库 [`esp32e22-fw`](https://github.com/espressif/esp32e22-fw#readme)。

## 布局与命名

| 项目 | 说明 |
| ---- | ---- |
| 目录 | 仓库内 `firmware/` 子模块，见该子模块的 `README.md` |
| 仓库内固件制品 | `firmware` 子模块内的 `esp32e22-fw.bin`；这是当前固件仓用于保持单一固件二进制的仓库侧文件名 |
| Linux 运行时安装路径 | 当前 Linux 驱动请求 `/lib/firmware/espressif/esp32e22.bin`；打包或安装流程需要将仓库内固件制品映射到该运行时文件名 |
| Manifest | `manifest.json` 记录固件版本、构建日期、大小、SHA-256、源码提交、功能标志和 Secure Download 支持情况 |
| 版本规则 | `firmware/VERSIONING.md` 定义版本规则、发布流程和 manifest schema |
| 校验 | SHA-256 校验值记录在 `manifest.json` 中 |

仓库内固件制品名与 Linux 运行时文件名有意分离。固件子模块保留一个用于版本管理和发布跟踪的规范二进制；
各主机侧打包流程可以按对应驱动的要求安装或重命名该二进制。对当前 Linux 驱动而言，安装后的文件名是
`espressif/esp32e22.bin`。

## 固件–驱动兼容性要求

- 驱动与固件存在 **ABI/协议版本** 依赖；**不匹配的组可能导致无法枚举、固件加载失败或运行时异常**。
- **早期版本**：每个驱动发布仅对应**唯一一个固件版本**（1:1 配对）。初始版本不计划在同一驱动中支持多个固件版本。
- 每次发布必须包含兼容性表格，映射**驱动版本（或子模块 SHA） ↔ 对应固件版本 ↔ 测试过的内核范围**。

## 获取方式

- 克隆本聚合仓时带上子模块，或在已克隆仓库中初始化/更新子模块：
  ```bash
  git submodule update --init --recursive
  ```
- 正式发布页或内部制品库也可以提供打包后的二进制；使用这些分发渠道时，
  必须与本仓库固定的 `firmware/` 子模块提交保持一致。

## 法律与再分发

- 二进制许可可能与根仓库 **Apache-2.0** 不同；以固件子模块仓库内的 `LICENSE`、EULA 及 `README.md` 为准，详见 [LICENSE_POLICY.md](LICENSE_POLICY.md)。

*English: [docs/en/FIRMWARE.md](../en/FIRMWARE.md)*
