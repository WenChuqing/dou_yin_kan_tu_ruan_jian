# 抖音式看图 Android 应用

一个模仿抖音交互方式的看图应用，支持上下滑动浏览图片和视频，左右滑动切换文件夹。

## 功能特性

### 核心功能
- ✅ **抖音式上下滑动**：全屏浏览图片和视频，垂直滑动切换
- ✅ **左右滑动切换文件夹**：水平滑动切换不同的图片文件夹
- ✅ **双击点赞**：双击屏幕点赞，显示心形动画
- ✅ **长按删除**：长按弹出删除确认对话框
- ✅ **视频自动播放**：视频自动循环播放（默认静音）
- ✅ **多媒体格式支持**：JPG、PNG、WEBP、MP4等常见格式

### 技术特性
- ✅ **MVVM 架构**：清晰的代码分层
- ✅ **ViewPager2**：高性能滑动体验
- ✅ **ExoPlayer**：专业视频播放
- ✅ **Glide**：高效图片加载
- ✅ **Kotlin Flow**：响应式数据流
- ✅ **ViewBinding**：类型安全的视图绑定
- ✅ **Coroutines**：异步处理支持

## 技术栈

- **语言**: Kotlin
- **最低 SDK**: 26 (Android 8.0)
- **目标 SDK**: 34 (Android 14)
- **架构**: MVVM
- **UI**: View体系 + ViewPager2
- **图片加载**: Glide
- **视频播放**: ExoPlayer (Media3)
- **异步处理**: Kotlin Coroutines + Flow
- **权限处理**: AndroidX Permission

## 项目结构

```
app/
├── src/main/
│   ├── java/com/douyin/photoapp/
│   │   ├── ui/
│   │   │   ├── MainActivity.kt          # 主Activity
│   │   │   ├── MediaPagerAdapter.kt     # 媒体Pager适配器
│   │   │   └── FolderPagerAdapter.kt    # 文件夹Pager适配器
│   │   ├── viewmodel/
│   │   │   └── MediaViewModel.kt        # 媒体ViewModel
│   │   ├── repository/
│   │   │   └── MediaRepository.kt       # 数据仓库
│   │   ├── model/
│   │   │   ├── MediaItem.kt             # 媒体项模型
│   │   │   └── MediaFolder.kt           # 媒体夹模型
│   │   ├── player/
│   │   │   └── ExoPlayerManager.kt      # ExoPlayer管理器
│   │   └── utils/
│   │       ├── MediaLoader.kt           # 媒体加载工具
│   │       └── PermissionHelper.kt      # 权限处理工具
│   └── res/
│       ├── layout/
│       │   ├── activity_main.xml        # 主布局
│       │   ├── item_media.xml           # 媒体项布局
│       │   └── item_folder_tab.xml      # 文件夹tab布局
│       ├── drawable/
│       ├── values/
│       └── xml/
└── build.gradle.kts
```

## 快速开始

### 环境要求
- Android Studio Hedgehog (2023.1.1) 或更高版本
- JDK 17
- Android SDK 34

### 构建步骤

1. **克隆项目**
```bash
git clone <repository-url>
cd 抖音看图_完整版
```

2. **使用 Android Studio 打开**
```
File -> Open -> 选择项目目录
```

3. **同步 Gradle**
等待 Android Studio 自动同步 Gradle 依赖

4. **连接设备或启动模拟器**
确保已连接 Android 设备或启动 AVD 模拟器

5. **运行应用**
点击 Run 按钮或使用快捷键 `Shift + F10`

### 命令行构建

```bash
# Debug 构建
./gradlew assembleDebug

# Release 构建
./gradlew assembleRelease

# 安装到设备
./gradlew installDebug
```

## 权限说明

应用需要以下权限：

| 权限 | 用途 |
|------|------|
| `READ_MEDIA_IMAGES` | 读取设备中的图片文件 (Android 13+) |
| `READ_MEDIA_VIDEO` | 读取设备中的视频文件 (Android 13+) |
| `READ_EXTERNAL_STORAGE` | 读取外部存储 (Android 12-) |
| `WRITE_EXTERNAL_STORAGE` | 删除媒体文件 (Android 12-) |

首次启动时会请求存储权限，请授予权限以正常使用应用功能。

## 使用说明

### 基本操作
- **上下滑动**：切换当前文件夹中的图片/视频
- **左右滑动**：切换不同的文件夹
- **双击屏幕**：点赞/取消点赞，显示心形动画
- **长按屏幕**：弹出删除确认对话框
- **右侧按钮**：点赞和删除快捷按钮

### 视频播放
- 视频会自动开始播放
- 默认静音播放
- 循环播放视频
- 滑出屏幕时自动停止

### 文件夹分类
- "全部媒体"：包含所有图片和视频，按时间倒序排列
- 其他文件夹：按系统相册文件夹分类

## GitHub Actions CI/CD

项目包含 GitHub Actions 工作流配置，每次提交到 `main` 分支或 PR 都会自动构建 APK。

### 工作流文件
`.github/workflows/android.yml`

### 构建产物
- APK 文件位置：`app/build/outputs/apk/debug/app-debug.apk`
- GitHub Actions 会自动上传 APK 作为构建产物

## 常见问题

### Q: 应用启动后显示空白？
A: 请确保已授予存储权限，重启应用即可。

### Q: 视频无法播放？
A: 请检查视频格式是否为 MP4，确保文件未损坏。

### Q: 构建失败？
A: 请检查：
1. JDK 版本是否为 17
2. Android SDK 34 是否已安装
3. Gradle 同步是否完成

### Q: 找不到图片？
A: 应用从系统 MediaStore 读取媒体文件，请确保设备中有图片。

## 版本历史

### v1.0.0 (2024)
- 初始版本发布
- 实现抖音式上下滑动浏览
- 实现左右滑动切换文件夹
- 实现双击点赞和长按删除
- 集成 ExoPlayer 视频自动播放
- 完整的 MVVM 架构

## 许可证

```
Copyright 2024

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

## 贡献

欢迎提交 Issue 和 Pull Request！

---

**Enjoy browsing photos and videos TikTok-style! 🎉**
