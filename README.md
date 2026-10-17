<p align="center">
  <img src="docs/images/logo.svg" alt="cclear logo" width="128" />
</p>

<h1 align="center">cclear</h1>

<p align="center">图形化的 Claude Code 清理与 macOS Claude Desktop 环境管理工具。</p>

[下载最新安装包](https://github.com/aibayanyu20/cclear/releases/latest)

支持 macOS（Apple 芯片和 Intel 通用）、Windows x64 / ARM64，以及 Linux x64 / ARM64。

## macOS Claude Desktop（v0.1.3 新增）

全部通过界面点击操作，无需输入终端命令：

- 预览白名单范围、修复缓存或重置本地状态，可单独选择是否包含 Desktop 设置、MCP 配置和日志。
- 先确认、正常退出 Claude，再将文件移动到本机私有备份；支持备份恢复，同名文件不覆盖。
- 保留 Code / Cowork 相关目录、未知目录以及 Claude Code 独立配置，不清理 Keychain。
- 设置启动时区、语言、地区格式、应用位置和可选诊断日志；保存方案后点击启动或重启，也可选择清理成功后启动。

备份位于 `~/Library/Application Support/cclear/backups/`。移动到备份不等于释放磁盘空间；文件重置不代表已退出登录。启动设置只影响从 cclear 启动的应用，不修改系统时区、语言或 Claude 的持久偏好；界面语言及子进程行为以 Claude 自身设置为准。

Desktop 功能仅在 macOS 显示；Windows 和 Linux 保留 Claude Code 清理功能。窗口顶部不展示品牌 logo 或标题。

## Claude Code

清理范围与 `claudego clear -h` 一致，保留项目、历史记录、skills 和插件文件。Code 页默认点击「一键清理」会永久删除 Claude 的全局配置、文件凭据、会话标记、缓存和配置备份，并重置 MCP、权限、hooks 和插件启用配置等全局设置。执行前请退出 Claude，并备份需要保留的设置。此操作不清理系统 Keychain，不代表所有登录会话均已退出。

v0.1.2 恢复正式清理功能，更新成功、无需清理及失败结果反馈，并移除窗口顶部的 logo 和标题。旧版 v0.1.0 / v0.1.1 是模拟清理版本。
