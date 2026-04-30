# 贡献指南

## 本聚合仓库适合贡献的内容

- **文档**：架构说明、子模块工作流、固件–驱动版本矩阵、错别字与链接修正。
- **元数据与脚本**：构建编排、校验清单生成、最小化 CI 辅助（在维护者认可范围内）。
- **目录占位与约定**：与子模块路径、发布流程一致的结构性更新。

## Issue 报告指引

Wi-Fi 与 Bluetooth 并非总能完全独立看待——芯片级崩溃会同时影响两个协议栈，共存场景中的问题往往难以归因于某一方。请参考以下原则：

- **芯片级问题**（如系统崩溃、固件挂起、ROM/启动失败）：在**本仓库**报告。
- **驱动独有问题**（明确仅涉及 Wi-Fi 或 Bluetooth 主机驱动代码）：在 `wifi-driver/` 或 `bluetooth-driver/` 所指向的**上游仓库**报告。
- **无法区分是哪一方的问题**（如共存异常、不明挂起）：在**本仓库**报告，维护者会进行分流，必要时转至对应上游。
- **芯片固件源码**（不在本聚合仓范围内时）：遵循相应固件/SDK 项目流程。

## 代码变更

- **Wi-Fi / Bluetooth 驱动代码**：请向 `wifi-driver/` 和 `bluetooth-driver/` 所指向的**上游仓库**提交。本仓库负责更新子模块指针，维护文档、元数据与发布编排。

## 贡献者协议

向本仓库提交贡献（Pull Request、补丁或其他形式）即表示您同意以下条款：

1. 您的贡献为原创作品，或您有权在适用许可证条款下提交该贡献。
2. 您授予乐鑫信息科技（Espressif Systems）一项永久、全球性、非独占、免版税、不可撤销的许可，允许其在 **Apache License 2.0**（或适用于特定组件的许可证）条款下使用、复制、修改和分发您的贡献。
3. 您理解您的贡献可能被纳入乐鑫产品，并在相同或兼容条款下再分发。

如果后续引入正式 CLA 或 DCO 要求，将在按该流程接收外部贡献前补充说明。

## 流程提示

1. 变更子模块指针时，请在**提交说明正文**与 MR/PR 中说明**原因**、**测试范围**与**对应固件版本**（若适用），使 `git log` 与评审可见信息一致。
2. 涉及许可证或第三方声明的变更，请同步更新 [LICENSE_POLICY.md](LICENSE_POLICY.md)（并与[英文版](../en/LICENSE_POLICY.md)内容保持一致）。

## 分支命名

本**聚合仓库**中**集成分支**、**合并请求用话题分支**与**发布分支**的命名约定。

### 集成默认分支

日常开发合并进 **`main`**，除非维护者约定使用其他长期集成分支。

### 合并请求 / 话题分支

通过 MR/PR 贡献时使用**短生命周期**分支：自 `main` 分出、发起合并请求、合并后删除分支。

**格式：** **`类型/短标识`（`type/short-slug`）**

- **`type`** — 与 [Conventional Commits](https://www.conventionalcommits.org/) 及**下文「提交信息」**所列**类型**一致，例如 `feat`、`fix`、`docs`、`firmware`、`ci`、`test`、`chore`、`refactor`、`revert`、`perf`、`build` 等。
- **`short-slug`** — 小写、**半角连字符**、无空格；用简短英文概括变更。

**示例：** `feat/manifest-checksum-field`、`docs/en-fix-submodules-link`、`firmware/bump-prebuilt-submodule`

### 发布分支

**可选。** 若需要在 `main` 之外单独稳定某一版发布，维护者可拉**发布线**。

**格式：** **`release/vN`**

- **`N`** — 非负整数，与官方聚合仓发布序号及 git 标签 **`vN`** 一致（见 [firmware/VERSIONING.md](https://github.com/espressif/esp32e22-fw/blob/main/VERSIONING.md)，如 `v1`、`v2` …）。
- 并非每次打标都要长期保留分支；仅在打标前需要**稳定线**上持续修问题时再使用 **`release/vN`**。

## 提交信息（commit message）

- **首行（标题）：** 使用**英文**、**祈使语气**，约 **72 个字符**以内。推荐 [Conventional Commits](https://www.conventionalcommits.org/)：`类型(可选范围): 简短说明`（例如 `feat(scripts):`、`docs(zh):`、`firmware:`、`fix(ci):`）。
- **类型**：采用 [Conventional Commits](https://www.conventionalcommits.org/) 中的类型名，按**主要变更**择一：
  - `feat` — 本仓库内**新增**对外可见能力（如清单字段、发布/校验脚本、CI）
  - `fix` — 修正错误行为（文档、工具、测试、自动化等）
  - `docs` — 仅文档
  - `firmware` — `firmware/` 子模块或清单
  - `ci` — CI 配置或流水线
  - `test` — 仅测试
  - `chore` — 机械性维护
  - `refactor` — 无意图改行为的重构
  - `revert` — 回滚某次提交
  - `perf` — 脚本或工具性能
  - `build` — 构建或打包相关流程
- **适用范围**：**主机端驱动源码**一般在上游**驱动仓库**中提交（遵循**上游**习惯）。在**本聚合仓**中，`feat` / `fix` 多指本仓库的文档、子模块、清单、脚本与 CI，而不是仅存在于上游的完整「驱动功能」开发。
- **正文**：对**子模块指针**、**版本/清单**变更，或**许可证/声明**等不易从 diff 直观看懂的修改，在正文中写清**原因**、**测试情况**、以及**固件或驱动版本**（标签、提交 SHA 或版本号）。仅错别字、单处链接等微小文档修复可省略正文。

*English: [docs/en/CONTRIBUTING.md](../en/CONTRIBUTING.md)*
