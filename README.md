<p align="center">
  <img src="docs/images/logo.svg" alt="cclear logo" width="128" />
</p>

<h1 align="center">cclear</h1>

<p align="center">图形化的 Claude Code 清理与 macOS / Windows Claude Desktop 环境管理工具。</p>

[下载最新安装包](https://github.com/aibayanyu20/cclear/releases/latest)

支持 macOS（Apple 芯片和 Intel 通用）、Windows x64 / ARM64，以及 Linux x64 / ARM64。

## Claude Desktop（macOS / Windows）

全部通过界面点击操作，无需输入终端命令：

- 预览白名单范围、修复缓存或重置本地状态，可单独选择是否包含 Desktop 设置、MCP 配置和日志。
- 先确认、正常退出 Claude，再将文件移动到本机私有备份；支持备份恢复，同名文件不覆盖。
- 保留 Code / Cowork / VM 相关目录、未知目录以及 Claude Code 独立配置，不处理系统凭据存储。
- 设置启动时区、语言、地区格式、应用位置和可选诊断日志；保存方案后点击启动或重启，也可选择清理成功后启动。

macOS 备份位于 `~/Library/Application Support/cclear/backups/`；Windows 备份位于 `%LOCALAPPDATA%\cclear\backups\`。移动到备份不等于释放磁盘空间；文件重置不代表已退出登录。启动设置只影响从 cclear 启动的应用，不修改系统时区、语言或 Claude 的持久偏好；界面语言及子进程行为以 Claude 自身设置为准。

v0.1.4 将 Desktop 功能扩展到 Windows x64 / ARM64，界面与 macOS 一致：

- 兼容传统安装和 MSIX 的 Claude 用户数据目录，仅处理明确白名单中的缓存、登录与本地状态；设置和日志分别勾选。
- 启动设置中点击「自动查找 Claude Desktop」，也可用文件选择框选择应用；保存方案后启动或重启。
- 备份使用 Windows 私有目录权限、原子不覆盖移动和文件 ID 日志恢复；锁定文件、恢复冲突、目录链接异常会明确报错，不静默覆盖数据。
- 仅请求正常退出，不强杀进程。如果 Claude 只缩到托盘，先从托盘退出再点击重试；不会绕过企业策略、修改系统环境或清理凭据管理器。
- AppData 重定向到用户目录之外或需要跨卷移动的环境暂不支持，会安全停止。Claude 实际界面语言、Cowork / VM / 远程子 Agent 是否采用启动配置，以应用自身行为为准。

发布流程包含 Windows 原生临时目录、权限、文件 ID、junction、进程识别和环境变量安全测试；这不等于对每个 Claude 安装版本的真实启停与语言设置都做了验收。

macOS 和 Windows 均保留 Claude Code 清理功能；Linux 暂仅提供 Claude Code 清理。窗口顶部继续不展示品牌 logo 或标题。

## v0.2.0 下载

- [macOS 通用安装包（Apple 芯片 / Intel）](https://github.com/aibayanyu20/cclear/releases/download/v0.2.0/cclear-0.2.0-macos-universal.dmg)
- [Windows x64 安装包](https://github.com/aibayanyu20/cclear/releases/download/v0.2.0/cclear-0.2.0-windows-amd64.exe)
- [Windows ARM64 安装包](https://github.com/aibayanyu20/cclear/releases/download/v0.2.0/cclear-0.2.0-windows-arm64.exe)

更多平台文件与更新说明见 [v0.2.0 发布页](https://github.com/aibayanyu20/cclear/releases/tag/v0.2.0)。

## Claude Code 环境与 IP 自动同步（v0.2.0）

macOS / Windows 都在界面中点击操作，不要求用户编写命令或填写 IP：

- 「环境设置」合并用户 `settings.json` 的 `env.TZ / LANG / LC_ALL`，保留其他配置；相同值不重复写入、不增加备份。支持预览和恢复最近修改，不改系统时区或语言。
- macOS 可导入现有简单 zsh `claude` alias，并在勾选迁移、确认后备份移除原行，不重复追加。建议先迁移 alias，再同步其他地区，避免两处设置冲突。
- 「IP 自动同步」默认自动获取公网出口 IP、地区和时区建议。优先读取 Code 代理，再检查系统静态 HTTPS 代理；手动代理与预期 IP 核对放在默认收起的高级设置。无需手动提供 IP。
- 允许联网后，通过 ipify 与 AWS 的 IPv4 回显交叉核对，再将观察到的 IP 发送给 ipwho.is 查询时区。保存前重新检测、确认后再次核对出口；不一致或代理失败则停止，不静默绕过代理。
- 无显式代理时只能显示当前网络出口；需主动确认 TUN/VPN 路径或通过可选预期 IP 核对后才能同步。PAC/WPAD、SOCKS-only 和分流歧义不自动猜测。
- 语言按国家提供默认建议，多语言/未知地区保留现有语言。定位误差、域名/进程分流和 IPv6 会造成差异，不保证 Claude API 也从相同 IP 出口，不承诺“万无一失”。
- Code 清理默认保留已保存的三个时区/语言键；取消保留则完整重置。其他认证、代理、权限等配置仍按清理范围处理，私有配置备份不随 Code 清理删除。

仅用户允许并点击后才联系上述服务；不会发送 Claude Token、账号或会话。原始配置备份可能含敏感内容，保存在本机私有目录。窗口顶部仍不显示品牌 logo 或标题。

## Claude Code

清理范围与 `claudego clear -h` 一致，保留项目、历史记录、skills 和插件文件。Code 页默认点击「一键清理」会永久删除 Claude 的全局配置、文件凭据、会话标记、缓存和配置备份，并重置 MCP、权限、hooks 和插件启用配置等全局设置。执行前请退出 Claude，并备份需要保留的设置。此操作不清理系统 Keychain，不代表所有登录会话均已退出。

v0.1.2 恢复正式清理功能，更新成功、无需清理及失败结果反馈，并移除窗口顶部的 logo 和标题。旧版 v0.1.0 / v0.1.1 是模拟清理版本。
