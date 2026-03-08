# CLAUDE.md

## 项目概述

Skills Manager v2 — AI Agent Skills 桌面管理工具，基于 Tauri 2 + React + TypeScript 构建。

## 技术栈

- **前端**: React 19 + TypeScript + Vite
- **后端**: Tauri 2 (Rust)
- **数据库**: SQLite (rusqlite)
- **构建/发布**: GitHub Actions 跨平台自动构建

## 发版规范

每次打 tag 发版前，**必须**先更新 `CHANGELOG.md`：

1. 在 `CHANGELOG.md` 顶部新增版本条目，格式遵循 [Keep a Changelog](https://keepachangelog.com/en/1.1.0/)
2. 同步更新以下文件中的版本号：
   - `package.json` → `"version"`
   - `src-tauri/tauri.conf.json` → `"version"`
   - `src/i18n/en.json` → `settings.version`（设置页面显示的版本号）
   - `src/i18n/zh.json` → `settings.version`（设置页面显示的版本号）
3. 提交变更后再打 tag

```bash
# 示例流程
git add CHANGELOG.md package.json src-tauri/tauri.conf.json src/i18n/en.json src/i18n/zh.json
git commit -m "chore: bump version to x.y.z"
git tag vx.y.z
git push origin main --tags
```

## CHANGELOG 格式

```markdown
## [x.y.z] - YYYY-MM-DD

### Added      (新功能)
### Changed    (已有功能变更)
### Fixed      (Bug 修复)
### Removed    (移除的功能)
```

## 关键路径

| 文件/目录 | 说明 |
|-----------|------|
| `src/` | React 前端源码 |
| `src-tauri/` | Rust 后端源码 |
| `src-tauri/tauri.conf.json` | Tauri 配置（版本号、窗口、打包） |
| `.github/workflows/release.yml` | CI 跨平台构建 workflow |
| `CHANGELOG.md` | 版本变更记录 |
