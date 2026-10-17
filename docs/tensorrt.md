# 插帧提示「TensorRT 组件下载失败，使用 DirectML」怎么办？

[← 返回帮助首页](../README.md)

## 这是怎么回事

插帧的 TensorRT 后端（NVIDIA RTX 显卡专用）要用到微软的一个系统组件：**Windows ML NVIDIA TensorRT-RTX Execution Provider**。这个组件 Vivid Player 没有自带，第一次使用时由 Windows 通过 **Windows Update** 自动下载（对应更新 KB5128776）。

不少用户的电脑上这一步会失败，比如 Windows Update 被关闭或被公司策略管控、网络连不上微软的下载服务器、Windows 版本较旧等。失败后播放器会自动退回 DirectML 继续插帧，只是速度慢一些，不影响正常播放。

这种情况可以手动安装这个组件，装好后 TensorRT 就能用了。

## 下载

到 [Releases 页面](https://github.com/cjw1115/Vivid-Player/releases/tag/trt-rtx-ep) 下载下面这个文件：

| 文件 | 大小 | SHA256 |
|---|---|---|
| `NvTensorRtRtxEP.1.8.24.0.msix` | 约 71 MB | `266121509BFAEEB6680DD1D65B01BDC54B94D446BBE8640BA76B823BCC2147D1` |

这个文件就是 Windows Update 下发的微软原版安装包，带有 **Microsoft Corporation** 的数字签名，没有任何改动。你可以在文件上右键 →「属性」→「数字签名」里看到签名，也可以用下面这条命令核对 SHA256：

```
Get-FileHash .\NvTensorRtRtxEP.1.8.24.0.msix
```

> 仅适用于 x64 的 Windows 11，并且需要 NVIDIA RTX 显卡。

## 安装

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

如果提示「已安装更高版本」，说明 Windows Update 已经帮你装过更新的版本，不需要再装。如果装完还是不行，请按 [怎么抓日志](logs.md) 抓一份日志，发到 demoapp_dev@hotmail.com。
