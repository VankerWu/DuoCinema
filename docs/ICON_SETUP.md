# App 图标安装与排查

`DuoCinema/Assets.xcassets/AppIcon.appiconset/AppIcon.png` 为 1024×1024 RGB 图标，`Contents.json` 将它声明为 iOS Universal App Icon。Xcode Build Settings 的 `ASSETCATALOG_COMPILER_APPICON_NAME` 必须是 `AppIcon`。

## 为什么模拟器出现白色网格占位符？
通常是当前 Xcode 工程尚未导入图标，或运行的是此前单独创建的 `MyApp` 工程，而不是这个带 Assets 的 `DuoCinema.xcodeproj`。

1. 双击打开此仓库中的 `DuoCinema.xcodeproj`（不要使用旧 `MyApp.xcodeproj`）。
2. 左侧检查 `DuoCinema > Assets.xcassets > AppIcon` 预览能看到用户设计的黑白图标。
3. 点击 App Target 的 General / Build Settings，确认 App Icon Source / Asset Catalog App Icon Set Name = `AppIcon`。
4. `Product > Clean Build Folder`（Shift+Command+K）。
5. 在 iPhone Duo 模拟器删除旧 DuoCinema App，再从 Xcode 重新运行。

**如果必须沿用你正在开发的 MyApp 工程**，从这个仓库复制整个 `AppIcon.appiconset` 到那个工程的 `Assets.xcassets`，并执行步骤 3–5。仅复制 `ContentView.swift` 不会复制 App 图标。

本仓库仅静态核对图标尺寸、颜色通道、Contents.json、project.pbxproj 与 Info.plist；没有使用 Xcode 实际编译。
