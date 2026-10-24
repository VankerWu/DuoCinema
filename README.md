# DuoCinema 🎬

<img src="DuoCinema/Assets.xcassets/AppIcon.appiconset/AppIcon.png" width="120" alt="DuoCinema App Icon" />

**为折叠屏打造的独立 iOS 播放器｜公开源码预览版**

DuoCinema 是一款从零设计的 SwiftUI 影音播放器实验项目。它尝试充分利用 iPhone Duo 的外屏、内屏与折叠姿态：影片占据主要画面，另一块区域作为控制台，并通过实时的镜像反射营造影院氛围。项目也支持本地文件、HTTPS 媒体直链与多个 WebDAV/NAS 媒体目录。

> **项目状态：预览版 v0.18.0（开发迭代 V1.8）。** 源码已做静态语法检查，但**尚未在 Xcode 27.1 完成正式归档、八方向设备兼容性及真实 WebDAV 实测**。功能可能不稳定，不建议存放唯一一份重要文件。

## 已实现的功能

- **Duo 自适应显示**：按系统提供的折叠保留区域调整布局；支持外屏与内屏不同姿态。
- **影院模式**：支持影片原始比例 / 裁切铺满切换；需要时可主动进入隐藏状态栏的全屏模式。
- **折叠控制台**：半折叠时采用上下或左右两块区域；支持暂停、前后跳转 10 秒、进度拖动、倍速、静音。
- **动态镜像倒影**：折叠分屏的控制区域可显示同步反向画面特效。特效仍需针对真机调校。
- **本地与网络**：文件 App 文件选择；AVPlayer 支持的 HTTPS 视频/HLS 直链。
- **WebDAV/NAS（早期版）**：支持保存多个 HTTPS WebDAV 挂载、文件夹浏览、当前目录搜索、显示下载进度并取消；登录密码使用系统 Keychain 保存。

## 目前不支持

- WebDAV **边播边缓存**、远程任意拖动进度；WebDAV 文件需要**先下载缓存再播放**。
- SMB 协议原生浏览、阿里云盘或百度网盘原生账号登录、Jellyfin / Emby API 接入。
- MKV/AVI 等扩展格式的全格式解码、所有字幕/音轨的选择与管理。
- 承诺所有 Duo 姿态与所有片源绝对无裁切；比例模式可以由用户切换。

## 运行环境

- 建议 **Xcode 27.1 或更新版本**，iPhone Duo 相关接口需相应 SDK。
- App 最低 iOS 17；Duo 折叠区域读取仅在 iOS 27.1 或以上系统启用。
- 使用苹果系统框架：SwiftUI、AVKit、Security、Foundation/URLSession 等，**没有引入第三方代码库或商业播放器 SDK**。

## 安装（推荐：自行编译签名）

1. 下载本仓库的源码 ZIP 并解压。
2. 双击 `DuoCinema.xcodeproj`，使用 Xcode 打开。
3. 选中左侧 **DuoCinema Target → Signing & Capabilities**，选择自己的 Team。
4. 把 **Bundle Identifier** 从演示用的 `com.example.duocinema` 改成自己独有的 ID（例如 `com.yourname.duocinema`）。
5. 选择可用的 iPhone / Duo 模拟器或自己的手机，按 **Command + R**。

没有开发者付费账号也可以尝试用个人 Apple 账号对**自己的设备**开发签名；有设备数量、有效期和功能限制。有关分发与 IPA 的差异，请参阅 [签名和 IPA 教程](docs/BUILD_AND_SIGN.md)。

## 发布下载

请从右侧 **Releases** 下载你信任的官方预览版本。如果暂时没有 Release，说明尚未提供经过验证的 IPA：**源码仓库本身不是 IPA 安装包**。切勿下载来源不明的重签包。

## 隐私与网络访问

- 服务器地址、用户名和挂载列表保存在设备的本地 App 数据中；WebDAV 密码使用 iOS Keychain。
- 播放 WebDAV 文件时，App 会向**你配置的 WebDAV 服务器**发送登录信息及访问请求，并把文件缓存到本地。
- 本项目源码未加入广告 SDK、用户行为统计 SDK 或自有云端收集服务。
- 参阅 [隐私说明](PRIVACY.md)。

## 原创性与许可证

项目界面和应用逻辑独立设计，未引入第三方播放器的源码、界面素材、商标或受版权保护的电影片段。部分代码在 AI 辅助下编写，已进行**仓库级的依赖和敏感信息检查**，但这不等同于任何第三方版权的完整法律保证。欢迎在 MIT License 下使用、学习与贡献；参阅 [原创性审查记录](docs/ORIGINALITY_CHECKLIST.md)。

**DuoCinema 非 Apple 官方产品，不隶属或获得 Apple 认可。** iPhone 等名称属于各自权利人。示意截图和测试视频必须由贡献者确保有权公开。

## 反馈与贡献

在 GitHub 的 Issues 中反馈时，请说明：设备、iOS 版本、折叠姿态、预期和实际表现，并**遮挡个人云盘地址、账号、密码、视频私人信息**。参阅 [贡献指南](CONTRIBUTING.md) 和 [安全政策](SECURITY.md)。

---

**English:** DuoCinema is an independently developed, source-available SwiftUI media-player preview focused on foldable-screen interactions. Supports local files, HTTPS media URLs and early WebDAV mounting (download-before-play). Experimental; not affiliated with Apple. MIT licensed. See docs for build/signing instructions.
