# 简介

基于 [v2fly/domain-list-community#256](https://github.com/v2fly/domain-list-community/issues/256) 的提议，重构 [v2fly/domain-list-community](https://github.com/v2fly/domain-list-community) 的构建流程，并添加新功能。

本 fork 额外维护 `data/` 下的语义化域名列表，用于给 `jaguarocean/clash-rules` 等下游项目生成独立 provider。当前内置的本地扩展列表包括：

- `ai-services`
- `developer`
- `social`
- `meeting`
- `ip-check`

## 与官方版 `dlc.dat` 不同之处

- 将 `dlc.dat` 重命名为 `geosite.dat`
- 去除 `cn` 列表里带有 `@ads`、`@!cn` 属性的规则
- 去除 `geolocation-cn` 列表里带有 `@ads`、`@!cn` 属性的规则
- 去除 `geolocation-!cn` 列表里带有 `@ads`、`@cn` 属性的规则，尽量避免在中国大陆有接入点的海外公司的域名走代理。例如，避免国区 Steam 游戏下载服务走代理。

## 下载地址

[https://github.com/jaguarocean/domain-list-custom/releases/latest/download/geosite.dat](https://github.com/jaguarocean/domain-list-custom/releases/latest/download/geosite.dat)

本 fork 的纯文本导出产物发布在 `release` 分支，供下游直接消费，例如：

- `https://raw.githubusercontent.com/jaguarocean/domain-list-custom/release/ai-services.txt`
- `https://raw.githubusercontent.com/jaguarocean/domain-list-custom/release/developer.txt`
- `https://raw.githubusercontent.com/jaguarocean/domain-list-custom/release/social.txt`
- `https://raw.githubusercontent.com/jaguarocean/domain-list-custom/release/meeting.txt`
- `https://raw.githubusercontent.com/jaguarocean/domain-list-custom/release/ip-check.txt`

GitHub Actions 在构建时会先 checkout 官方 `domain-list-community`，再用本仓 `data/` 覆盖同名/新增列表，因此本地维护项也会进入 `geosite.dat` 和 `release/*.txt`。

## 使用本项目的项目

[@Loyalsoldier/v2ray-rules-dat](https://github.com/Loyalsoldier/v2ray-rules-dat)
