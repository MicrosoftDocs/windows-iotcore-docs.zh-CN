---
title: 启用安全启动、 BitLocker 和 Windows 10 IoT Core 上的设备保护
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何启用安全引导、 BitLocker 和 Windows 10 IoT Core 上的 Device Guard
keywords: windows iot，安全启动，BitLocker，设备保护、 安全性、 交钥匙安全
ms.openlocfilehash: 092be64210f651c25156e93885a63f35c22d4791
ms.sourcegitcommit: fcc0c6add468040e2f676893b44b260e3ddc3c52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65779396"
---
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a>启用安全启动、 BitLocker 和 Windows 10 IoT Core 上的设备保护

Windows 10 IoT 核心版包括如 UEFI 安全引导、 BitLocker 设备加密和 Device Guard 推出的安全功能。  这些将帮助设备构建者创建完全锁定 Windows IoT 设备时可复原的许多不同类型的攻击。  同时，这些功能提供最佳保护，以确保一个平台，将启动中定义的方式，同时锁定未知的二进制文件和保护用户数据，通过使用设备加密。

## <a name="boot-order"></a>启动顺序

我们可以深入了解为 IoT 设备提供安全的平台的各个组件，还需要了解的 Windows 10 IoT Core 设备上的启动顺序。

有三个主要区域发生从 IoT 设备时已启动的一直到 OS 内核加载和已安装的应用程序的执行。

* 平台安全启动
* 统一可扩展固件接口 (UEFI) 安全启动
* Windows 代码完整性

![启动顺序](../media/SecureBootAndBitLocker/BootOrder.jpg)

可在 Windows 10 启动过程的其他信息[此处](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process)。

## <a name="locking-down-iot-devices"></a>锁定 IoT 设备

为了锁定 Windows IoT 设备，必须考虑以下注意事项。

### <a name="platform-secure-boot"></a>平台安全启动

第一次打开设备，整个引导过程的第一步时，加载并运行固件的引导加载程序，在初始化硬件设备，并提供紧急闪烁的功能。 然后加载 UEFI 环境，控制将传递。

这些固件的引导加载程序是特定于 SoC 的因此将需要使用适当的设备制造商能够在设备上创建这些的引导加载程序。

我们可以深入了解为 IoT 设备提供安全的平台的各个组件，还需要了解的 Windows 10 IoT Core 设备上的启动顺序。

有三个主要区域发生从 IoT 设备时已启动的一直到 OS 内核加载和已安装的应用程序的执行。

* 平台安全启动
* 统一可扩展固件接口 (UEFI) 安全启动
* Windows 代码完整性

![仪表板的屏幕截图](../media/SecureBootAndBitLocker/BootOrder.jpg)

可在 Windows 10 启动过程的其他信息[此处](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process)。

为了锁定 Windows IoT 设备，必须考虑以下注意事项。

### <a name="platform-secure-boot"></a>平台安全启动

第一次打开设备，整个引导过程的第一步时，加载并运行固件的引导加载程序，在初始化硬件设备，并提供紧急闪烁的功能。 然后加载 UEFI 环境，控制将传递。

这些固件的引导加载程序是特定于 SoC 的因此将需要使用适当的设备制造商能够在设备上创建这些的引导加载程序。

### <a name="uefi-secure-boot"></a>UEFI 安全启动

UEFI 安全启动是第一个策略强制点，并且位于在 UEFI 中。  它将限制为只允许指定的颁发机构，如固件驱动程序、 选项 Rom、 UEFI 驱动程序或应用程序和 UEFI 的引导加载程序签名的二进制文件执行的系统。 此功能可以阻止在平台上执行未知代码，也可以阻止未知代码削弱它的安全状况。 安全启动到该设备，如 rootkit 减少预启动恶意软件攻击的风险。 

作为 OEM，您需要用于存储数据库上的 IoT 设备制造时间 UEFI 安全引导。 这些数据库包括签名数据库 (db)、 撤消签名数据库 (dbx) 和密钥注册密钥数据库 (KEK)。 这些数据库存储在设备的固件非易失性内存 （NV 内存）。

为了锁定 Windows IoT 设备，必须考虑以下注意事项。

### <a name="platform-secure-boot"></a>平台安全启动

第一次打开设备，整个引导过程的第一步时，加载并运行固件的引导加载程序，在初始化硬件设备，并提供紧急闪烁的功能。 然后加载 UEFI 环境，控制将传递。

这些固件的引导加载程序是特定于 SoC 的因此将需要使用适当的设备制造商能够在设备上创建这些的引导加载程序。

### <a name="uefi-secure-boot"></a>UEFI 安全启动

UEFI 安全启动是第一个策略强制点，并且位于在 UEFI 中。  它将限制为只允许指定的颁发机构，如固件驱动程序、 选项 Rom、 UEFI 驱动程序或应用程序和 UEFI 的引导加载程序签名的二进制文件执行的系统。 此功能可以阻止在平台上执行未知代码，也可以阻止未知代码削弱它的安全状况。 安全启动到该设备，如 rootkit 减少预启动恶意软件攻击的风险。 

作为 OEM，您需要用于存储数据库上的 IoT 设备制造时间 UEFI 安全引导。 这些数据库包括签名数据库 (db)、 撤消签名数据库 (dbx) 和密钥注册密钥数据库 (KEK)。 这些数据库存储在设备的固件非易失性内存 （NV 内存）。

* **签名数据库 (db):** 这将列出的签名者或操作系统加载程序、 UEFI 应用程序和 UEFI 驱动程序允许在设备上加载的映像哈希

* **已撤消的签名数据库 (dbx):** 这将列出的签名者或操作系统加载程序、 UEFI 应用程序和 UEFI 驱动程序，将不再受信任的它们是映像哈希*不*允许在设备上加载 

* **密钥注册密钥数据库 (KEK):** 包含签名密钥，可用于更新签名且撤消签名数据库的列表。

一旦这些数据库都创建并添加到设备，OEM 锁定编辑，固件，并生成一个签名密钥 (PK) 的平台。 Kek 的更新进行签名，或禁用 UEFI 安全引导，可以使用此密钥。

下面是 UEFI 安全引导所采取的步骤：

1. 设备已开机后，签名数据库每个检查针对签名密钥 (PK) 平台。
2. 如果固件不受信任，UEFI 固件启动特定于 OEM 恢复以还原受信任的固件。
3. 如果无法加载 Windows 启动管理器，固件将尝试启动的 Windows 启动管理器中的备份副本。 如果这也将失败，UEFI 固件启动特定于 OEM 的修正。
4. Windows 启动管理器运行和验证 Windows 内核的数字签名。 如果受信任的 Windows 启动管理器会将控制传递给 Windows 内核中。

更多详细信息安全启动以及密钥创建和管理指南，位于[此处](https://technet.microsoft.com/library/dn747883.aspx)。

### <a name="windows-code-integrity"></a>Windows 代码完整性

Windows 代码完整性 (WCI) 验证驱动程序或应用程序每次加载到内存的完整性，从而可以增强操作系统的安全性。 CI 不含两个主要组件的内核模式代码完整性 (KMCI) 和用户模式代码完整性 (UMCI)。

可配置代码完整性 (CCI) 是一项功能在 Windows 10 中，允许设备的设备构建者为锁定，并仅允许它运行和执行签名和受信任的代码。  若要执行此操作，设备构建者可以 golden 设备 （硬件和软件的最终版本） 上创建的代码完整性策略保护并在工厂车间的所有设备上应用此策略。

若要了解有关部署代码完整性策略的详细信息，审核和强制执行，请查看最新的 technet 文档[此处](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps)。

下面是由 Windows 代码完整性所采取的步骤：

1. Windows 内核将验证对签名的数据库加载之前的所有其他组件。 这包括驱动程序、 启动文件和 ELAM （早期启动反恶意软件）。
2. Windows 内核将加载在启动过程中，受信任的组件，并禁止不受信任的组件的加载。
3. 将加载 Windows 10 IoT 核心版操作系统，以及任何已安装的应用程序。

### <a name="bitlocker-device-encryption"></a>BitLocker 设备加密

Windows 10 IoT Core 还实现 BitLocker 设备加密，保护免受脱机攻击的 IoT 设备的轻量版本。 此功能存在的平台，包括执行必要的度量的 UEFI 中的必要预操作系统协议上的 TPM 存在强的依赖关系。 这些预操作系统度量可确保 OS 今后拥有的操作系统已启动方式; 明确记录但是，它不会强制执行的任何限制。

> [!TIP]
> 在 Windows 10 IoT Core 上的 BitLocker 功能允许基于 NTFS 的 OS 卷时绑定到它的所有可用 NTFS 数据卷的自动加密的。 为此，它是为了确保 EFIESP 卷 GUID 将设置为_C12A7328-F81F-11D2-BA4B-00A0C93EC93B_。

### <a name="device-guard-on-windows-iot-core"></a>在 Windows IoT Core 上的设备保护

大多数 IoT 设备是作为固定功能的设备。 这意味着设备构建者知道确切的固件、 操作系统、 驱动程序和应用程序应运行在给定设备上。 随后，可以将此信息用于完全锁定 IoT 设备通过仅允许已知且受信任代码的执行。 在 Windows 10 IoT Core 上的设备保护可帮助保护 IoT 设备通过确保未知或不受信任的可执行代码，不能锁定的设备上运行。


## <a name="turnkey-security-on-iot-core"></a>在 IoT Core 上的关守安全

为了便于轻松启用 IoT Core 设备上的主要安全功能，Microsoft 将提供[统包安全包]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity)这样生成的设备构建完全锁定 IoT 设备。 此包将帮助了解：

* 预配安全启动密钥和受支持的 IoT 平台上启用功能
* 安装和配置使用 BitLocker 设备加密
* 启动设备锁定为只允许已签名的应用程序和驱动程序的执行

遵循以下步骤将逐步创建一个锁定图像使用[统包安全包]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity)

![创建锁定映像](../media/SecurityFlowAndCertificates/ImageLockDown.png)

### <a name="prerequisites"></a>系统必备

* 运行 Windows 10 企业版的 PC
* [Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) -必需的证书生成
* [Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) -必需 CAB 生成
* 参考平台的发布的硬件与传送固件、 操作系统、 驱动程序和应用程序将是所必需的最后一个锁定

### <a name="development-iot-devices"></a>开发 IoT 设备

Windows 10 IoT 核心版适用于在数百个设备中利用的各种 silicons。 [建议的 IoT 开发设备](../learn-about-hardware/SoCsAndCustomBoards.md)，下面提供了默认情况下，安全引导、 标准引导、 BitLocker 和 Device Guard 功能以及固件 TPM 功能：

* Qualcomm DragonBoard 410c

    为了启用安全启动，可能需要预配 RPMB。 一旦已经使用 Windows 10 IoT Core 刷新 eMMC (按说明[此处](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c)，按 [Power] + [期 +] + [期-] BDS 菜单从打开电源启动并选择"预配 RPMB"时在设备上同时。 *请注意此步骤不可恢复。*

* Intel MinnowBoardMax

    Intel 的 MinnowBoard Max 固件版本必须为 0.82 或更高版本 (获取[最新的固件](https://firmware.intel.com/projects/minnowboard-max))。 若要启用 TPM 功能，请打开附加了键盘和屏幕的开发板的电源，然后按 F2 进入 UEFI 设置。 转到_设备管理器-> 系统设置-> 安全配置-> PTT_并将其设置为_&lt;启用&gt;_。 按 F10 保存更改，并继续重新启动平台。

> [!NOTE]
> Raspberry Pi 2 或 3 不支持 TPM，因此我们不能配置锁定方案。

### <a name="generate-lockdown-packages"></a>生成锁定包

1. 下载[DeviceLockDown 脚本](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)包，其中包含的所有其他工具和脚本所需的配置并锁定设备
2. 在 Windows 10 PC 上启动管理 PowerShell (PS) 控制台并导航到下载的脚本的位置。
3. 将引用硬件平台 （运行解锁的图像） 装载到您的 PC 通过使用网络共享

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. 为设备使用生成密钥

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * 在具有相应后缀指定的输出文件夹中生成密钥和证书。
    * **确保生成的密钥的安全**如设备将信任二进制文件在锁定后才使用这些密钥进行签名。
    * 你可以跳过此步骤和仅供测试使用预生成的密钥

5. 配置_settings.xml_

    * 常规部分：指定包目录
    * 工具部分：设置工具的路径
        * Windows10KitsRoot `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`
        * WindowsSDKVersion `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`
            * 在计算机上安装的 SDK 版本低于 `C:\Program Files (x86)\Windows Kits\10\`
    * SecureBoot 部分：指定要用于安全启动 （PK 和 SB 键） 的键
    * BitLocker 部分：指定 Bitlocker 数据恢复 （DRA 密钥） 的证书
    * SIPolicy 部分：指定应为受信任的证书
        * ScanPath:用于扫描二进制文件，设备的路径 `\\a.b.c.d\C$`
        * 更新：签名者的 SIPolicy （PAUTH 键）
        * 用户：用户模式证书 （UMCI 键） 
        * 内核：内核模式证书 （KMCI 键）
    * 打包：指定包生成设置

> [!IMPORTANT]
> 为了帮助测试初始开发周期内，Microsoft 已提供预生成的密钥和证书，在适当的位置。  这意味着 Microsoft 测试、 开发和预发布二进制文件被视为受信任。  在最终产品创建和生成图像，请确保删除这些证书并使用你自己的密钥以确保完全锁定的设备。

6.执行以下命令以生成所需的包：

    ```powershell
    Import-Module .\IoTTurnkeySecurity.psm1
    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml
    (or)
    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
    ```

### <a name="test-lockdown-packages"></a>测试锁定包
可以通过手动安装它们未锁定的设备上通过以下步骤来测试生成的包

1. Flash 解锁映像 （用于扫描前面的步骤中的映像） 的设备。
2. 连接到设备 ([使用 SSH](../connect-your-device/SSH.md)或使用[Powershell](../connect-your-device/PowerShell.md))
3. 例如以下的.cab 文件复制到的目录下的设备 `c:\OemInstall`
    * OEM.Custom.Cmd.cab
    * OEM.Security.BitLocker.cab
    * OEM.Security.SecureBoot.cab
    * OEM.Security.DeviceGuard.cab
4. 启动临时生成的包的正在发送的以下命令

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    如果你使用自定义映像，则你将需要*跳过*此文件，并手动编辑`c:\windows\system32\oemcustomization.cmd`中提供的内容`Output\OEMCustomization\OEMCustomization.cmd`文件

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. 设备将重新启动进入更新 OS （显示齿轮） 来安装包，并将再次重新启动到主操作系统。  设备重启后恢复到 MainOS，将启用安全启动，并且应按 SIPolicy。
7. 重新启动设备再次激活 Bitlocker 加密。
8. 测试的安全功能
    * SecureBoot： 尝试`bcdedit /debug on`，您将获得一个错误，指出值受安全启动策略
    * BitLocker：运行`fvecon -status c:`，你将获得状态提及*上加密、 已恢复数据 （外部密钥）、 具有 TPM 数据、 安全、 启动分区、 仅已用空间*
    * DeviceGuard:运行未签名的任何二进制文件或使用不在 SIPolicy 列表中的证书签名的二进制文件并确认它无法运行。

### <a name="generate-lockdown-image"></a>生成锁定映像

在验证之后锁定包正在根据前面定义的设置，然后，可以包括这些包到映像按照下面给出的步骤。 读取[IoT 制造指南](https://aka.ms/iotcoreguide)有关自定义映像创建的说明。

1. 在工作区目录中，更新将在上述生成的输出目录中的以下文件
    * SecureBoot: `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`
      * SetVariable_db.bin
      * SetVariable_kek.bin
      * SetVariable_pk.bin
    * BitLocker: `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`
      * DETask.xml
      * Security.Bitlocker.wm.xml
      * setup.bitlocker.cmd
    * DeviceGuard: `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`
      * SIPolicyOn.p7b
      * SIPolicyOff.p7b
  
2. 锁定包功能 id 为 ProductName 目录下添加 RetailOEMInput.xml 和 TestOEMInput.xml
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. 重新生成映像
    * `buildpkg all` （这将生成基于以上策略文件的新锁定包）
    * `buildimage ProductName test(or)retail`  （这将生成新 Flash.ffu）
4. Flash 与此新 Flash.ffu 设备并验证的安全功能。

请参阅[SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample)作为锁定龙板配置的一个示例。

或者，您可以在 IoTCore 外壳本身中生成的安全包，请参阅[添加的安全包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages)有关详细信息。


### <a name="developing-with-codesigning-enforcement-enabled"></a>使用已启用的代码签名强制进行开发

生成包并激活锁定后，任何开发过程中引入到映像中的二进制文件需要正确地签名。 确保您的用户模式的二进制文件进行签名具有键 _。 \Keys\ * * *-UMCI.pfx_。 适用于签名的内核模式，如驱动程序，你将需要指定自己的签名密钥，请确保它们也包括上述 SIPolicy 中。

### <a name="unlocking-encrypted-drives"></a>解锁加密的驱动器

在开发和测试，当尝试读取内容从加密设备脱机 （例如 SD 卡 MinnowBoardMax 或 DragonBoard 的 eMMC 通过 USB 大容量存储模式为），diskpart 可用于将驱动器号分配给 MainOS 和数据量 （让我们假定 v 部分： MainOS 和 w： 数据）。
卷会显示为已锁定，并且需要手动解锁。 这可以在安装了 OEM DRA.pfx 证书的任何计算机上 (包含在[DeviceLockDown 示例](https://github.com/ms-iot/security/tree/master/TurnkeySecurity))。 安装 PFX，然后在管理 CMD 提示符中运行以下命令：

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

如果要经常离线访问内容，可以使用以下命令在初始解锁后设置卷的 BitLocker 自动解锁：

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a>禁用 BitLocker

一旦要临时禁用 BitLocker，请通过 IoT 设备初始化远程 PowerShell 会话，并运行以下命令：`sectask.exe -disable`。  

> [!NOTE]
> 除非计划的加密任务处于禁用状态，将在以后的设备启动重新启用设备加密。


