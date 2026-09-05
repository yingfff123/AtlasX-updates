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
| 最新升级包 | [atlasx-upgrade.zip](https://github.com/yingfff123/AtlasX-updates/releases/latest/download/atlasx-upgrade.zip) |
| 版本发布页 | [Releases](https://github.com/yingfff123/AtlasX-updates/releases) |

应用升级包后请重启 **web** 与 **worker** 进程（或 `docker compose restart web worker`）使变更生效。

---

## 发布说明（维护者）

1. 按 AtlasX 升级包规范打包（`manifest.json` + `payload/`，路径须在应用白名单内）。
2. 创建 Release，资源文件名建议固定为 **`atlasx-upgrade.zip`**，便于 `latest` 直链稳定。
3. 更新本仓库根目录 `channel.json` 字段：`version`、`notes`、`download_url`、`sha256`（zip 的 SHA-256）。

示例：

```bash
gh release create upgrade-x.y.z ./atlasx-upgrade.zip \
  --repo yingfff123/AtlasX-updates \
  --title "AtlasX x.y.z" \
  --notes "发布说明"
```

`channel.json` 示例结构：

```json
{
  "name": "AtlasX",
  "version": "x.y.z",
  "notes": "本版本变更摘要",
  "download_url": "https://github.com/yingfff123/AtlasX-updates/releases/download/upgrade-x.y.z/atlasx-upgrade.zip",
  "sha256": "<sha256>"
}
```

---

## 相关项目

| 项目 | 说明 |
|------|------|
| [AtlasX-docker](https://github.com/yingfff123/AtlasX-docker) | Linux / Docker 一键部署 |
| 容器镜像 | `ghcr.io/yingfff123/atlasx-docker` |

Docker 整镜像升级请使用部署仓的 `update.sh`（调整 `ATLASX_IMAGE_TAG`），与本仓库的 zip 升级包相互独立。

---

## 安全

- 请仅从本仓库 Releases 或经官方 `channel.json` 声明的 `download_url` 获取升级包。
- 应用端可对 `sha256` 做完整性校验；请勿信任来源不明的第三方压缩包。
- 本仓库不存放密钥、`.env` 或签发私钥。

---

## License

与 AtlasX 主项目一致（MIT）。
