# Vivid Player 帮助

遇到问题时，下面的方法能帮你和我们更快地把它解决。反馈请发到 demoapp_dev@hotmail.com。

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
