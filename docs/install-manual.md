# 商店下载失败，怎么手动安装 Vivid Player？

[← 返回帮助首页](../README.md)

Vivid Player 只在微软商店发布，没有单独的 EXE 安装包。如果商店一直下载或安装失败，可以从微软商店的服务器手动下载安装包来装。

> **注意**：先在微软商店里点过一次「免费试用」或「购买」，再用这个方法安装。否则装好后会因为没有许可证而打不开。

## 1. 下载安装包

1. 打开 https://store.rg-adguard.net/ （第三方网站，用来生成商店安装包的下载链接，文件本身直接从微软服务器下载）。
2. 左侧下拉框保持默认的 **URL (link)**，中间输入框填 `https://apps.microsoft.com/detail/9PF8WT09D2NT`，右侧选 **RP**，点 ✓。
3. 在结果列表里下载下面 **3 个文件**。普通电脑选带 `x64` 的，ARM 电脑（比如骁龙笔记本）选带 `arm64` 的。版本号以列表里最新的为准：

| 文件名（示例） | 作用 |
|---|---|
| `Microsoft.VCLibs.140.00.UWPDesktop_14.0.xxxxx.0_x64__8wekyb3d8bbwe.appx` | 运行库 |
| `Microsoft.WindowsAppRuntime.1.8_8000.xxx.xxxx.0_x64__8wekyb3d8bbwe.msix` | 运行库 |
| `43612cjw1115.VividPlayer_x.x.x.0_x64__6ey2ky5vtg2yj.msix` | Vivid Player 本体 |

列表里以 `.BlockMap` 结尾的文件不用下载。

## 2. 安装

按下面的顺序依次双击安装：**先装两个运行库，最后装 Vivid Player**。运行库如果提示「已安装」或「已安装更高版本」，直接跳过就行。

如果双击后没有出现安装窗口，就在文件所在文件夹的空白处按住 Shift 再右键 →「在终端中打开」/「在此处打开 PowerShell 窗口」，按顺序执行（文件名换成你实际下载的）：

```
Add-AppxPackage .\Microsoft.VCLibs.140.00.UWPDesktop_xxx.appx
Add-AppxPackage .\Microsoft.WindowsAppRuntime.1.8_xxx.msix
Add-AppxPackage .\43612cjw1115.VividPlayer_xxx.msix
```

装好后在开始菜单打开「Vivid Player」。以后的版本更新仍然由微软商店自动完成。

> 原文：[如何通过安装包安装 Vivid Player（B 站）](https://www.bilibili.com/opus/1216745122417344533)
