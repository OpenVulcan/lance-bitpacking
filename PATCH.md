# lance-bitpacking with `paste` replaced by `pastey`

This repository holds the one patch [Vulcan Code](https://github.com/OpenVulcan/vulcan-code) applies to
`lance-bitpacking`. It is consumed through `[patch.crates-io]` with a pinned commit; it is not published
to crates.io.

- Source: crates.io `lance-bitpacking 11.0.0` (first commit, unchanged; `.crate` sha256
  `6f45658c5b2dc9aada41b66ee44b83af3fa888b7385ae414bae951b12a9f1cd3`).
- Upstream: <https://github.com/lance-format/lance> commit `ab6b5bbe46009ed78746b444df8db59a8bc5d842`,
  path `rust/compression/bitpacking`.
- Change: the manifest redirects the `paste` dependency to the maintained, API-compatible `pastey 0.2.3`
  and keeps the import name, so every Rust source file is identical to the published package. `LICENSE`
  is the upstream Apache-2.0 license, which the published package omits.
- Reason: `paste` is unmaintained and `lance-bitpacking 12.0.0` still depends on it. A local patch avoids
  upgrading the whole Lance data format and database interface.
- When Vulcan Code upgrades Lance, re-check this patch; once upstream drops `paste`, retire this
  repository and the override.
- Verification: run this crate's upstream bitpacking tests and every target of the Vulcan LanceDB engine.

Copyright remains with the Lance authors; see `LICENSE`.

## 中文说明

本仓库保存 Vulcan Code 对 `lance-bitpacking` 的唯一补丁：清单中的 `paste` 依赖改为维护中的 `pastey 0.2.3`，
保留原导入名，所有 Rust 源文件与 crates.io 发布包完全一致。第一个提交是原样导入的发布包，第二个提交是补丁。
Vulcan Code 通过 `[patch.crates-io]` 固定提交引用，不发布到 crates.io。升级 Lance 时必须重新检查；上游移除
`paste` 后删除本仓库与覆盖项。
