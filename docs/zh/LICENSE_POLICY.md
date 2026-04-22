# 许可证与分发策略（根仓库）

本文档记录本聚合仓库的**既定策略**，便于与 Espressif 常见开源实践及内部法务流程对齐。若与正式法务结论不一致，**以法务结论为准**，并应更新本文件与根目录法律文本。

## 根仓库（本仓库自有内容）

- **许可证**：**Apache License 2.0**（见仓库根目录 `LICENSE`）。
- **适用范围**：本仓库中**非子模块、非预编译固件二进制**的内容，例如根目录与 `docs/` 下的文档、脚本、构建辅助、占位说明等。
- **与 Espressif 开源策略的对应关系**：Espressif 大量开源项目采用 Apache-2.0；根仓库采用同族许可有利于策略一致性与合规说明的可复用性。

## Git 子模块（`wifi-driver/`、`bluetooth-driver/`、`firmware/` 等）

- **各自仓库根目录的 `LICENSE` 为准**；本聚合仓**不对**上游仓库树做统一再许可。
- Wi-Fi 与 Bluetooth 主机驱动子模块采用 **GPL-2.0** 许可，这是 Linux 内核模块的标准做法。根仓库的 Apache-2.0 与驱动的 GPL-2.0 不存在冲突，因为它们适用于通过子模块指针连接的独立组件，不构成衍生作品。
- 驱动子模块可能面向**芯片族或通用 Linux 驱动**，不限于 ESP32E22 单一芯片名；本仓通过版本与文档锁定支持矩阵（见 [SUBMODULES.md](SUBMODULES.md)）。
- 根仓库中的脚本或构建辅助**不得**嵌入或派生自 GPL 许可的驱动源码，否则相关文件需改为 GPL 许可。

### 子模块许可证汇总

| 子模块 | 许可证 (SPDX) | 版权持有者 |
| ------ | ------------- | ---------- |
| `wifi-driver/` | <!-- TODO: 确认 SPDX 许可证 --> | <!-- TODO: 确认版权持有者 --> |
| `bluetooth-driver/` | <!-- TODO: 确认 SPDX 许可证 --> | <!-- TODO: 确认版权持有者 --> |
| `firmware/` | <!-- TODO: 确认许可证 --> | <!-- TODO: 确认版权持有者 --> |

## 固件子模块（`firmware/`）

- `firmware/` 目录为 **Git 子模块**，指向上游固件仓库。
- **与根仓库源码许可分离**：预编译固件可能受单独条款约束（例如专用 EULA、闭源二进制分发条件）。适用许可以固件子模块仓库根目录为准。
- **发布时须**在固件子模块内提供清晰说明：`README.md`，以及必要时 `LICENSE` / EULA / `NOTICE` 片段。
- 在条款未定稿前，可使用占位说明并标注「待发布时更新」，避免法律空白；**正式发布（GA）前**须由产品与法务相关方审核批准。

## SPDX 版权标头要求

本仓库自有的所有**脚本、构建辅助和源文件**必须包含 [SPDX](https://spdx.dev/) 版权标头，格式如下：

```
// SPDX-FileCopyrightText: 2026 Espressif Systems (Shanghai) CO LTD
// SPDX-License-Identifier: Apache-2.0
```

根据文件类型使用对应的注释风格（如 Shell/Python 用 `#`，C 用 `/* */`）。

- **Git 子模块**内的文件遵循各上游仓库自身的标头规范。
- **`firmware/`** 目录下的预编译二进制文件免于添加源码标头，其条款由子模块级 `LICENSE` / EULA 覆盖。

<!-- TODO: 添加版权标头 CI 检查（参考 esp-idf 的 tools/ci/check_copyright_config.yaml）。 -->
<!-- TODO: 与法务确认准确的乐鑫法律实体名称和版权年份范围。 -->

## 变更记录

| 日期       | 说明 |
| ---------- | ---- |
| 2026-04-14 | 根仓库 Apache-2.0；子模块与固件分层说明；SPDX 标头要求；固件改为子模块。 |

*English: [docs/en/LICENSE_POLICY.md](../en/LICENSE_POLICY.md)*
