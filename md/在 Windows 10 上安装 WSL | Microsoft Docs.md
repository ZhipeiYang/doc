> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [docs.microsoft.com](https://docs.microsoft.com/zh-cn/windows/wsl/install-win10#step-4---download-the-linux-kernel-update-package)

适用于 Linux 的 Windows 子系统安装指南 (Windows 10)Windows Subsystem for Linux Installation Guide for Windows 10
=====================================================================================================

*   2021/04/07
*   *    [![](https://github.com/craigloewen-msft.png?size=32) c](https://github.com/craigloewen-msft "craigloewen-msft") 
    *    [![](https://github.com/olprod.png?size=32) o](https://github.com/olprod "olprod") 
    *    [![](https://github.com/ticianaciminari.png?size=32) t](https://github.com/ticianaciminari "ticianaciminari") 
    *    [![](https://github.com/pzhlkj6612.png?size=32) p](https://github.com/pzhlkj6612 "pzhlkj6612") 
    *    [![](https://github.com/howiezhao.png?size=32) h](https://github.com/howiezhao "howiezhao") 

### 本文内容

1.  [Windows 预览体验计划的简化安装](#simplified-installation-for-windows-insiders)
2.  [手动安装步骤](#manual-installation-steps)
3.  [步骤 1 - 启用适用于 Linux 的 Windows 子系统](#step-1---enable-the-windows-subsystem-for-linux)
4.  [步骤 2 - 检查运行 WSL 2 的要求](#step-2---check-requirements-for-running-wsl-2)
5.  [步骤 3 - 启用虚拟机功能](#step-3---enable-virtual-machine-feature)
6.  [步骤 4 - 下载 Linux 内核更新包](#step-4---download-the-linux-kernel-update-package)
7.  [步骤 5 - 将 WSL 2 设置为默认版本](#step-5---set-wsl-2-as-your-default-version)
8.  [步骤 6 - 安装所选的 Linux 分发](#step-6---install-your-linux-distribution-of-choice)
9.  [安装 Windows 终端（可选）](#install-windows-terminal-optional)
10.  [将分发版版本设置为 WSL 1 或 WSL 2](#set-your-distribution-version-to-wsl-1-or-wsl-2)
11.  [排查安装问题](#troubleshooting-installation)

安装适用于 Linux 的 Windows 子系统 (WSL) 时有两个选项：There are two options available for installing Windows Subsystem for Linux (WSL):

*   **[简化安装](#simplified-installation-for-windows-insiders)** _（预览版）_ ：`wsl --install`**[Simplified install](#simplified-installation-for-windows-insiders)** _(preview release)_: `wsl --install`
    
    要使用 `wsl --install` 简化安装命令，你需要加入 [Windows 预览体验计划](https://insider.windows.com/getting-started) 并安装 Windows 10 的预览版（OS 版本 20262 或更高版本），但不需要执行手动安装步骤。The `wsl --install` simplified install command requires that you join the [Windows Insiders Program](https://insider.windows.com/getting-started) and install a preview build of Windows 10 (OS build 20262 or higher), but eliminates the need to follow the manual install steps. 只需使用管理员权限打开命令窗口并运行 `wsl --install`，重启后即可使用 WSL。All you need to do is open a command window with administrator privileges and run `wsl --install`, after a restart you will be ready to use WSL.
    
*   **[手动安装](#manual-installation-steps)** ：按照下列 6 个步骤进行操作。**[Manual install](#manual-installation-steps)**: Follow the six steps listed below.
    
    下面列出了 WSL 的手动安装步骤，可按这些步骤在任意版本的 Windows 10 上安装 Linux。The manual install steps for WSL are listed below and can be used to install Linux on any version of Windows 10.
    

备注

如果在安装过程中遇到问题，请查看本页底部的[安装问题疑难解答](#troubleshooting-installation)。If you run into an issue during the install process, check the [Troubleshooting installation](#troubleshooting-installation) section at the bottom of this page.

[](#simplified-installation-for-windows-insiders)Windows 预览体验计划的简化安装 Simplified Installation for Windows Insiders
-----------------------------------------------------------------------------------------------------------------

在 Windows 10 的最新 Windows 预览体验预览版中，显著改进了适用于 Linux 的 Windows 子系统的安装过程，将以下手动步骤替换为单个命令。The installation process for Windows Subsystem for Linux has been significantly improved in the latest Windows Insiders preview builds of Windows 10, replacing the manual steps below with a single command.

要使用 `wsl --install` 简化安装命令，必须先完成以下操作：In order to use the `wsl --install` simplified install command, you must:

*   加入 [Windows 预览体验计划](https://insider.windows.com/getting-started) Join the [Windows Insiders Program](https://insider.windows.com/getting-started)
*   安装 Windows 10 的预览版（OS 版本 20262 或更高版本）。Install a preview build of Windows 10 (OS build 20262 or higher).
*   使用管理员特权打开命令行窗口 Open a command line windows with Administrator privileges

满足这些要求后，可通过以下方式安装 WSL：Once those requirements are met, to install WSL:

*   在管理员模式下打开命令行，并输入以下命令：`wsl.exe --install`Enter this command in the command line you've opened in Admin mode: `wsl.exe --install`
*   重启计算机 Restart your machine

首次启动新安装的 Linux 分发版时，将打开一个控制台窗口，要求你等待将文件解压缩并存储到电脑上。The first time you launch a newly installed Linux distribution, a console window will open and you'll be asked to wait for files to de-compress and be stored on your PC. 未来的所有启动时间应不到一秒。All future launches should take less than a second.

然后，需要[为新的 Linux 分发版创建用户帐户和密码](user-support)。You will then need to [create a user account and password for your new Linux distribution](user-support).

**祝贺你！现已成功安装并设置了与 Windows 操作系统完全集成的 Linux 分发！****CONGRATULATIONS! You've successfully installed and set up a Linux distribution that is completely integrated with your Windows operating system!**

--install 命令执行以下操作：The --install command performs the following actions:

*   启用可选的 WSL 和虚拟机平台组件 Enables the optional WSL and Virtual Machine Platform components
*   下载并安装最新 Linux 内核 Downloads and installs the latest Linux kernel
*   将 WSL 2 设置为默认值 Sets WSL 2 as the default
*   下载并安装 Linux 分发版（可能需要重启）Downloads and installs a Linux distribution _(reboot may be required)_

默认情况下，安装的 Linux 分发版为 Ubuntu。By default, the installed Linux distribution will be Ubuntu. 可以使用 `wsl --install -d <Distribution Name>` 进行更改。This can be changed using `wsl --install -d <Distribution Name>`. （将 `<Distribution Name>` 替换为所需分发版的名称。）初始安装后，可以使用 `wsl --install -d <Distribution Name>` 命令将其他 Linux 分发版添加到计算机。_(Replacing `<Distribution Name>` with the name of your desired distribution.)_ Additional Linux distributions may be added to your machine after the initial install using the `wsl --install -d <Distribution Name>` command.

若要查看可用 Linux 分发版的列表，请输入 `wsl --list --online`。To see a list of available Linux distributions, enter `wsl --list --online`.

[](#manual-installation-steps)手动安装步骤 Manual Installation Steps
--------------------------------------------------------------

如果你没有使用 Windows 预览体验版本，则需要按照以下步骤手动启用 WSL 所需的功能。If you are not on a Windows Insiders build, the features required for WSL will need to be enabled manually following the steps below.

[](#step-1---enable-the-windows-subsystem-for-linux)步骤 1 - 启用适用于 Linux 的 Windows 子系统 Step 1 - Enable the Windows Subsystem for Linux
------------------------------------------------------------------------------------------------------------------------------------

需要先启用 “适用于 Linux 的 Windows 子系统” 可选功能，然后才能在 Windows 上安装 Linux 分发。You must first enable the "Windows Subsystem for Linux" optional feature before installing any Linux distributions on Windows.

以管理员身份打开 PowerShell 并运行：Open PowerShell as Administrator and run:

```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart


```

建议现在转到步骤 #2，更新到 WSL 2，但如果只想安装 WSL 1，现在可以重新启动计算机，然后继续执行[步骤 6 - 安装所选的 Linux 发行版](install-win10#step-6---install-your-linux-distribution-of-choice)。We recommend now moving on to step #2, updating to WSL 2, but if you wish to only install WSL 1, you can now **restart** your machine and move on to [Step 6 - Install your Linux distribution of choice](install-win10#step-6---install-your-linux-distribution-of-choice). 若要更新到 WSL 2，请等待重新启动计算机，然后继续执行下一步。To update to WSL 2, **wait to restart** your machine and move on to the next step.

[](#step-2---check-requirements-for-running-wsl-2)步骤 2 - 检查运行 WSL 2 的要求 Step 2 - Check requirements for running WSL 2
---------------------------------------------------------------------------------------------------------------------

若要更新到 WSL 2，需要运行 Windows 10。To update to WSL 2, you must be running Windows 10.

*   对于 x64 系统：**版本 1903** 或更高版本，采用 **内部版本 18362** 或更高版本。For x64 systems: **Version 1903** or higher, with **Build 18362** or higher.
*   对于 ARM64 系统：**版本 2004** 或更高版本，采用 **内部版本 19041** 或更高版本。For ARM64 systems: **Version 2004** or higher, with **Build 19041** or higher.
*   低于 18362 的版本不支持 WSL 2。Builds lower than 18362 do not support WSL 2. 使用 [Windows Update 助手](https://www.microsoft.com/software-download/windows10)更新 Windows 版本。Use the [Windows Update Assistant](https://www.microsoft.com/software-download/windows10) to update your version of Windows.

若要检查 Windows 版本及内部版本号，选择 Windows 徽标键 + R，然后键入 “winver”，选择 “确定”。To check your version and build number, select **Windows logo key + R**, type **winver**, select **OK**. 更新到 “设置” 菜单中的[最新 Windows 版本](ms-settings:windowsupdate)。[Update to the latest Windows version](ms-settings:windowsupdate) in the Settings menu.

备注

如果运行的是 Windows 10 版本 1903 或 1909，请在 Windows 菜单中打开 “设置”，导航到 “更新和安全性”，然后选择 “检查更新”。If you are running Windows 10 version 1903 or 1909, open "Settings" from your Windows menu, navigate to "Update & Security" and select "Check for Updates". 内部版本号必须是 18362.1049+ 或 18363.1049+，次要内部版本号需要高于 .1049。Your Build number must be 18362.1049+ or 18363.1049+, with the minor build # over .1049. 阅读详细信息：[WSL 2 即将支持 Windows 10 版本 1903 和 1909](https://devblogs.microsoft.com/commandline/wsl-2-support-is-coming-to-windows-10-versions-1903-and-1909/)。Read more: [WSL 2 Support is coming to Windows 10 Versions 1903 and 1909](https://devblogs.microsoft.com/commandline/wsl-2-support-is-coming-to-windows-10-versions-1903-and-1909/). 请参阅[疑难解答说明](troubleshooting#im-on-windows-10-version-1903-and-i-still-do-not-see-options-for-wsl-2)。See the [troubleshooting instructions](troubleshooting#im-on-windows-10-version-1903-and-i-still-do-not-see-options-for-wsl-2).

[](#step-3---enable-virtual-machine-feature)步骤 3 - 启用虚拟机功能 Step 3 - Enable Virtual Machine feature
--------------------------------------------------------------------------------------------------

安装 WSL 2 之前，必须启用 “虚拟机平台” 可选功能。Before installing WSL 2, you must enable the **Virtual Machine Platform** optional feature. 计算机需要[虚拟化功能](troubleshooting#error-0x80370102-the-virtual-machine-could-not-be-started-because-a-required-feature-is-not-installed)才能使用此功能。Your machine will require [virtualization capabilities](troubleshooting#error-0x80370102-the-virtual-machine-could-not-be-started-because-a-required-feature-is-not-installed) to use this feature.

以管理员身份打开 PowerShell 并运行：Open PowerShell as Administrator and run:

```
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart


```

**重新启动** 计算机，以完成 WSL 安装并更新到 WSL 2。**Restart** your machine to complete the WSL install and update to WSL 2.

[](#step-4---download-the-linux-kernel-update-package)步骤 4 - 下载 Linux 内核更新包 Step 4 - Download the Linux kernel update package
-----------------------------------------------------------------------------------------------------------------------------

1.  下载最新包：Download the latest package:
    
    *   [适用于 x64 计算机的 WSL2 Linux 内核更新包 WSL2 Linux kernel update package for x64 machines](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)
    
    备注
    
    如果使用的是 ARM64 计算机，请下载 [ARM64 包](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi)。If you're using an ARM64 machine, please download the [ARM64 package](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi) instead. 如果不确定自己计算机的类型，请打开命令提示符或 PowerShell，并输入：`systeminfo | find "System Type"`。If you're not sure what kind of machine you have, open Command Prompt or PowerShell and enter: `systeminfo | find "System Type"`. **警告：** 在非英语 Windows 版本中，你可能需要修改搜索文本，例如在德语中为 `systeminfo | find "Systemtyp"`。**Caveat:** On non-English Windows versions, you might have to modify the search text, for example, in German it would be `systeminfo | find "Systemtyp"`.
    
2.  运行上一步中下载的更新包。Run the update package downloaded in the previous step. （双击以运行 - 系统将提示你提供提升的权限，选择 “是” 以批准此安装。）(Double-click to run - you will be prompted for elevated permissions, select ‘yes’ to approve this installation.)
    

安装完成后，请继续执行下一步 - 在安装新的 Linux 分发时，将 WSL 2 设置为默认版本。Once the installation is complete, move on to the next step - setting WSL 2 as your default version when installing new Linux distributions. （如果希望将新的 Linux 安装设置为 WSL 1，请跳过此步骤。）(Skip this step if you want your new Linux installs to be set to WSL 1).

备注

有关详细信息，请参阅 [Windows 命令行博客](https://aka.ms/cliblog)上的文章[对更新 WSL2 Linux 内核的更改](https://devblogs.microsoft.com/commandline/wsl2-will-be-generally-available-in-windows-10-version-2004)。For more information, read the article [changes to updating the WSL2 Linux kernel](https://devblogs.microsoft.com/commandline/wsl2-will-be-generally-available-in-windows-10-version-2004), available on the [Windows Command Line Blog](https://aka.ms/cliblog).

[](#step-5---set-wsl-2-as-your-default-version)步骤 5 - 将 WSL 2 设置为默认版本 Step 5 - Set WSL 2 as your default version
----------------------------------------------------------------------------------------------------------------

打开 PowerShell，然后在安装新的 Linux 发行版时运行以下命令，将 WSL 2 设置为默认版本：Open PowerShell and run this command to set WSL 2 as the default version when installing a new Linux distribution:

```
wsl --set-default-version 2


```

[](#step-6---install-your-linux-distribution-of-choice)步骤 6 - 安装所选的 Linux 分发 Step 6 - Install your Linux distribution of choice
-------------------------------------------------------------------------------------------------------------------------------

1.  打开 [Microsoft Store](https://aka.ms/wslstore)，并选择你偏好的 Linux 分发版。Open the [Microsoft Store](https://aka.ms/wslstore) and select your favorite Linux distribution.
    
    ![](https://docs.microsoft.com/zh-cn/windows/wsl/media/store.png)
    
    单击以下链接会打开每个分发版的 Microsoft Store 页面：The following links will open the Microsoft store page for each distribution:
    
    *   [Ubuntu 16.04 LTSUbuntu 16.04 LTS](https://www.microsoft.com/store/apps/9pjn388hp8c9)
    *   [Ubuntu 18.04 LTSUbuntu 18.04 LTS](https://www.microsoft.com/store/apps/9N9TNGVNDL3Q)
    *   [Ubuntu 20.04 LTSUbuntu 20.04 LTS](https://www.microsoft.com/store/apps/9n6svws3rx71)
    *   [openSUSE Leap 15.1openSUSE Leap 15.1](https://www.microsoft.com/store/apps/9NJFZK00FGKV)
    *   [SUSE Linux Enterprise Server 12 SP5SUSE Linux Enterprise Server 12 SP5](https://www.microsoft.com/store/apps/9MZ3D1TRP8T1)
    *   [SUSE Linux Enterprise Server 15 SP1SUSE Linux Enterprise Server 15 SP1](https://www.microsoft.com/store/apps/9PN498VPMF3Z)
    *   [Kali LinuxKali Linux](https://www.microsoft.com/store/apps/9PKR34TNCV07)
    *   [Debian GNU/LinuxDebian GNU/Linux](https://www.microsoft.com/store/apps/9MSVKQC78PK6)
    *   [Fedora Remix for WSLFedora Remix for WSL](https://www.microsoft.com/store/apps/9n6gdm4k2hnc)
    *   [PengwinPengwin](https://www.microsoft.com/store/apps/9NV1GV1PXZ6P)
    *   [Pengwin EnterprisePengwin Enterprise](https://www.microsoft.com/store/apps/9N8LP0X93VCP)
    *   [Alpine WSLAlpine WSL](https://www.microsoft.com/store/apps/9p804crf0395)
2.  在分发版的页面中，选择 “获取”。From the distribution's page, select"Get".
    
    ![](https://docs.microsoft.com/zh-cn/windows/wsl/media/ubuntustore.png)
    

首次启动新安装的 Linux 分发版时，将打开一个控制台窗口，系统会要求你等待一分钟或两分钟，以便文件解压缩并存储到电脑上。The first time you launch a newly installed Linux distribution, a console window will open and you'll be asked to wait for a minute or two for files to de-compress and be stored on your PC. 未来的所有启动时间应不到一秒。All future launches should take less than a second.

然后，需要[为新的 Linux 分发版创建用户帐户和密码](user-support)。You will then need to [create a user account and password for your new Linux distribution](user-support).

![](https://docs.microsoft.com/zh-cn/windows/wsl/media/ubuntuinstall.png)

**祝贺你！现已成功安装并设置了与 Windows 操作系统完全集成的 Linux 分发！****CONGRATULATIONS! You've successfully installed and set up a Linux distribution that is completely integrated with your Windows operating system!**

[](#install-windows-terminal-optional)安装 Windows 终端（可选）Install Windows Terminal (optional)
------------------------------------------------------------------------------------------

Windows 终端可启用多个选项卡（在多个 Linux 命令行、Windows 命令提示符、PowerShell 和 Azure CLI 等之间快速切换）、创建键绑定（用于打开或关闭选项卡、复制粘贴等的快捷方式键）、使用搜索功能，以及使用自定义主题（配色方案、字体样式和大小、背景图像 / 模糊 / 透明度）。Windows Terminal enables multiple tabs (quickly switch between multiple Linux command lines, Windows Command Prompt, PowerShell, Azure CLI, etc), create custom key bindings (shortcut keys for opening or closing tabs, copy+paste, etc.), use the search feature, and custom themes (color schemes, font styles and sizes, background image/blur/transparency). [了解详细信息。Learn more.](/zh-cn/windows/terminal)

[安装 Windows 终端](/zh-cn/windows/terminal/get-started)。[Install Windows Terminal](/zh-cn/windows/terminal/get-started).

![](https://docs.microsoft.com/zh-cn/windows/wsl/media/terminal.png)

[](#set-your-distribution-version-to-wsl-1-or-wsl-2)将分发版版本设置为 WSL 1 或 WSL 2Set your distribution version to WSL 1 or WSL 2
--------------------------------------------------------------------------------------------------------------------------

可打开 PowerShell 命令行并输入以下命令（仅在 [Windows 内部版本 18362 或更高版本](ms-settings:windowsupdate)中可用），检查分配给每个已安装的 Linux 分发版的 WSL 版本：`wsl -l -v`You can check the WSL version assigned to each of the Linux distributions you have installed by opening the PowerShell command line and entering the command (only available in [Windows Build 18362 or higher](ms-settings:windowsupdate)): `wsl -l -v`

```
wsl --list --verbose


```

若要将分发版设置为受某一 WSL 版本支持，请运行：To set a distribution to be backed by either version of WSL please run:

```
wsl --set-version <distribution name> <versionNumber>


```

请确保将 `<distribution name>` 替换为你的分发版的实际名称，并将 `<versionNumber>` 替换为数字 “1” 或“2”。Make sure to replace `<distribution name>` with the actual name of your distribution and `<versionNumber>` with the number '1' or '2'. 可以随时更改回 WSL 1，方法是运行与上面相同的命令，但将 “2” 替换为“1”。You can change back to WSL 1 at anytime by running the same command as above but replacing the '2' with a '1'.

备注

从 WSL 1 更新到 WSL 2 可能需要几分钟才能完成，具体取决于目标分发版的大小。The update from WSL 1 to WSL 2 may take several minutes to complete depending on the size of your targeted distribution. 如果从 Windows 10 周年更新或创意者更新运行 WSL 1 的旧（历史）安装，可能会遇到更新错误。If you are running an older (legacy) installation of WSL 1 from Windows 10 Anniversary Update or Creators Update, you may encounter an update error. 按照这些说明[卸载并删除任何旧分发](install-legacy#uninstallingremoving-the-legacy-distro)。Follow these instructions to [uninstall and remove any legacy distributions](install-legacy#uninstallingremoving-the-legacy-distro).

如果 `wsl --set-default-version` 结果为无效命令，请输入 `wsl --help`。If `wsl --set-default-version` results as an invalid command, enter `wsl --help`. 如果 `--set-default-version` 未列出，则表示你的 OS 不支持它，你需要更新到版本 1903（内部版本 18362）或更高版本。If the `--set-default-version` is not listed, it means that your OS doesn't support it and you need to update to version 1903, Build 18362 or higher. 如果你在使用 ARM64 版本 19041，那么当使用 PowerShell 时，此命令可能会失败；在这种情况下，你可使用命令提示符，而不是发出 `wsl.exe` 命令。If you are on Build 19041 for ARM64, this command may fail when using PowerShell in which case you can use a _Command Prompt_ instead to issue the `wsl.exe` command.

运行命令后如果看到此消息：`WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel`。If you see this message after running the command: `WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel`. 仍需要安装 MSI Linux 内核更新包。You still need to install the MSI Linux kernel update package.

此外，如果要使 WSL 2 成为你的默认体系结构，可以通过此命令执行该操作：Additionally, if you want to make WSL 2 your default architecture you can do so with this command:

```
wsl --set-default-version 2


```

这会将安装的任何新分发版的版本设置为 WSL 2。This will set the version of any new distribution installed to WSL 2.

[](#troubleshooting-installation)排查安装问题 Troubleshooting installation
--------------------------------------------------------------------

下面是相关的错误和建议的修复措施。Below are related errors and suggested fixes. 有关其他常见错误及其解决方法，请参阅 [WSL 故障排除页](troubleshooting)。Refer to the [WSL troubleshooting page](troubleshooting) for other common errors and their solutions.

*   **安装失败并出现错误 0x80070003****Installation failed with error 0x80070003**
    
    *   适用于 Linux 的 Windows 子系统只能在系统驱动器（通常是 `C:` 驱动器）中运行。The Windows Subsystem for Linux only runs on your system drive (usually this is your `C:` drive). 请确保分发版存储在系统驱动器上：Make sure that distributions are stored on your system drive:
    *   打开 “设置”->“系统”-->“存储”-> **“更多存储设置”：** 更改新内容的保存位置” ![](https://docs.microsoft.com/zh-cn/windows/wsl/media/appstorage.png)Open **Settings** -> **System --> **Storage** -> **More Storage Settings: Change where new content is saved** ![](https://docs.microsoft.com/zh-cn/windows/wsl/media/appstorage.png)
*   **WslRegisterDistribution 失败并出现错误 0x8007019e****WslRegisterDistribution failed with error 0x8007019e**
    
    *   未启用 “适用于 Linux 的 Windows 子系统” 可选组件：The Windows Subsystem for Linux optional component is not enabled:
    *   打开 “控制面板” -> “程序和功能” -> “打开或关闭 Windows 功能”-> 选中 “适用于 Linux 的 Windows 子系统”，或使用本文开头所述的 PowerShell cmdlet。Open **Control Panel** -> **Programs and Features** -> **Turn Windows Feature on or off** -> Check **Windows Subsystem for Linux** or using the PowerShell cmdlet mentioned at the beginning of this article.
*   **安装失败，出现错误 0x80070003 或错误 0x80370102****Installation failed with error 0x80070003 or error 0x80370102**
    
    *   请确保在计算机的 BIOS 内已启用虚拟化。Please make sure that virtualization is enabled inside of your computer's BIOS. 有关如何执行此操作的说明因计算机而异，并且很可能在 CPU 相关选项下。The instructions on how to do this will vary from computer to computer, and will most likely be under CPU related options.
    *   WSL2 要求 CPU 支持二级地址转换 (SLAT) 功能，后者已在 Intel Nehalem 处理器（Intel Core 第一代）和 AMD Opteron 中引入。WSL2 requires that your CPU supports the Second Level Address Translation (SLAT) feature, which was introduced in Intel Nehalem processors (Intel Core 1st Generation) and AMD Opteron. 即使成功安装了虚拟机平台，旧版 CPU（例如 Intel Core 2 Duo）也无法运行 WSL2。Older CPUs (such as the Intel Core 2 Duo) will not be able to run WSL2, even if the Virtual Machine Platform is successfully installed.
*   **尝试升级时出错：`Invalid command line option: wsl --set-version Ubuntu 2`****Error when trying to upgrade: `Invalid command line option: wsl --set-version Ubuntu 2`**
    
    *   请确保已启用适用于 Linux 的 Windows 子系统，并且你使用的是 Windows 内部版本 18362 或更高版本。Enure that you have the Windows Subsystem for Linux enabled, and that you're using Windows Build version 18362 or higher. 若要启用 WSL，请在 PowerShell 提示符下以具有管理员权限的身份运行此命令：`Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`。To enable WSL run this command in a PowerShell prompt with admin privileges: `Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`.
*   **由于虚拟磁盘系统的某个限制，无法完成所请求的操作。虚拟硬盘文件必须是解压缩的且未加密的，并且不能是稀疏的。****The requested operation could not be completed due to a virtual disk system limitation. Virtual hard disk files must be uncompressed and unencrypted and must not be sparse.**
    
    *   取消选中 “压缩内容”（如果已选中 “加密内容”，请一并取消选中），方法是打开 Linux 发行版的配置文件文件夹。Deselect “Compress contents” (as well as “Encrypt contents” if that’s checked) by opening the profile folder for your Linux distribution. 它应位于 Windows 文件系统上的一个文件夹中，类似于：`USERPROFILE%\AppData\Local\Packages\CanonicalGroupLimited...`It should be located in a folder on your Windows file system, something like: `USERPROFILE%\AppData\Local\Packages\CanonicalGroupLimited...`
    *   在此 Linux 发行版配置文件中，应存在一个 LocalState 文件夹。In this Linux distro profile, there should be a LocalState folder. 右键单击此文件夹可显示选项的菜单。Right-click this folder to display a menu of options. 选择 “属性”>“高级”，然后确保未选择（未勾选）“压缩内容以节省磁盘空间” 和“加密内容以保护数据”复选框。Select Properties > Advanced and then ensure that the “Compress contents to save disk space” and “Encrypt contents to secure data” checkboxes are unselected (not checked). 如果系统询问是要将此应用到当前文件夹还是应用到所有子文件夹和文件，请选择 “仅此文件夹”，因为你只是要清除压缩标志。If you are asked whether to apply this to just to the current folder or to all subfolders and files, select “just this folder” because you are only clearing the compress flag. 完成此操作后，`wsl --set-version` 命令应正常工作。After this, the `wsl --set-version` command should work.

![](https://docs.microsoft.com/zh-cn/windows/wsl/media/troubleshooting-virtualdisk-compress.png)

备注

在我的示例中，我的 Ubuntu 18.04 发行版的 LocalState 文件夹位于 C:\Users<my-user-name>\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu18.04onWindows_79rhkp1fndgscIn my case, the LocalState folder for my Ubuntu 18.04 distribution was located at C:\Users<my-user-name>\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu18.04onWindows_79rhkp1fndgsc

请检查 [WSL Docs GitHub 主题 #4103](https://github.com/microsoft/WSL/issues/4103)，其中跟踪了此问题以提供更新的信息。Check [WSL Docs GitHub thread #4103](https://github.com/microsoft/WSL/issues/4103) where this issue is being tracked for updated information.

*   **无法将词语 “wsl” 识别为 cmdlet、函数、脚本文件或可运行程序的名称。****The term 'wsl' is not recognized as the name of a cmdlet, function, script file, or operable program.**
    
    *   请确保[已安装 “适用于 Linux 的 Windows 子系统” 可选组件](install-win10#step-3---enable-virtual-machine-feature)。Ensure that the [Windows Subsystem for Linux Optional Component is installed](install-win10#step-3---enable-virtual-machine-feature). 此外，如果你使用的是 ARM64 设备，并从 PowerShell 运行此命令，则会收到此错误。Additionally, if you are using an ARM64 device and running this command from PowerShell, you will receive this error. 请改为从 [PowerShell Core](/zh-cn/powershell/scripting/install/installing-powershell-core-on-windows) 或从命令提示符运行 `wsl.exe`。Instead run `wsl.exe` from [PowerShell Core](/zh-cn/powershell/scripting/install/installing-powershell-core-on-windows), or Command Prompt.
*   **错误：此更新仅适用于装有适用于 Linux 的 Windows 子系统的计算机。****Error: This update only applies to machines with the Windows Subsystem for Linux.**
    
    *   若要安装 Linux 内核更新 MSI 包，需要 WSL，应先启用它。To install the Linux kernel update MSI package, WSL is required and should be enabled first. 如果失败，将看到以下消息：`This update only applies to machines with the Windows Subsystem for Linux`。If it fails, it you will see the message: `This update only applies to machines with the Windows Subsystem for Linux`.
    *   出现此消息有三个可能的原因：There are three possible reason you see this message:
    
    1.  你仍使用旧版 Windows，不支持 WSL 2。You are still in old version of Windows which doesn't support WSL 2. 有关版本要求和要更新的链接，请参阅步骤 #2。See step #2 for version requirements and links to update.
        
    2.  未启用 WSL。WSL is not enabled. 需要返回到步骤 #1，并确保在计算机上启用了可选的 WSL 功能。You will need to return to step #1 and ensure that the optional WSL feature is enabled on your machine.
        
    3.  启用 WSL 后，需要重新启动才能使其生效，请重新启动计算机，然后重试。After you enabled WSL, a reboot is required for it to take effect, reboot your machine and try again.
        
*   **错误：WSL 2 要求对其内核组件进行更新。若需了解相关信息，请访问 [https://aka.ms/wsl2kernel](https://aka.ms/wsl2kernel) 。****Error: WSL 2 requires an update to its kernel component. For information please visit [https://aka.ms/wsl2kernel](https://aka.ms/wsl2kernel) .**
    
    *   如果 %SystemRoot%\system32\lxss\tools 文件夹中缺少 Linux 内核包，会遇到此错误。If the Linux kernel package is missing in the %SystemRoot%\system32\lxss\tools folder, you will encounter this error. 若要解决此问题，请在安装说明的步骤 #4 中安装 Linux 内核更新 MSI 包。Resolve it by installing the Linux kernel update MSI package in step #4 of these installation instructions. 可能会需要从 [“添加或删除程序”](ms-settings:appsfeatures-app) 卸载 MSI，然后重新安装。You may need to uninstall the MSI from ['Add or Remove Programs'](ms-settings:appsfeatures-app), and install it again.