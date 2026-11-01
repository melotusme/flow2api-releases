# Flow2API private releases

安装包和更新清单只放在这个私有仓库。源码仍是公开的 [TheSmallHanCat/flow2api](https://github.com/TheSmallHanCat/flow2api)。不要把这个仓库改成公开。

应用用本机 `gh` 登录，在原生后端读取固定仓库的数字 asset ID。令牌不进界面，也不写进配置。检查更新前，账号需要对这个仓库有读取权限。

Actions 里的 Publish signed release 只能手动触发。它按一次解析出的完整 commit SHA 同时构建 macOS universal 和 Windows x64。两个平台都成功后才发布 latest。源码提交还不在 GitHub 上时不要运行。

签名私钥是仓库 Secret `TAURI_SIGNING_PRIVATE_KEY`，密码为空。这是 Tauri updater 的 minisign，不是 Apple 公证，也不是 Windows Authenticode。macOS 构建使用 ad-hoc 签名。Windows 只有 x64，没有原生 ARM64。
