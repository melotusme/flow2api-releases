# Flow2API releases

Flow2API 桌面版的安装包和更新清单。源码在公开 fork [melotusme/flow2api](https://github.com/melotusme/flow2api)（上游是 [TheSmallHanCat/flow2api](https://github.com/TheSmallHanCat/flow2api)）。

## 安装

- macOS（Apple Silicon / Intel 通用包）：`brew tap melotusme/flow2api && brew install --cask melotusme/flow2api/flow2api`，或下载 [最新 Release](https://github.com/melotusme/flow2api-releases/releases/latest) 里的 `Flow2API.app.tar.gz`。
- Windows x64：下载最新 Release 的 `Flow2API.windows.x64.exe`，对照 `SHA256SUMS` 校验后安装（静默安装参数是大写 `/S`）。
- Linux x64：`Flow2API.linux.x64.AppImage`。

安装后应用会自动检查这里的最新 Release，下载后先验证签名再安装，不需要 GitHub 登录。

## 发布

Actions 里的 Publish signed release 只能手动触发：`gh workflow run "Publish signed release" -R melotusme/flow2api-releases -f source_ref=main`。它按一次解析出的完整 commit SHA 构建 macOS universal、Windows x64 和 Linux x64，全部成功后才发布 latest。这个仓库是公开的，Actions 免费。

签名私钥是仓库 Secret `TAURI_SIGNING_PRIVATE_KEY`。这是 Tauri updater 的 minisign 签名，不是 Apple 公证，也不是 Windows Authenticode。macOS 使用 ad-hoc 签名。
