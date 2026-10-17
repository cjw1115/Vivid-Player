# 怎么抓 Dump（崩溃 / 卡死转储）？

[← 返回帮助首页](../README.md)

## 如果程序卡死、无响应（还在，但点不动）

趁它卡住、先别关：

1. 按 Ctrl + Shift + Esc 打开任务管理器。
2. 在「详细信息」标签页里找到 VividPlayer.App.exe。
3. 右键它 →「创建转储文件」。
4. 弹窗会告诉你文件保存位置，一般是：
   `C:\Users\你的用户名\AppData\Local\Temp\VividPlayer.App.DMP`
5. 这个文件比较大，压缩成 zip 后发到 demoapp_dev@hotmail.com。

抓完就可以关掉卡住的程序了。

## 如果程序一启动就闪退 / 用着自己崩掉

这种一闪就没，需要先让 Windows 在下次崩溃时自动存一份：

1. 下载并双击运行 [启用崩溃转储.reg](启用崩溃转储.reg)，弹窗点「是」。（导入时会弹 UAC，点「是」即可；如果没有管理员权限，改用上面「卡死」那种任务管理器抓法。）
2. 再打开 Vivid Player，把崩溃的操作重做一遍，让它再崩一次。
3. 打开这个文件夹（把整段路径复制到「文件资源管理器」顶部的地址栏回车即可，其中「你的用户名」换成你自己的）：`C:\Users\你的用户名\AppData\Local\VividPlayer\CrashDumps`
4. 里面会有 VividPlayer.App.exe.<数字>.dmp，压缩后发到 demoapp_dev@hotmail.com。

弄完这次，下载并双击 [关闭崩溃转储.reg](关闭崩溃转储.reg) 即可还原。
