# Bili Market 价格终端（Windows 客户端）

本仓库只提供可直接运行的 Windows x64 客户端，**不提供项目源码、个人数据库或账号凭据**。

## 下载和使用

1. 下载仓库中的 `BiliMarketPriceMonitor.exe` 与 `manifest.sha256`，放在**同一目录**。也可通过 GitHub Releases 发布这两个文件，供用户从 Releases 下载。
2. Windows 10/11 安装 Microsoft Edge WebView2 Runtime（多数系统已自带），双击 EXE 启动；无需安装 Python 或 Node.js。
3. 首次运行如遇 Windows SmartScreen「未知发布者」，请先确认下载来源和校验值，再自行决定是否运行。本版本未进行 Authenticode 数字签名，SHA-256 清单不是发布者签名。
4. 默认关闭窗口会隐藏到系统托盘，继续监测；右键托盘图标选择退出，才会停止监测。

## 完整性核验

同目录的 `manifest.sha256` 记录该 EXE 的 SHA-256；Windows PowerShell 可执行：

```powershell
(Get-FileHash .\BiliMarketPriceMonitor.exe -Algorithm SHA256).Hash
```

本次发布文件的 SHA-256：

```text
7e62793ff653b9bd6afbf085a85c0627b3fe7b9e34cf21985e8bd3cf232bc6d7
```

应与 `manifest.sha256` 中的值一致。**更换、重建或签名 EXE 后必须重新生成清单并更新这里的值。**哈希只能检查文件与这份清单一致，无法证明发布者身份。

## 数据与隐私

客户端在本机查询 B 站市集接口，关注列表、价格历史、设置和通知默认保存在 `%LOCALAPPDATA%\BiliMarket\data\monitor.db`；旧版本或自定义路径可能不同。手机推送功能使用用户自行填写的 PushPlus Token 或企业微信群机器人 Webhook。**不要把数据库、凭据或含有个人信息的配置上传到 GitHub。**

## 上传提示

此文件夹应仅包含 `README.md`、`BiliMarketPriceMonitor.exe`、`manifest.sha256` 三个文件。可以在 GitHub 创建空仓库后直接上传这三个文件；仓库内容对公众可见时，任何人都可以下载 EXE。若用 Git 命令上传，请仅在这个文件夹执行 `git init` 和 `git add .`，并在提交前检查 `git status --short`。不要上传旁边的原项目文件夹或备份。GitHub 可能根据仓库或文件大小限制拒绝网页上传；此 EXE 约 21.3 MiB。

> 只发布 EXE 不等于源码完全无法被分析；本程序是 Python 打包客户端，可被逆向分析。本项目为非官方价格观察工具，请合理使用并遵守相关平台规则。
