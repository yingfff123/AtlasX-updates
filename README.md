# AtlasX Updates

公开升级通道：**不必改业务仓权限**。把升级包传到本仓 Releases，用户即可在 Web「设置 → 系统」一键检查/下载/应用。

## 用户配置

```bash
RADAR_UPDATE_CHANNEL_URL=https://raw.githubusercontent.com/yingfff123/AtlasX-updates/main/channel.json
```

或留空时，将应用默认 GitHub Releases 仓库设为 `yingfff123/AtlasX-updates`。

## 维护者发版

```bash
# 1) 上传 zip（资源名建议固定）
gh release create upgrade-0.2.5 ./atlasx-upgrade.zip \
  --repo yingfff123/AtlasX-updates \
  --title "Upgrade 0.2.5" \
  --notes "变更说明"

# 2) 更新 channel.json 的 version / download_url / sha256 后 commit
```

| 链接 | URL |
|------|-----|
| 检查更新 | https://raw.githubusercontent.com/yingfff123/AtlasX-updates/main/channel.json |
| 最新包 | https://github.com/yingfff123/AtlasX-updates/releases/latest/download/atlasx-upgrade.zip |
| Releases | https://github.com/yingfff123/AtlasX-updates/releases |
