# 第一次把 DuoCinema 上传到 GitHub（推荐用 GitHub Desktop）

> 本仓库源码已经打包好，不需要先学 Git 命令行。**先不要上传 IPA**，确保你能用 Xcode 打开工程并成功运行。

1. 解压 `DuoCinema_GitHub_完整原创源码仓库.zip`，打开里面的 `DuoCinema_GitHub_Original_Source_v1.8` 文件夹。
2. 登录 GitHub，打开 GitHub Desktop（官方免费桌面程序）。
3. GitHub Desktop 菜单 **File → Add Local Repository**，选择上述文件夹。如果提示它还不是 Git 仓库，点 **Create a Repository Here**。
4. 仓库名建议 `DuoCinema`；描述可用：`An open-source SwiftUI media player exploring foldable iPhone Duo interactions and WebDAV libraries.`
5. 在 GitHub Desktop 填写提交说明，如 `Initial open-source preview v0.18.0`，点击 **Commit to main**。
6. 点击 **Publish repository**，注意：若要粉丝能访问，**不要**勾选 `Keep this code private`。第一次公开前务必确认仓库里没有个人秘密。
7. 打开 GitHub 仓库首页，确认 README、LICENSE、DuoCinema.xcodeproj、DuoCinema 文件夹及 docs 都完整。
8. GitHub → **Settings → General** 可确认默认分支；**About**（右上角齿轮）填写简介与 Topics，例如 `swiftui`, `ios`, `video-player`, `webdav`, `foldable`。
9. 编译验证并准备好真正 IPA 后，再进入 **Releases → Draft a new release**，设置 tag `v0.18.0-preview`，上传 IPA、填写 `docs/RELEASE_TEMPLATE.md` 中的说明，点 **Publish release**。首次仅发布源码也完全可以。

## 贴给粉丝的说明

见根目录 `README.md` 和 `docs/RELEASE_TEMPLATE.md`。无需任何人把 Apple ID 密码发给开发者。不要索取粉丝 UDID、Apple ID 或签名证书。
