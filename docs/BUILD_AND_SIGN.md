# Xcode 打包与用户自行签名教程

## A. 最适合粉丝的方式：下载源码、自己在 Xcode 签名

1. 在 GitHub 点击 **Code → Download ZIP**。
2. 解压并打开 `DuoCinema.xcodeproj`。
3. 在 **DuoCinema Target → Signing & Capabilities** 选择自己的 Apple Team；如果没有 Team，可先在 Xcode → Settings → Accounts 中添加自己的 Apple 账号。
4. 更改 **Bundle Identifier**：默认 `com.example.duocinema` 仅是演示值，实际签名须唯一。
5. 连接自己的 iPhone，按需在手机上启用 Developer Mode；在 Xcode 选择真实设备后 **Command + R** 构建运行。
6. 用免费 Apple 账号进行个人开发签名可能有有效期、设备或功能限制；**不等于永久安装，也不等于可分发给所有粉丝**。

## B. 发布者打包 IPA（在自己的 Mac 完成）

- 首先在 **Xcode 27.1+** 中验证 Debug/Release 编译以及 Duo 外屏、内屏、旋转、状态栏和 WebDAV。
- Xcode 选择可归档的 iOS 目的地，使用菜单 **Product → Archive**。
- 在 **Window → Organizer → Archives** 选择归档，点击 **Distribute App**。当前 Xcode 具体选项依账号和版本不同：开发/调试或 Ad Hoc 导出都会受签名证书和设备注册限制。
- 成功导出后才会出现 `.ipa` 文件；本仓库**没有假冒的 IPA**，也不要将源码 ZIP 改名为 `.ipa`。
- 想让粉丝在他们各自设备上自行重签 IPA，需要用户自行选择合规工具与方法，成功与否取决于他们的系统版本、签名资格、IPA 内的 Entitlements 和包内容；**不保证每台手机都能直接安装**。
- 不要把 `.p12`、Apple 私钥、`*.mobileprovision`、账号密码或密钥嵌入 GitHub 发布资产。
- 建议 GitHub Releases 同时提供**源码 ZIP**与经过测试的**IPA**（如果已合法导出）。若你希望更顺畅地面向普通用户安装，符合资格后可考虑 TestFlight。

## C. 发布前核对

- [ ] Xcode 真正完成编译与真机运行，不只是 Swift 语法检查
- [ ] 已设置自己的 Team 与 Bundle ID
- [ ] 已添加你自己设计并拥有权利的 App Icon（当前 Assets 内是空位）
- [ ] 外屏四方向、内屏及半折叠相关姿态均做过实际测试
- [ ] 状态栏、摄像头、铰链位置以及字幕/视频比例没有明显问题
- [ ] 在真实 WebDAV 测试服务器上验证 HTTPS 连接、目录遍历、下载与取消
- [ ] GitHub 仓库里没有测试账号、签名证书、秘密、私人影片
- [ ] Release 明确列出本次仍不支持的功能和已知问题
- [ ] 安装说明没有宣称“无需签名直接安装”

## D. Apple 官方资料

- https://developer.apple.com/documentation/xcode/distributing-your-app-for-beta-testing-and-releases
- https://developer.apple.com/documentation/xcode/distributing-your-app-to-registered-devices
