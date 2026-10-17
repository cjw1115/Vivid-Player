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

1. 在开始按钮上右键 →「终端（管理员）」或「Windows PowerShell（管理员）」，弹出 UAC 时点「是」。（没有管理员权限的话，改用上面「卡死」那种任务管理器抓法。）
2. 把下面整段复制进去，回车。看到三行「操作成功完成」就好了：
   ```
   $k = "HKLM\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\VividPlayer.App.exe"; reg add $k /v DumpType /t REG_DWORD /d 2 /f; reg add $k /v DumpCount /t REG_DWORD /d 10 /f; reg add $k /v DumpFolder /t REG_EXPAND_SZ /d "%LOCALAPPDATA%\VividPlayer\CrashDumps" /f
   ```
   > 要在 **PowerShell / 终端** 里执行，不要用旧的「命令提示符」（cmd）。
3. 再打开 Vivid Player，把崩溃的操作重做一遍，让它再崩一次。
4. 打开这个文件夹（把整段路径复制到「文件资源管理器」顶部的地址栏回车即可，其中「你的用户名」换成你自己的）：`C:\Users\你的用户名\AppData\Local\VividPlayer\CrashDumps`
5. 里面会有 VividPlayer.App.exe.<数字>.dmp，压缩后发到 demoapp_dev@hotmail.com。

弄完这次，同样用管理员 PowerShell 执行下面这句即可还原：

```
reg delete "HKLM\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\VividPlayer.App.exe" /f
```
