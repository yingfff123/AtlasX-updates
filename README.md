# AtlasX Updates

公开升级通道。把升级包传到本仓 **Releases**，用户在 Web「设置 → 系统」即可检查 / 下载 / 应用。

> `AtlasX-docker` 若保持 Private，不要把 channel 只放在那边——匿名拉不到。

## 用户配置

```bash
RADAR_UPDATE_CHANNEL_URL=https://cdn.jsdelivr.net/gh/yingfff123/AtlasX-updates@main/channel.json
```

## 你怎么上传

```bash
gh release create upgrade-0.2.5 ./atlasx-upgrade.zip \
  --repo yingfff123/AtlasX-updates \
  --title "Upgrade 0.2.5" \
  --notes "变更说明"
```

然后改本仓根目录 `channel.json` 的 `version` / `download_url` / `sha256` 并提交。

资源名建议固定为 **`atlasx-upgrade.zip`**，这样 latest 链接不用改。

## 链接

| 用途 | URL |
|------|-----|
| 检查更新（推荐） | https://cdn.jsdelivr.net/gh/yingfff123/AtlasX-updates@main/channel.json |
| 检查更新（raw） | https://raw.githubusercontent.com/yingfff123/AtlasX-updates/main/channel.json |
| 最新包 | https://github.com/yingfff123/AtlasX-updates/releases/latest/download/atlasx-upgrade.zip |
| Releases | https://github.com/yingfff123/AtlasX-updates/releases |
