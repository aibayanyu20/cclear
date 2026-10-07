<p align="center">
  <img src="docs/images/logo.svg" alt="cclear logo" width="128" />
</p>

<h1 align="center">cclear</h1>

<p align="center">一个简洁的 Claude Code Cli 一键清理本地环境的工具。</p>

[下载最新安装包](https://github.com/aibayanyu20/cclear/releases/latest)

支持 macOS（Apple 芯片和 Intel 通用）、Windows x64 / ARM64，以及 Linux x64 / ARM64。

清理范围与 `claudego clear -h` 一致，保留项目、历史记录、skills 和插件文件。默认点击「一键清理」会永久删除 Claude 的全局配置、文件凭据、会话标记、缓存和配置备份，并重置 MCP、权限、hooks 和插件启用配置等全局设置。执行前请退出 Claude，并备份需要保留的设置。此操作不清理系统 Keychain，不代表所有登录会话均已退出。

v0.1.2 恢复正式清理功能，更新成功、无需清理及失败结果反馈，并移除窗口顶部的 logo 和标题。旧版 v0.1.0 / v0.1.1 是模拟清理版本。
