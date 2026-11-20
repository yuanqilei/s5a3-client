# S5A3 Client（客户端补丁与版本清单）

> ⚠️ **当前状态（2026-11-20）**：下列二进制**尚未上传任何 Release**，
> 因此本仓目前不能独立拿到 PVF / v216 补丁 / 登录器；请先按 `RELEASE-ASSETS.md` 建 Release。
>
> 本仓只保存客户端补丁说明、版本清单、校验值和脱敏配置示例。
> 二进制产物（v216 补丁 ZIP、Script.pvf、PurpleMagic 登录器 EXE）**不提交 Git**，作为对应 Release 附件分发，摘要见 `SHA256SUMS.txt`。
> 真实 `profile.json` 含服务器地址与线上配置，禁止进公开仓；本仓只提供 `profile.example.json`（占位值）。
> 登录器源码与发布在 [`purplemagic-nexus`](https://github.com/yuanqilei/purplemagic-nexus)。

---

# S5A3 客户端、PVF 与登录器 1.0.16 离线交付（原始交付说明）

生成日期：2026-11-19。来源：`Cec1c/ServerS5A3` Releases；登录器由交接的②号源码和③号构建输入编译。此目录是待部署产物，线上服务、玩家更新通道与 GitHub Release 尚未切换。

## 选用组合

- PVF：`Script.pvf`，128,720,006 字节，SHA-256 `664829766ab016ad6935370281bb24820e40990a6db4d607607aa67b49d8da4b`。
- 客户端：v216 预发行补丁，需把 `DNF.exe`、`CombatPower.dll`、`DpsMeter.dll`、`ImagePacks2` 中的 NPK **成套合并**到现有客户端；保留现有依赖和玩家 INI。v216 ZIP 不含 PVF。
- 本次 `profile.json` 和登录器按 v216 EXE SHA-256 `58e51fba3258a9499e77caedaea16a6d9f38904054e10edd91564e24894547c4` 构建。
- 登录器：`PurpleMagic-1.0.16.exe`，23,832,064 字节，SHA-256 `42e91426be92d2e9bf615f7a7316bed036af72f4d622358213e696fad69dbdbc`。此目录只保留部署用的单文件 EXE。
- `channel.override.etc` 来自①号源码的推荐 120 频道表，和源码内测试数据逐字节一致；替换线上频道表前仍须核对当前运行配置。

所有文件的完整摘要见 `SHA256SUMS.txt`。`profile.json` 含服务地址、公钥及资源摘要，无口令、Token 或私钥；请不要放进公开源码仓库。

## 部署次序

1. 备份服务端两处 PVF、数据库 `dnf_local`、`data2/` 与玩家客户端；记录现有摘要和回滚路径。
2. 将此 `Script.pvf` 同时用于服务端和客户端，核对摘要。按①号源码说明确认 `channel.override.etc` 与实际频道目录同代；重新生成频道目录并重启游戏服。
3. 用新 PVF 运行 `GMTool -rebuild-index`，等索引完成并核对资源摘要。
4. 使用 v216 的四项文件整包更新客户端。对应服务端如需启用帝国新协议，参照①号源码 `Docs/SELECTED_PUBLICATION_20261117.md` 显式配置 `tag_buff_group_sync` 和精确客户端身份；v216 的真实 GUI 与完整勇气施放仍需玩家验收。
5. 将此 `profile.json` 同步到实际 Hub 私有档案与已发布状态，再发布新登录器。`client/versions.json` 已记录 1.0.16 的真实大小和 SHA-256；其中的 GitHub Release URL 需上传同一 EXE 后才能使用。
6. 核对玩家实际下载结果、登录/注册/建角和频道列表；有问题时按备份回滚 PVF、客户端、登录器、索引和配置。

此交付没有访问线上服务器或修改玩家数据。
