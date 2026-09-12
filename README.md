# AtlasX Updates

**AtlasX 官方升级通道**

本仓库仅用于发布应用升级包与更新清单（`channel.json`）。部署、源码与 Docker 镜像不在此托管。

---

## 用户：一键更新

在运行中的 AtlasX 实例配置更新通道后，于 Web 控制台完成检查与应用：

**设置 → 系统 → 检查更新 → 下载升级包 → 应用**

推荐环境变量：

```bash
RADAR_UPDATE_CHANNEL_URL=https://cdn.jsdelivr.net/gh/yingfff123/AtlasX-updates@main/channel.json
RADAR_UPDATE_GITHUB_REPO=yingfff123/AtlasX-updates
```

| 资源 | 地址 |
|------|------|
| 更新清单（推荐） | [channel.json · jsDelivr](https://cdn.jsdelivr.net/gh/yingfff123/AtlasX-updates@main/channel.json) |
| 更新清单（GitHub） | [channel.json · raw](https://raw.githubusercontent.com/yingfff123/AtlasX-updates/main/channel.json) |
| 最新升级包 | [Releases · upgrade-0.3.2](https://github.com/yingfff123/AtlasX-updates/releases/tag/upgrade-0.3.2) |
| 版本发布页 | [Releases](https://github.com/yingfff123/AtlasX-updates/releases) |

### 重启说明

| 当前版本 | 应用升级后 |
|----------|------------|
| **0.2.8 之前**（含 0.2.7.x）→ 升到 0.2.8 | Docker 须**手动**重启：`sudo systemctl restart docker` |
| **0.2.8 及以后** | 包内自动重启（macOS `kickstart` / Docker compose·共享旗标）；失败时再手动 `docker compose restart web worker` |

---

## 升级台账

| 日期 | 版本 | 内容 |
|------|------|------|
| 2026-09-13 | **0.3.2**（当前） | 路径发现修补 + worker 共享卷热更同步。[Release](https://github.com/yingfff123/AtlasX-updates/releases/tag/upgrade-0.3.2) · sha256 `9b234fe8c07cb012bfc833e4ef075aca40465fe62ef9ab158ec51fee453f683d` |
| 2026-09-12 | 0.3.1 | 路径发现热更：终态耗尽 + 波级隔离；瘦快照补 risk_level；Docker worker 同步。[Release](https://github.com/yingfff123/AtlasX-updates/releases/tag/upgrade-0.3.1) · sha256 `c2b0f4e7202062a507f6fdb55edba3e42605a1318963f714486376ed3b94a432` |
| 2026-09-12 | 0.2.9 | CE / Pro 均可升级；栈手测清单扩充。[Release](https://github.com/yingfff123/AtlasX-updates/releases/tag/upgrade-0.2.9) · sha256 `27a7577dc00c5617d3ab8280162743257ca66afa6a1ad2d91b1c6e38bac0b696` | CE / Pro 均可升级；栈手测清单扩充。[Release](https://github.com/yingfff123/AtlasX-updates/releases/tag/upgrade-0.2.9) · sha256  | CE / Pro 均可升级；栈手测清单扩充。[Release](https://github.com/yingfff123/AtlasX-updates/releases/tag/upgrade-0.2.9) · sha256 `a35d03de8e183b904732b3f00b67aed98e0130ed206bf9e47715bdbc080fd07b` |
| 2026-09-10 | 0.2.8 | veo 合法 0 命中打空指纹戳；升级自动重启（macOS `kickstart` / Docker）；`requires: 0.2.7.4`。[Release](https://github.com/yingfff123/AtlasX-updates/releases/tag/upgrade-0.2.8) · sha256 `62c5fe67f28e804b6cd404e99192f6e144eaa0e06744e984b369903d21270625` |
| 2026-09-08 | 0.2.7.1 | 多任务稳定性：pipeline / worker / db / collectors / paths |
| 2026-09-08 | 0.2.7 | 多任务 stage-lock、idle-tx、删除 FK、wayback 熔断隔离；`requires: 0.2.6` |
| 2026-09-07 | 0.2.6 | 登录页纯前端验证码；须逐版升级（禁止跳版本）。[Release](https://github.com/yingfff123/AtlasX-updates/releases/tag/upgrade-0.2.6) |
| 2026-09-07 | 0.2.5.1 | 去掉扫描策略页 Community/Pro 共用说明文案。[Release](https://github.com/yingfff123/AtlasX-updates/releases/tag/upgrade-0.2.5.1) |
| 2026-09-07 | 0.2.5.0 | 应用升级后自动重启本实例（LaunchAgent / daemon）；含 0.2.5 能力。[Release](https://github.com/yingfff123/AtlasX-updates/releases/tag/upgrade-0.2.5.0) |
| 2026-09-05 | 0.2.5 | 扫描任务级联删除；系统更新修复（检查/同版补丁/sha256）；默认通道改 GitHub Releases。[Release](https://github.com/yingfff123/AtlasX-updates/releases/tag/upgrade-0.2.5) |

逐版升级：检查更新只推下一档；应用端拒绝跳版本（除非包声明允许）。

---

## 相关项目

| 项目 | 说明 |
|------|------|
| [AtlasX](https://github.com/yingfff123/AtlasX) | Linux / Docker 一键部署 |
| 容器镜像 | `ghcr.io/yingfff123/atlasx` |

Docker 整镜像升级请使用部署仓的 `update.sh`（调整 `ATLASX_IMAGE_TAG`），与本仓库的 zip 升级包相互独立。

---

## 安全

- 请仅从本仓库 Releases 或经官方 `channel.json` 声明的 `download_url` 获取升级包。
- 应用端可对 `sha256` 做完整性校验；请勿信任来源不明的第三方压缩包。
- 本仓库不存放密钥、`.env` 或签发私钥。

---

## License

与 AtlasX 主项目一致（MIT）。
