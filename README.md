# 造梦西游 · iOS 原生版（自动编译 ipa）

这个仓库只做一件事：**用 GitHub 免费的 macOS 机器，把你上传的工程编译成 ipa**。
不需要 Mac，也不需要装 Xcode。

## 两个动作

### ① 上传工程

GitHub 网页右上 **Add file → Upload files**，把 `造梦西游-iOS原生工程.zip` 拖进去 → Commit。

### ② 把构建脚本放到正确位置

打开 [`ci/build.yml`](ci/build.yml) → 右上铅笔（Edit）→ 把顶部路径从 `ci/build.yml`
改成 `.github/workflows/build.yml` → Commit。

GitHub 会自动开始编译。

## 拿 ipa

顶栏 **Actions** → 最新的 `Build IPA` → 跑完（约 5~10 分钟）→ 页面底部 **Artifacts** →
下载 `ZMXY-unsigned-ipa` → 解压得 `ZMXY-unsigned.ipa`。

未签名的包，用 Sideloadly / AltStore 填自己的 Apple ID 重签即可安装。

## 工程里有什么

- `ZMXY.xcodeproj` — 含 scheme，可双击打开
- `Sources/GameScene.swift` — SpriteKit 游戏主体（842 行）
- `Sources/GameViewController.swift` — SKView，60fps
- `Sources/www/assets/` — 原版 APK 素材：216 张精灵表、204 条动画、技能图标、背景
- 22 个角色族 / 每 5 波 Boss / 每 3 波三选一强化卡

## 编译报错怎么办

把 Actions 日志里的 `error:` 行贴进对话，我按报错改源码。
