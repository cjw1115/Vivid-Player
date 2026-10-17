# Vivid Player 帮助

遇到问题时，下面的方法能帮你和我们更快地把它解决。反馈请发到 demoapp_dev@hotmail.com。

---

## 商店下载失败，怎么手动安装 Vivid Player？

Vivid Player 只在微软商店发布，没有单独的 EXE 安装包。如果商店一直下载或安装失败，可以从微软商店的服务器手动下载安装包来装。

> **注意**：先在微软商店里点过一次「免费试用」或「购买」，再用这个方法安装。否则装好后会因为没有许可证而打不开。

### 1. 下载安装包

1. 打开 https://store.rg-adguard.net/ （第三方网站，用来生成商店安装包的下载链接，文件本身直接从微软服务器下载）。
2. 左侧下拉框保持默认的 **URL (link)**，中间输入框填 `https://apps.microsoft.com/detail/9PF8WT09D2NT`，右侧选 **RP**，点 ✓。
3. 在结果列表里下载下面 **3 个文件**。普通电脑选带 `x64` 的，ARM 电脑（比如骁龙笔记本）选带 `arm64` 的。版本号以列表里最新的为准：

| 文件名（示例） | 作用 |
|---|---|
| `Microsoft.VCLibs.140.00.UWPDesktop_14.0.xxxxx.0_x64__8wekyb3d8bbwe.appx` | 运行库 |
| `Microsoft.WindowsAppRuntime.1.8_8000.xxx.xxxx.0_x64__8wekyb3d8bbwe.msix` | 运行库 |
| `43612cjw1115.VividPlayer_x.x.x.0_x64__6ey2ky5vtg2yj.msix` | Vivid Player 本体 |

列表里以 `.BlockMap` 结尾的文件不用下载。

### 2. 安装

按下面的顺序依次双击安装：**先装两个运行库，最后装 Vivid Player**。运行库如果提示「已安装」或「已安装更高版本」，直接跳过就行。

如果双击后没有出现安装窗口，就在文件所在文件夹的空白处按住 Shift 再右键 →「在终端中打开」/「在此处打开 PowerShell 窗口」，按顺序执行（文件名换成你实际下载的）：

```
Add-AppxPackage .\Microsoft.VCLibs.140.00.UWPDesktop_xxx.appx
Add-AppxPackage .\Microsoft.WindowsAppRuntime.1.8_xxx.msix
Add-AppxPackage .\43612cjw1115.VividPlayer_xxx.msix
```

装好后在开始菜单打开「Vivid Player」。以后的版本更新仍然由微软商店自动完成。

> 原文：[如何通过安装包安装 Vivid Player（B 站）](https://www.bilibili.com/opus/1216745122417344533)

---

## 怎么抓日志？

1. 打开 Vivid Player → 设置，找到「日志」这张卡片。
2. 把右边的「日志级别」改成 Debug（记录更详细，查完可以再改回 Info）。
3. 重新做一遍出问题的操作（比如再打开那个打不开的视频、再复现一次花屏）——先改成 Debug 再复现。
4. 复现完，回到「日志」卡片，点「打开日志文件夹」。
5. 把里面当天日期的文件 vivid-年-月-日.log 发到 demoapp_dev@hotmail.com（如果还有 vivid-年-月-日.previous.log 也一起发）。

日志只包含播放器自己的运行记录，不含账号密码等隐私。

---

## 怎么抓 Dump（崩溃 / 卡死转储）？

### 如果程序卡死、无响应（还在，但点不动）

趁它卡住、先别关：

1. 按 Ctrl + Shift + Esc 打开任务管理器。
2. 在「详细信息」标签页里找到 VividPlayer.App.exe。
3. 右键它 →「创建转储文件」。
4. 弹窗会告诉你文件保存位置，一般是：
   `C:\Users\你的用户名\AppData\Local\Temp\VividPlayer.App.DMP`
5. 这个文件比较大，压缩成 zip 后发到 demoapp_dev@hotmail.com。

抓完就可以关掉卡住的程序了。

### 如果程序一启动就闪退 / 用着自己崩掉

这种一闪就没，需要先让 Windows 在下次崩溃时自动存一份：

1. 双击运行 启用崩溃转储.reg，弹窗点「是」。（导入时会弹 UAC，点「是」即可；如果没有管理员权限，改用上面「卡死」那种任务管理器抓法。）
2. 再打开 Vivid Player，把崩溃的操作重做一遍，让它再崩一次。
3. 打开这个文件夹（把整段路径复制到「文件资源管理器」顶部的地址栏回车即可，其中「你的用户名」换成你自己的）：`C:\Users\你的用户名\AppData\Local\VividPlayer\CrashDumps`
4. 里面会有 VividPlayer.App.exe.<数字>.dmp，压缩后发到 demoapp_dev@hotmail.com。

弄完这次，双击 关闭崩溃转储.reg 即可还原。

---

## 怎么描述问题能更快定位？

发反馈到 demoapp_dev@hotmail.com 时，带上这几条会很有帮助：

1. 哪个文件 / 哪个源：本地文件（什么格式，如 mp4 / mkv / 蓝光原盘）还是网络源（SMB / WebDAV / 在线直播）？
2. 具体现象：花屏 / 黑屏 / 没声音 / 字幕错位 / 卡顿 / 崩溃？发生在打开时、播放中途还是快进跳转后？
3. 能否稳定复现：每次都这样还是偶尔？有固定步骤按 1、2、3 写下来。
4. 环境：Windows 版本、显卡型号；外接显示器 / HDR 屏也注明。

---

## 怎么安装测试包（旁加载 / sideload）？
```
1. 在设置 →「应用」里找到 **Vivid Player** 卸载。
2. 右键测试包里的 `Add-AppDevPackage.ps1` →「使用 PowerShell 运行」，然后按提示继续（中途会弹 UAC，点「是」）。看到安装成功的提示后，去开始菜单打开「Vivid Player」验证。

如果第2步窗口一闪就消失、装不上，先用**管理员身份**打开 PowerShell 执行下面这句，再回到第二步右键运行即可：
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy Bypass -Force
```

---

## 插帧提示「TensorRT 组件下载失败，使用 DirectML」怎么办？

### 这是怎么回事

插帧的 TensorRT 后端（NVIDIA RTX 显卡专用）要用到微软的一个系统组件：**Windows ML NVIDIA TensorRT-RTX Execution Provider**。这个组件 Vivid Player 没有自带，第一次使用时由 Windows 通过 **Windows Update** 自动下载（对应更新 KB5128776）。

不少用户的电脑上这一步会失败，比如 Windows Update 被关闭或被公司策略管控、网络连不上微软的下载服务器、Windows 版本较旧等。失败后播放器会自动退回 DirectML 继续插帧，只是速度慢一些，不影响正常播放。

这种情况可以手动安装这个组件，装好后 TensorRT 就能用了。

### 下载

到 [Releases 页面](https://github.com/cjw1115/Vivid-Player/releases/tag/trt-rtx-ep) 下载下面这个文件：

| 文件 | 大小 | SHA256 |
|---|---|---|
| `NvTensorRtRtxEP.1.8.24.0.msix` | 约 71 MB | `266121509BFAEEB6680DD1D65B01BDC54B94D446BBE8640BA76B823BCC2147D1` |

这个文件就是 Windows Update 下发的微软原版安装包，带有 **Microsoft Corporation** 的数字签名，没有任何改动。你可以在文件上右键 →「属性」→「数字签名」里看到签名，也可以用下面这条命令核对 SHA256：

```
Get-FileHash .\NvTensorRtRtxEP.1.8.24.0.msix
```

> 仅适用于 x64 的 Windows 11，并且需要 NVIDIA RTX 显卡。

### 安装

1. 先关闭 Vivid Player。
2. 双击 `NvTensorRtRtxEP.1.8.24.0.msix`，在弹出的窗口里点「安装」。
3. 如果双击后没有出现安装窗口（有些系统去掉了「应用安装程序」），就在文件所在的文件夹空白处按住 Shift 再右键 →「在终端中打开」/「在此处打开 PowerShell 窗口」，执行：
   ```
   Add-AppxPackage .\NvTensorRtRtxEP.1.8.24.0.msix
   ```
4. 检查是否装好：在 PowerShell 里执行下面这句，能看到 `TRT-RTX.EP.1.8` 这一行就说明成功了：
   ```
   Get-AppxPackage *TRT-RTX* | Select-Object Name, Version
   ```
5. 重新打开 Vivid Player，在插帧里选 TensorRT。第一次使用会「为这块显卡优化」约 10 秒，之后就快了。

如果提示「已安装更高版本」，说明 Windows Update 已经帮你装过更新的版本，不需要再装。如果装完还是不行，请按上面的方法抓一份日志，发到 demoapp_dev@hotmail.com。
