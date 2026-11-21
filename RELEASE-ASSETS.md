# Release 资产登记（二进制不入库）

本文件登记**必须**随 Release 上传的二进制及其摘要；仓库内 `SHA256SUMS.txt` 只覆盖仓库里实际存在的文本文件。

| 资产 | 字节数 | SHA-256 | 归属 Release |
|---|---|---|---|
| `Script.pvf` | 128,720,006 | `664829766ab016ad6935370281bb24820e40990a6db4d607607aa67b49d8da4b` | `client-v216-20261119` |
| `client-v216-selected-feedback-20261117.zip` | 36.4 MB | `e5bc8b0a7cc8854a9182757aae590ef0c6832dcf5a7b46cd62670b7f7c81785e` | 同上 |
| `PurpleMagic-1.0.16.exe` | 23,832,064 | `42e91426be92d2e9bf615f7a7316bed036af72f4d622358213e696fad69dbdbc` | 同上 |
| `client-v216-activity-npk-20261121.zip` | 1,171,594 | `bfc355eed84f5b86ff07bde8aceca3e453642b678f541860f5d98184a0c10596` | `client-v216-activity-npk-20261121`（补充预发行） |
| `profile.json` | — | `5ebc8e0a43b07efd049e5ca0bf0307902cd724a4b7f0fbe3c55b2ac7ea7ff6f0` | **不公开**，单独交付 |

> 上传后请把对应 Release 链接补进 README，并确认 `purplemagic-nexus/client/versions.json` 的
> `url` 与实际 Release 标签一致。

## 状态

- [x] [`client-v216-20261119`](https://github.com/yuanqilei/s5a3-client/releases/tag/client-v216-20261119) 已创建并上传 3 个公开资产（2026-11-20）
- [ ] `client-v216-activity-npk-20261121` 补充 NPK 预发行：待上传 Release 附件并发布
- [ ] `profile.json` 待私下交付（含服务器地址，禁止公开）
