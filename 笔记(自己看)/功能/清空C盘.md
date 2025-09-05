Markdown Preview
## 清空用户目录

`C:\Users\qianjin` C盘共`199G`，该目录占 `102G `

* `C:\Users\qianjin\Documents` 占 `8.32G`

  * `C:\Users\qianjin\Documents\Downloads` 占 `7.53G`

* `C:\Users\qianjin\AppData` 占 `91.6G`

  * `C:\Users\qianjin\AppData\Local\Temp` 可以安全删除 `403M`

* `C:\Users\qianjin\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu20.04LTS_79rhkp1fndgsc\LocalState\ext4.vhdx`占 `75.1G`

在 Windows 11 中，显示文件夹大小有以下几种方法：



* 使用图形界面

  * 鼠标悬停速览：将鼠标指针移动到文件夹上停留片刻，在 “悬浮提示框” 中可看到文件夹的大小。如果未显示，可打开文件资源管理器，点击 “更多（…）” 选择 “选项”，在弹出窗口中勾选 “在工具提示中显示文件大小信息”，点击 “应用” 保存。

  * 查看文件夹属性：使用 “Windows+E” 快捷键打开 “文件资源管理器”，选中要查看的文件夹，右键点击选择 “属性”，或直接按 “Alt+Enter” 快捷键，也可在右侧的 “详细信息” 面板中点击 “属性”。在弹出窗口的 “常规” 选项卡中，可查看 “大小” 和 “占用空间”，“大小” 是文件夹的原始大小，“占用空间” 是文件夹在硬盘上的实际占用空间。

* 使用命令行

  * 使用 “命令提示符”：右键点击 “开始” 菜单，选择 “终端管理员”，以管理员权限打开 Windows 终端，使用 “Ctrl+Shift+2” 快捷键切换到 “命令提示符” 窗口。切换到目标盘符和目标文件夹，执行 “dir /s” 命令查看当前文件夹大小，该命令会遍历文件夹中的所有文件及其大小，并以 “字节” 为单位统计出来，查看 “所列文件总数” 那一行的字节数即可，若要换算成 MB 和 GB 单位，可将字节数复制到字节单位换算器中进行转换。

  * 使用 PowerShell：右键点击 “开始” 菜单，选择 “终端管理员”，以管理员权限打开 Windows 终端，使用 “Ctrl+Shift+1” 快捷键切换到 Powershell 窗口，进入目标文件夹，使用 “Get-ChildItem -Recurse | Measure-Object -Property Length -Sum” 命令递归统计所有文件，并显示总字节数，还可使用后续代码将其转换和输出为更易读的 MB 和 GB 单位。

* 使用第三方工具

  * 使用 WinDirStat 工具：通过 “winget install WinDirStat” 命令安装该应用，打开后选择需要分析的驱动器盘符，扫描完成后，可在 “物理大小” 和 “逻辑大小” 列看到文件夹的占用大小，还能通过彩色块状图直观展示各个文件夹的磁盘占用情况。

  * 使用 Windhawk 魔改 “文件资源管理器”：通过 “winget install Windhawk” 命令安装该应用，打开后搜索 “Better File Sizes in Explorer Details” 插件并安装，安装完成后，在插件的 “设置” 界面，将 “Show Folder Sizes” 下拉菜单设置为启用状态，即可让 “文件资源管理器” 的 “详细信息” 视图中显示文件夹大小。



WSL2中的`ext4.vhdx`文件可以移到其他盘，以下是一般的步骤：

1. 首先，关闭所有正在运行的WSL2相关的终端窗口和应用程序，确保没有任何进程在访问`ext4.vhdx`文件。

2. 打开命令提示符（管理员权限），输入以下命令来停止WSL2服务：

   ```powershell
   wsl --shutdown
   ```

3. 找到`ext4.vhdx`文件的默认存储位置。默认情况下，它位于`C:\Users\<用户名>\AppData\Local\Packages\CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc\LocalState\ext4.vhdx`，你需要将`<用户名>`替换为实际的用户名。

4. 剪切`ext4.vhdx`文件到你想要移动到的目标盘的指定位置。

5. 打开注册表编辑器（管理员权限）`Win+R` 输入 `regedit`，找到`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Lxss`键。在该键下，有一个或多个子键，每个子键对应一个WSL2发行版。找到与你要移动的`ext4.vhdx`文件对应的发行版的子键，通常可以通过查看`DistributionName`值来确定。在该子键下，找到`BasePath`值，将其修改为`ext4.vhdx`文件的新路径。

6. 完成上述步骤后，你可以重新打开WSL2终端，验证系统是否能够正常启动和运行。



在进行上述操作时要谨慎，因为不正确的操作可能会导致WSL2系统无法正常启动。如果可能，在操作前备份`ext4.vhdx`文件和相关的注册表项，以防出现问题可以恢复。
