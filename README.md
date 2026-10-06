# cclear

一键清理缓存和残留文件的小工具。一个圆环按钮，点一下就开始，清完给你看释放了多少空间。

- 原生界面，窗口只有 320×372，macOS 上是磨砂背景
- 单文件二进制，约 10 MB，空闲时不占 CPU
- 支持 macOS、Windows 和 Linux

## 下载

到 [Releases](https://github.com/aibayanyu20/cclear/releases/latest) 页面下载对应平台的安装包：

| 平台 | 文件 |
|---|---|
| macOS（Apple 芯片和 Intel 通用） | `cclear-<版本>-macos-universal.dmg` |
| Windows x64 | `cclear-<版本>-windows-amd64.exe` |
| Windows ARM64 | `cclear-<版本>-windows-arm64.exe` |
| Debian / Ubuntu | `cclear_<版本>_amd64.deb` 或 `cclear_<版本>_arm64.deb` |
| 其他 Linux | `cclear-<版本>-linux-<架构>.tar.gz`，解压后运行 `sh install.sh` |

macOS 安装包暂未经过 Apple 公证，首次打开请在应用上右键选择「打开」。Windows 安装包暂未签名，SmartScreen 提示时选择「仍要运行」。

## 清理什么

| 平台 | 清理项目 |
|---|---|
| macOS | 应用缓存、日志、开发工具缓存（npm、pnpm、bun、cargo）、Xcode 构建产物、下载目录里的安装包、废纸篓 |
| Windows | 临时文件、开发工具缓存、下载目录里的安装包 |
| Linux | 应用缓存、开发工具缓存、下载目录里的安装包、回收站 |

除了废纸篓和回收站本身会被清空，其他文件都是移到废纸篓，可以恢复。

## 反馈

遇到问题或有建议，请到 [Issues](https://github.com/aibayanyu20/cclear/issues) 提交。

## 许可

cclear 是免费软件，源码不公开。使用条款见 [LICENSE.md](LICENSE.md)。
