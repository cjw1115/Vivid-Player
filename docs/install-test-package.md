# 怎么安装测试包（旁加载 / sideload）？

[← 返回帮助首页](../README.md)

1. 在设置 →「应用」里找到 **Vivid Player** 卸载。
2. 右键测试包里的 `Add-AppDevPackage.ps1` →「使用 PowerShell 运行」，然后按提示继续（中途会弹 UAC，点「是」）。看到安装成功的提示后，去开始菜单打开「Vivid Player」验证。

如果第 2 步窗口一闪就消失、装不上，先用**管理员身份**打开 PowerShell 执行下面这句，再回到第 2 步右键运行即可：

```
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy Bypass -Force
```
