# 在 WSA 上使用 Magisk（与 Google 应用程序一起使用）

:警告： 2025 年 3 月 5 日之后，WSA 上的 Magisk 将不再可用。[了解更多信息](https://learn.microsoft.com/en-us/windows/android/wsa/)。

:warning： 针对 fork 开发人员： 请不要使用 GitHub Actions 构建，因为 GitHub 会将您的分叉 GitHub Actions 使用量计入此上游版本库，这可能会导致此上游版本库被 GitHub 工作人员禁用，比如 [MagiskOnWSA](https://github.com/LSPosed/MagiskOnWSA)，因为有许多分叉在构建 GitHub Actions，并将分叉的 Action 使用量计入此上游版本库。

## 支持从以下系统生成

- Linux (x86_64 或 arm64)

  需要以下依赖项：


  | DistrOS             |                            |            |                    |               |               |
  |:-------------------:|----------------------------|------------|--------------------|---------------|---------------|
  | Debian | `python3 aria2 unzip sudo` | `whiptail` | `python3-venv` | `python3-pip` | `p7zip-full` | | `p7zip-full` | `p7zip-full` | `p7zip-full` | `p7zip-full` |
  | openSUSE Tumbleweed | 同上 | `dialog` | `python3-venvctrl` | 同上 | | 同上 |
  | Arch | 与 Debian 相同 | `libnewt` | 与 Debian 相同 | `python-pip` | `p7zip` | `libnewt` | 与 Debian 相同 |

  使用 python3 库 `requests`。

  Python 版本 ≥ **3.7.2**.

  - 建议使用

    - Ubuntu (可以使用 [WSL2](https://apps.microsoft.com/store/search?publisher=Canonical%20Group%20Limited))

      开箱即可使用。

    - Debian（可使用 [WSL2](https://apps.microsoft.com/store/detail/debian/9MSVKQC78PK6)）

      开箱即可使用。

    - openSUSE Tumbleweed（您可以使用 [WSL2](https://apps.microsoft.com/store/detail/opensuse-tumbleweed/9MSSK2ZXXN11)。

      开箱即可使用。

    `run.sh` 会自动处理所有依赖项。

    无需输入任何命令。

### 功能

- 几分钟内点击几下即可集成 Magisk 和 GApps
- 保持每次构建都是最新的
- 支持 ARM64 和 x64
- 支持 MindTheGapps
- 移除亚马逊应用商店
- 修复 VPN 对话框不显示的问题（使用我们的 [VpnDialogs 应用程序](https://github.com/LSPosed/VpnDialogs)
- 添加设备管理功能
- 无人值守安装
- 在 Windows 11 中自动激活开发者模式
- 使用一键脚本更新到新版本，同时保留数据
- 合并所有语言包

## 文本指南

1. 星星（如果你喜欢）。
2. 将 repo 克隆到本地：

   ```bash
   git clone https://github.com/LSPosed/MagiskOnWSALocal.git --depth 1
   ```

3. 运行 `cd MagiskOnWSALocal`。
4. 运行 `./scripts/run.sh`。
5. 选择 WSA 版本及其架构（大多为 x64）。
6. 选择 Magisk 版本。
7. 选择要安装的 GApps 品牌：
   - MindTheGapps

     没有其他变体可供选择。
8. 选择 root 解决方案（无表示无 root）。
9. 如果你是第一次运行脚本，它需要一些时间才能完成。脚本完成后，将在 `MagiskOnWSALocal` 文件夹中生成两个名为 `output` 和 `download` 的新文件夹。转到 `output` 文件夹。运行第 3 步中的 `./run.sh` 脚本时，如果在 “是否要压缩输出？”中选择了 “是”，那么在 “输出 ”文件夹中，你会看到一个名为 “WSA-with-magisk-stable-MindTheGapps_2207.40000.8.0_x64_Release-Nightly ”的压缩文件，或者会有一个名为 “WSA-with-magisk-stable-MindTheGapps_2207.40000.8.0_x64_Release-Nightly ”的文件夹。如果有文件夹，请打开并跳至步骤 10。注意：压缩文件的名称或 `output` 文件夹中生成的文件夹可能会有所不同。这取决于执行 `./run.sh` 时的选择。
10. 提取压缩文件并打开提取文件后创建的文件夹。
11. 在此查找文件 `Run.bat` 并运行。
    - 如果你之前安装了 MagiskOnWSA，它会自动卸载之前的安装，同时**保留所有用户数据**并安装新的，所以不用担心你的数据。
    - 如果您安装的是官方 WSA，则应先卸载它。(如果你想保留数据，可以在卸载前备份“%LOCALAPPDATA%Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\LocalCache\userdata.vhdx” 并在安装后恢复）。
    - 如果弹出窗口在未请求管理许可的情况下消失**，且 WSA 未成功安装，则应以管理员身份手动运行 `Install.ps1`：
        1. 按 `Win+x` 并选择 `Windows 终端 (管理员)`。
        2. 输入 `cd “{X:\path\to\your\extracted\folder}”` 并按 `enter`, 并记住替换 `{X:\path\to\your\extracted\folder}` 包括 `{}`, 例如 `cd “D:\wsa”`.
        3. 输入 `PowerShell.exe -ExecutionPolicy Bypass -File .\Install.ps1` 并按`Enter`。
        4. 脚本将运行并安装 WSA。
        5. 如果此变通方法不起作用，则说明您的电脑不支持 WSA。
12. 将启动 Magisk/Play Store。安装启用了 Zygisk 的 LSPosed-Zygisk 或 Riru 和 LSPosed-Riru，尽情享受吧。

---

## 常见问题

<详情打开

- 我可以删除已安装的文件夹吗？

  不能。

- 如何将 WSA 升级到新版本？

  1. 更新构建脚本：

      ```bash
      git pull
      ```

      有关 git 的更多用法，请参阅 <https://git-scm.com/book> 。

  2. 重新运行脚本，替换之前的安装内容，然后重新运行 `Install.ps1`。不用担心，您的数据将被保留。

- 如何从 WSA 获取 logcat？

  `%LOCALAPPDATA%\Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\LocalState\diagnostics\logcat`.

- 如何将Magisk更新到新版本？

  方法与更新 WSA 相同。

- 如何通过 Play Integrity（以前称为 SafetyNet）？

  和其他模拟器一样，没办法。

- 虚拟化未启用？

  如果未启用，“Install.ps1 ”可帮助您启用。重启后，重新运行 `Install.ps1` 安装 WSA。如果还是不行，就必须在 BIOS 中启用虚拟化。说来话长，请向 Google 寻求帮助。

- 如何将系统重新挂载为读写器？

  在 WSA 中没有办法，因为 Hyper-V 将其挂载为只读。你可以通过制作 Magisk 模块来修改系统。或者直接修改 system.img。请向 Google 寻求帮助。

- 我无法 `adb connect localhost:58526`，怎么办？

  确保已启用开发人员模式。如果问题仍然存在，请在设置页面检查 WSA 的 IP 地址并尝试 `adb connect ip:5555`。

- 为什么Magisk在线模块为空？

  Magisk 会主动删除在线模块库。您可以在本地安装模块，或者通过 `adb push module.zip /data/local/tmp` 和 `adb shell su -c magisk --install-module /data/local/tmp/module.zip` 安装。

- 我可以使用 Magisk v23.0 稳定版或更低版本吗？

  Magisk存在无法在WSA上运行的错误。Magisk v24+ 已经修复了这些问题。因此您必须使用Magisk v24或更高版本。

- 如何删除Magisk？

  选择 “无 ”作为根本解决方案。

- 如何安装自定义 GApp？

  [教程](Custom-GApps.md)

- 在哪里下载MindTheGapps？

  你可以从这里下载[MindTheGapps](https://androidfilehost.com/?w=files&flid=322935) ([mirror](http://downloads.codefi.re/jdcteam/javelinanddart/gapps)).

  请注意，这里没有x86_64预编译包，所以你需要自己编译（[Repository](https://gitlab.com/MindTheGapps/vendor_gapps)）。

  或者也可以从 [this page](https://sourceforge.net/projects/wsa-mtg/files/x86_64/) 下载 x86_64 版 12.1 和 13 的内置软件包。

- 能否将数据从 2305 等较低版本迁移到较新版本？

  当然可以，微软将只读分区从 2305 的EROFS改为只读的 EXT4 只影响只读的系统分区。

  对用户数据分区没有影响。如果出现启动失败，请查看日志。

- 如何安装 KernelSU？

  [教程]（KernelSU.md）

</details

---

## Credits

- [StoreLib](https://github.com/StoreDev/StoreLib)： 下载 WSA 的 API
- [Magisk](https://github.com/topjohnwu/Magisk)： 安卓系统上最有名的 root 解决方案
- ~~[The Open GApps Project](https://opengapps.org)： 最有名的谷歌应用程序软件包解决方案之一~~.
- [WSA-Kernel-SU](https://github.com/LSPosed/WSA-Kernel-SU) 和 [kernel-assisted-superuser](https://git.zx2c4.com/kernel-assisted-superuser/)： 用于调试 Magisk 集成的内核 `su
- ~~[WSAGAScript](https://github.com/ADeltaX/WSAGAScript)： 第一个用于 WSA 的 GApps 集成脚本~~[erofs-utils](): 用于调试 Magisk 集成的内核`su`。
- ~~[erofs-utils](https://github.com/sekaiacg/erofs-utils)： 预编译 `erofs-utils` 并启用 erofsfuse~~

该资源库作为实用程序提供。

_Android 是 Google LLC 的商标。Windows 是微软公司的商标。
