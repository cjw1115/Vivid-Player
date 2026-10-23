# 115 应用 ID 参考 / App ID reference

Vivid Player 添加 115 源时，由你填写应用 ID，再使用 115 App 扫码并确认授权。应用内不预填或自动选择 ID。

## 使用方法

1. 在 Vivid Player 的自定义源中选择 **115**。
2. 填入你选择的应用 ID，然后点击 **用 115 扫码**。
3. 用 115 App 扫描二维码，核对手机显示的应用名称和权限，确认后完成添加。

应用 ID 会随该源保存；刷新令牌通过系统凭据库保存。修改应用 ID 后，需要重新扫码授权，或填写该 ID 对应的刷新令牌。

## 公开资料中的应用 ID

以下为 [Muvyo 云盘接入教程](https://doc.mediavault.qzz.io/docs#step-cloud-drive)于 **2026-10-24** 收录的对应关系。这是一份公开资料索引，不表示这些应用向 Vivid Player 提供了授权或合作。名称与可用状态以 115 授权页面为准；未逐项验证所有 ID。

| App ID | 应用名称 / Application |
| --- | --- |
| `100195313` | CloudDrive2 |
| `100195161` | SenPlayer |
| `100195137` | VidHub |
| `100195145` | Filebar |
| `100195135` | 爆米花 |
| `100195129` | 飞牛 |
| `100195123` | Doge |
| `100195125` | 多珀媒体播放器 |
| `100195127` | 蒙太奇播放器 |
| `100195131` | 腾飞Webos |
| `100195133` | 恒星播放器 |
| `100195139` | 艾索洛HIFI播放器 |
| `100195141` | 纵道软件 |
| `100195143` | 云上生活 |
| `100195147` | CineUltra |
| `100195149` | DS Cloud |
| `100195151` | PurePhoto |
| `100195153` | BoxPlayer |
| `100195155` | Conflux Player |
| `100195157` | 大学生资源网 |
| `100195159` | media saber |

手机上的“已经过 115 生活认证”提示对应所填 ID 的注册应用，不代表 Vivid Player 已通过认证。若 ID 无法获取二维码或授权失败，可核对输入、重新扫码，或使用你自己在 [115 开放平台](https://open.115.com/)申请的应用 ID。

## English

Select **115** when adding a custom source, enter an App ID, then select **Scan with 115**. Scan the QR code in the 115 app and review the displayed application name and permissions before confirming.

The table reproduces the ID/name mappings listed in the linked public tutorial on **2026-10-24**. It does not establish permission to use another application's identity or a partnership with Vivid Player. Names and availability are determined by 115; not every ID has been tested. A certification message on your phone refers to the application registered under the entered ID.

Vivid Player does not preselect an ID. The source remembers your entry and stores its refresh token in the system credential vault. Changing the ID requires fresh authorization or a refresh token issued for that ID. You can also apply for your own App ID through the [115 Open Platform](https://open.115.com/).
