---
title: 启用安全启动、 BitLocker 和 Windows 10 IoT Core 上的设备保护
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何启用安全引导、 BitLocker 和 Windows 10 IoT Core 上的 Device Guard
keywords: windows iot，安全启动，BitLocker，设备保护、 安全性、 交钥匙安全
ms.openlocfilehash: 68698a1b440b297eb9bfa9223bd324ce330386b9
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510943"
---
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a>启用安全启动、 BitLocker 和 Windows 10 IoT Core 上的设备保护

## <a name="introduction"></a>简介

创意者更新的版本中，Windows 10 IoT 核心版可以提高其安全性推出的功能，包括 UEFI 安全引导、 BitLocker 设备加密和 Device Guard。  这将允许设备生成器中创建完全锁定 Windows IoT 设备时可复原的许多不同类型的攻击。  同时，这些功能提供最佳保护，以确保一个平台，将启动中定义的方式，同时锁定未知的二进制文件和保护用户数据，通过使用设备加密。

### <a name="secure-boot"></a>安全启动

UEFI 安全启动是位于 UEFI 中的第一个策略强制点。  它将系统限制为仅允许执行指定颁发机构签名的二进制文件。 此功能可以阻止在平台上执行未知代码，也可以阻止未知代码削弱它的安全状况。

### <a name="bitlocker-device-encryption"></a>BitLocker 设备加密

Windows 10 IoT Core 还实现 BitLocker 设备加密，保护免受脱机攻击的 IoT 设备的轻量版本。  此功能存在的平台，在执行必要的度量的 UEFI 中包括必要的 preOS 协议上的 TPM 存在强的依赖关系。 这些 preOS 测量可以确保操作系统以后可以明确记录它本身的启动方式；但是，这不会强制执行任何执行限制。

> [!TIP]
> 在 Windows 10 IoT Core 上的 BitLocker 功能允许基于 NTFS 的 OS 卷时绑定到它的所有可用 NTFS 数据卷的自动加密的。  为此，它是为了确保 EFIESP 卷 GUID 将设置为_C12A7328-F81F-11D2-BA4B-00A0C93EC93B_。

### <a name="device-guard-on-windows-iot-core"></a>在 Windows IoT Core 上的设备保护

大多数 IoT 设备是作为固定功能的设备。  这意味着设备构建者知道确切的固件、 操作系统、 驱动程序和应用程序应运行在给定设备上。  随后，可以将此信息用于完全锁定 IoT 设备通过仅允许已知且受信任代码的执行。  在 Windows 10 IoT Core 上的设备保护可帮助保护 IoT 设备通过确保未知或不受信任的可执行代码，不能锁定的设备上运行。

## <a name="locking-down-iot-devices"></a>锁定 IoT 设备

在为锁定 Windows IoT 设备的顺序，必须进行以下注意事项...

### <a name="uefi-platform--secure-boot"></a>UEFI 平台和安全启动

为了充分利用设备保护功能，有必要确保启动二进制文件和 UEFI 固件进行签名，并且不会遭到篡改。  UEFI 安全启动是位于 UEFI 中的第一个策略强制点。  它可以防止通过限制为只允许执行的启动二进制文件由指定的颁发机构签名的系统被篡改。 更多详细信息安全启动以及密钥创建和管理指南，位于[此处](https://technet.microsoft.com/library/dn747883.aspx)。

### <a name="configurable-code-integrity-cci"></a>可配置代码完整性 (CCI)

代码完整性 (CI) 验证驱动程序或应用程序每次加载到内存的完整性，从而可以增强操作系统的安全性。 CI 不含两个主要组件的内核模式代码完整性 (KMCI) 和用户模式代码完整性 (UMCI)。

可配置代码完整性 (CCI) 是一项功能在 Windows 10 中，允许设备的设备构建者为锁定，并仅允许它运行和执行签名和受信任的代码。  若要执行此操作，设备构建者可以 golden 设备 （硬件和软件的最终版本） 上创建的代码完整性策略保护并在工厂车间的所有设备上应用此策略。

若要了解有关部署代码完整性策略的详细信息，审核和强制执行，请查看最新的 technet 文档[此处](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps)。

## <a name="turnkey-security-on-iot-core"></a>在 IoT Core 上的关守安全

为了便于轻松启用 IoT Core 设备上的主要安全功能，Microsoft 将提供统包的安全包，允许设备生成器以生成完全锁定 IoT 设备。  此包将帮助了解：

* 预配安全启动密钥和受支持的 IoT 平台上启用功能
* 安装和配置使用 BitLocker 设备加密 
* 启动设备锁定为只允许已签名的应用程序和驱动程序的执行

### <a name="pre-requisites"></a>先决条件

* 运行 Windows 10 企业版的 PC
* [Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) -必需的证书生成
* [Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) -必需 CAB 生成
* 参考平台的发布的硬件与传送固件、 操作系统、 驱动程序和应用程序将是所必需的最后一个锁定

### <a name="development-iot-devices"></a>开发 IoT 设备

Windows 10 IoT 核心版适用于在数百个设备中利用的各种 silicons。 [建议的 IoT 开发设备](../learn-about-hardware/SoCsAndCustomBoards.md)，下面提供了默认情况下，安全引导、 标准引导、 BitLocker 和 Device Guard 功能以及固件 TPM 功能：

* Qualcomm DragonBoard 410c

    为了启用安全启动，可能需要预配 RPMB。 一旦已经使用 Windows 10 IoT Core 刷新 eMMC (按说明[此处](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c)，按 [Power] + [期 +] + [期-] BDS 菜单从打开电源启动并选择"预配 RPMB"时在设备上同时。 *请注意，这是不可恢复的步骤。*

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

5. 安装生成的.pfx 证书通过直接单击 pfx 文件或使用以下 powershell 命令

    ```powershell
    Import-PfxCertificate -FilePath $pfxfile -CertStoreLocation Cert:\CurrentUser\My
    ```

6. 配置_settings.xml_

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

> [!TIP]
> 可以通过在配置中包括的 Microsoft 应用商店 PCA 2011 证书允许从 Microsoft 应用商店应用_settings.xml_: 
    ```xml
    <Cert>db\MicrosoftMarketPlacePCA2011.cer</Cert>              <!-- Microsoft MarketPlace PCA 2011 -->
    ```

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
    * **SecureBoot** ： 尝试`bcdedit /debug on`，您将获得一个错误，指出值受安全启动策略。
   * **BitLocker** :若要验证的 bitlocker 加密完成后，运行<p>
        `sectask.exe -waitenableforcompletion 1`<p>
        如果它返回 0，这意味着已成功在系统上的所有驱动器都已位置。  任何其他返回代码是失败。<p>
        *其他语法*<p>
         `-waitenableforcompletion [timeout]` <p>
        = > 耐心等待，直到所有 NTFS 卷上完成 BitLocker 加密。<p>
        = > 超时 （秒） 为启用。 若要完成等待。<p>
        = > 如果不指定超时，它将无限期地或启用完成前一直等待。<p>
        返回： <p>
        0 :已成功完成的 BitLocker 加密卷是 Bitlocker 加密。<p>
        ERROR_TIMEOUT:等待完成后，仍在进行加密时超时。<p>
        失败 / 其他代码： 返回位保险箱服务返回的失败错误代码。

    * **DeviceGuard** :运行未签名的任何二进制文件或使用不在 SIPolicy 列表中的证书签名的二进制文件并确认它无法运行。

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
**注意：** 除非计划的加密任务处于禁用状态，将在以后的设备启动重新启用设备加密。

### <a name="disabling-device-guard"></a>禁用 Device Guard

交钥匙安全脚本的文件夹中生成 SIPolicyOn.p7b 和 SIPolicyOff.p7b 文件。
Wm.xml 打包 SIPolicyOn.p7b，并将其放在与 SIPolicy.p7b 系统上。

例如：

```
C:\src\iot-adk-addonkit.db410c\TurnkeySecurity\QCDB\Output\DeviceGuard\Security.DeviceGuard.wm.xml
…
    <files>
        <file
            destinationDir="$(runtime.bootDrive)\efi\microsoft\boot"
            source="SIPolicyOn.p7b"
            name="SIPolicy.p7b" />
    </files>
..

```

如果创建的包将 SIPolicyOff.p7b 文件并将其放置作为 SIPolicy.p7b，它会应用于此包和 Device Guard 将关闭。



