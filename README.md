# Vivid Player

面向 Windows 的高性能视频播放器，基于 WinUI 3（.NET 8）+ 自研 C++ 媒体引擎，以 MSIX 形式分发。

> Vivid Player is a high-performance Windows video player built on WinUI 3 (.NET 8) with a self-developed C++ media engine, distributed as an MSIX package.

## 特性 Features

- **全格式 / 全编码**：基于 FFmpeg 的自研引擎，容器与编码通吃（AVC / HEVC / VP8-9 / AV1 …），软解 + D3D11VA 零拷贝硬解。
- **HDR**：HDR10 / HLG / Dolby Vision / HDR Vivid 色调映射，跟随显示器峰值与 SDR/HDR 自适应。
- **音频**：多音轨切换；AC3 / DTS / TrueHD 及 Dolby Atmos（对象 / 声道床）比特流直通与空间音效。
- **字幕**：内嵌与外挂字幕（ASS / SRT / VTT / PGS…），可视化样式编辑，libass 渲染。
- **资源库**：本地媒体扫描入库、封面抽帧、续播记录、TMDB 刮削。
- **网络源**：SMB / WebDAV / Jellyfin，以及在线直播与点播。
- **蓝光原盘**：ISO / BDMV 识别与播放。
- **其它**：倍速、截图、画中画、小窗、画面旋转与缩放、多语言界面。

## 支持与反馈 Support

遇到问题需要我们排查时，请参考问答文档按步骤操作：

- **[常见问题问答（抓日志 / 抓 Dump / 如何反馈）](docs/support-qa.md)**
- 崩溃转储注册表文件：[启用](docs/support/启用崩溃转储.reg) · [关闭](docs/support/关闭崩溃转储.reg)

## 系统要求 Requirements

- Windows 10 版本 19041（20H1）及以上，x64。

---

© Vivid Player. 保留所有权利。第三方组件许可见随附的 THIRD-PARTY-NOTICES。
