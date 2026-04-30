# Contributing

## What fits this aggregate repository

- **Documentation**: architecture, submodule workflow, firmware–driver version matrices, typos and link fixes.
- **Metadata and scripts**: build orchestration, checksum manifests, minimal CI helpers (with maintainer agreement).
- **Structure and placeholders**: paths and conventions aligned with submodules and releases.

## Where to file issues

Wi-Fi and Bluetooth cannot always be treated as fully independent — a chip-level crash affects both stacks, and coexistence problems are often hard to attribute to one side. Use the following guidelines:

- **Chip-level issues** (e.g. system crash, firmware hang, ROM/boot failures): file in **this repository**.
- **Driver-specific issues** (clearly limited to Wi-Fi or Bluetooth host driver code): file in the corresponding **upstream repo** referenced by `wifi-driver/` or `bluetooth-driver/`.
- **Cannot tell which side is at fault** (e.g. coexistence anomalies, unclear hangs): file in **this repository**; maintainers will triage and redirect if needed.
- **On-chip firmware source** (when out of scope here): follow that firmware/SDK project's process.

## Code changes

- **Wi-Fi / Bluetooth driver code**: submit changes to the **upstream repos** referenced by `wifi-driver/` and `bluetooth-driver/`. This repo bumps submodule pointers and maintains docs, metadata, and release orchestration.

## Contributor agreement

By submitting a contribution (pull request, patch, or other form) to this repository, you agree that:

1. Your contribution is your original work, or you have the right to submit it under the applicable license.
2. You grant Espressif Systems a perpetual, worldwide, non-exclusive, royalty-free, irrevocable license to use, reproduce, modify, and distribute your contribution under the terms of the **Apache License 2.0** (or the license applicable to the specific component).
3. You understand that your contribution may be incorporated into Espressif products and redistributed under the same or compatible terms.

If a formal CLA or DCO requirement is introduced, it will be documented before
external contributions are accepted under that process.

## Process notes

1. When changing submodule pointers, explain **why**, **what was tested**, and **matching firmware version** (if any) in the **commit message body** and the MR/PR (so `git log` matches what reviewers read).
2. License or third-party notice changes must update [LICENSE_POLICY.md](LICENSE_POLICY.md) together with [docs/zh/LICENSE_POLICY.md](../zh/LICENSE_POLICY.md). Keep both language versions in sync.

## Branch naming

Conventions for **integration**, **merge-request (topic)**, and **release** branches in this aggregate repository.

### Integration default

Day-to-day work merges into **`main`** unless maintainers agree on another long-lived integration branch.

### Merge-request / topic branches

Use **short-lived** branches for MRs/PRs: branch off `main`, open the merge request, merge, then delete the branch.

**Pattern:** **`type/short-slug`**

- **`type`** — same vocabulary as [Conventional Commits](https://www.conventionalcommits.org/) and as in [**Commit messages**](#commit-messages) below: `feat`, `fix`, `docs`, `firmware`, `ci`, `test`, `chore`, `refactor`, `revert`, `perf`, `build`, …
- **`short-slug`** — lowercase, **ASCII hyphens**, no spaces; describe the change briefly.

**Examples:** `feat/manifest-checksum-field`, `docs/en-fix-submodules-link`, `firmware/bump-prebuilt-submodule`

### Release branches

**Optional.** Maintainers may create a **release line** when stabilizing a release separately from `main`.

**Pattern:** **`release/vN`**

- **`N`** — non-negative integer matching the official aggregate-repo release index and the **`vN`** git tag (see [firmware/VERSIONING.md](../../firmware/VERSIONING.md): `v1`, `v2`, …).
- Not every tag requires a long-lived branch; use **`release/vN`** only when you need ongoing fixes on a stabilization line before tagging.

## Commit messages

- **Subject (first line):** English, imperative mood, about **72 characters** or less. Prefer [Conventional Commits](https://www.conventionalcommits.org/): `type(optional scope): short description` (e.g. `feat(scripts):`, `docs(en):`, `firmware:`, `fix(ci):`).
- **Type:** Use [Conventional Commits](https://www.conventionalcommits.org/) types; pick the one that matches the **main** change:
  - `feat` — new capability *in this repo* (e.g. manifest fields, release/validation scripts, CI)
  - `fix` — correct broken behavior in docs, tooling, tests, or automation
  - `docs` — documentation only
  - `firmware` — submodule or manifest under `firmware/`
  - `ci` — CI configuration or pipelines
  - `test` — tests only
  - `chore` — mechanical or maintenance work
  - `refactor` — restructure without intended behavior change
  - `revert` — revert a prior commit
  - `perf` — performance of scripts or tools
  - `build` — build or packaging glue
- **Repository context:** **Host driver code** is usually committed in **upstream** driver repos (follow *their* conventions). In *this* aggregate repository, `feat` / `fix` usually refer to docs, submodules, manifests, scripts, and CI here—not a full driver feature that lives only upstream.
- **Body:** For **submodule pointer** updates, **version or manifest** changes, or **license/notice** edits that are not self-explanatory, include: **why**; **what was tested**; **firmware or driver version** (tag, commit SHA, or version string) when it matters. Small typo-only or link-only doc fixes can omit a body.

*中文: [docs/zh/CONTRIBUTING.md](../zh/CONTRIBUTING.md)*
