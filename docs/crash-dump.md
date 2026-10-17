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

这种一闪就没，需要先在注册表里加一个设置，让 Windows 在下次崩溃时自动存一份。

### 第一步：在注册表里加设置（只需做一次）

1. 按 Win + R，输入 `regedit`，回车，弹出 UAC 时点「是」。（没有管理员权限的话，改用上面「卡死」那种任务管理器抓法。）
2. 把下面这串路径复制到注册表编辑器顶部的地址栏，回车：
   ```
   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting
   ```
3. 看左侧 `Windows Error Reporting` 下面有没有一项叫 **LocalDumps**。
   - 没有的话：在 `Windows Error Reporting` 上右键 →「新建」→「项」，命名为 `LocalDumps`。
4. 选中 `LocalDumps`，在右侧空白处右键，按下表依次新建 3 个值。双击新建的值就能填数据：

| 新建类型 | 名称 | 数值数据 |
|---|---|---|
| DWORD (32 位)值 | `DumpType` | `2` |
| DWORD (32 位)值 | `DumpCount` | `10` |
| 字符串值 | `DumpFolder` | `C:\dumps` |

   - `DumpType` = 2 表示保存完整转储，`DumpCount` = 10 表示最多保留 10 份，`DumpFolder` 是 Dump 保存的文件夹。
   - 这个设置对**所有程序**生效（不只是 Vivid Player），这段时间里任何程序崩溃都会在 `C:\dumps` 留一份完整转储，比较占硬盘，所以抓完记得按最后一步还原。

建好后，右侧应该能看到这 3 个值（外加一个「(默认)」）。

### 第二步：复现崩溃，取出 Dump

1. 再打开 Vivid Player，把崩溃的操作重做一遍，让它再崩一次。
2. 打开 `C:\dumps` 文件夹（复制到「文件资源管理器」顶部的地址栏回车即可）。
3. 里面以 `VividPlayer.App.exe` 开头的 .dmp 文件就是 Vivid Player 的（其他程序的不用管），压缩后发到 demoapp_dev@hotmail.com。

### 用完还原

回到注册表编辑器的 `...\Windows Error Reporting\LocalDumps`，在右侧把刚才建的 `DumpType`、`DumpCount`、`DumpFolder` 三个值分别右键 →「删除」即可。`LocalDumps` 这一项本身不用删。`C:\dumps` 里的文件发完后也可以直接删掉。