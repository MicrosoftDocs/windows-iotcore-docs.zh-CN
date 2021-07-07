---
title: 在 Windows 10 IoT 核心版上启用安全启动、BitLocker 和设备保护
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何在 Windows 10 IoT 核心版上启用安全启动、BitLocker 和设备保护
keywords: windows iot，安全启动，BitLocker，device guard，安全性，全包式安全
ms.openlocfilehash: 99b106a672a379e8eca6e3d12614bd4af20e88a8
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230704"
---
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a>在 Windows 10 IoT 核心版上启用安全启动、BitLocker 和设备保护

Windows 10 IoT 核心版包括安全功能产品（如 UEFI 安全启动、BitLocker 设备加密和设备保护）。  这将帮助设备构建者创建完全锁定的 Windows IoT 设备，这些设备可复原多种不同类型的攻击。  这些功能结合在一起，可确保平台以定义的方式启动，同时锁定未知的二进制文件并通过使用设备加密来保护用户数据。

## <a name="boot-order"></a>启动顺序

需要先了解 Windows 10 IoT 核心版设备上的启动顺序，然后才能深入了解为 IoT 设备提供安全平台的单个组件。

有三个主要方面发生在 IoT 设备打开时，一直到操作系统内核加载和执行安装的应用程序。

* 平台安全启动
* 统一可扩展固件接口 (UEFI) 安全启动
* Windows代码完整性

![启动顺序](../media/SecureBootAndBitLocker/BootOrder.jpg)

可在[此处](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process)找到有关 Windows 10 启动过程的其他信息。

## <a name="locking-down-iot-devices"></a>锁定 IoT 设备

为了锁定 Windows IoT 设备，必须注意以下事项。

### <a name="platform-secure-boot"></a>平台安全启动

第一次打开设备时，整个启动过程中的第一步是加载并运行固件启动加载程序，它们会初始化设备上的硬件并提供紧急闪烁功能。 然后，将加载 UEFI 环境并移交控制权。

这些固件启动加载程序是 SoC 特定的，因此您需要与相应的设备制造商合作，以便在设备上创建这些启动加载程序。

### <a name="uefi-secure-boot"></a>UEFI 安全启动

UEFI 安全启动是第一个策略强制点，位于 UEFI。  它将系统限制为仅允许执行由指定的颁发机构（如固件驱动程序、选项 Rom、UEFI 驱动程序或应用程序）和 UEFI 启动加载程序所签名的二进制文件。 此功能可防止在平台上执行未知的代码，潜在地削弱这种代码的安全风险。 安全启动降低了对设备进行预启动恶意软件攻击的风险，例如 rootkit。

作为 OEM，需要在生产时将 UEFI 安全启动数据库存储在 IoT 设备上。 这些数据库包括签名数据库 (db) 、已吊销的签名数据库 (.dbx) 和密钥注册密钥数据库 (KEK) 。 这些数据库存储在设备 (NV RAM) 的固件非易失性 RAM 中。

* **(db) 的签名数据库：** 这列出了允许在设备上加载的操作系统加载程序、UEFI 应用程序和 UEFI 驱动程序的签名者或图像哈希

* 已 **吊销 (.dbx) 的签名数据库：** 这列出了不再受信任且 *不* 允许在设备上加载的操作系统加载程序、uefi 应用程序和 uefi 驱动程序的签名者或图像哈希

* **密钥注册密钥数据库 (KEK) ：** 包含一个签名密钥列表，可用于更新签名和吊销的签名数据库。

创建这些数据库并将其添加到设备后，OEM 会锁定固件以进行编辑，并 (PK) 生成平台签名密钥。 此密钥可用于对 KEK 的更新进行签名或禁用 UEFI 安全启动。

下面是 UEFI 安全启动所执行的步骤：

1. 打开设备后，会根据平台签名密钥检查每个签名数据库 (PK) 。
2. 如果固件不受信任，则 UEFI 固件启动 OEM 特定的恢复以还原受信任的固件。
3. 如果无法加载 Windows 启动管理器，固件将尝试启动 Windows 启动管理器的备份副本。 如果此操作失败，则 UEFI 固件会启动 OEM 特定的修正。
4. Windows启动管理器运行并验证 Windows 内核的数字签名。 如果受信任，Windows 启动管理器会将控制权传递给 Windows 内核。

[此处](https://technet.microsoft.com/library/dn747883.aspx)提供有关安全引导的其他详细信息，以及密钥创建和管理指南。

### <a name="windows-code-integrity"></a>Windows代码完整性

Windows代码完整性 (WCI) 通过在每次将驱动程序或应用程序加载到内存时验证其完整性来提高操作系统的安全性。 CI 包含两个主要组件：内核模式代码完整性 (KMCI) 和用户模式代码完整性 (UMCI) 。

可配置代码完整性 (CCI) 是 Windows 10 中的一项功能，它允许设备构建者锁定设备，并仅允许其运行和执行签名和信任的代码。  为此，设备构建者可以在 "黄金" 设备上创建代码完整性策略 (最终版本的硬件和软件) ，然后在工厂地面上的所有设备上保护并应用此策略。

若要了解有关部署代码完整性策略、审核和强制的详细信息，请查看 [此处](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps)的最新 technet 文档。

下面是 Windows 代码完整性执行的步骤：

1. Windows内核将在加载前对签名数据库验证所有其他组件。 这包括驱动程序、启动文件和 ELAM (提前启动反恶意软件) 。
2. Windows内核将在启动过程中加载受信任的组件，并禁止加载不受信任的组件。
3. 操作系统加载 Windows 10 IoT 核心版和任何已安装的应用程序。

### <a name="bitlocker-device-encryption"></a>BitLocker 设备加密

Windows 10 IoT 核心版还实现了 BitLocker 设备加密的轻型版本，保护 IoT 设备免受离线攻击。 此功能与平台上的 TPM 的存在很强，其中包括在 UEFI 中执行必要度量的必需的操作系统协议。 这些预操作系统度量值可确保 OS 更高版本具有操作系统启动方式的明确记录;但是，它不强制执行任何执行限制。

> [!TIP]
> Windows 10 IoT 核心版上的 BitLocker 功能允许对基于 ntfs 的 OS 卷进行自动加密，同时将所有可用的 ntfs 数据卷绑定到该卷。 为此，必须确保 EFIESP 卷 GUID 设置为 _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_。

### <a name="device-guard-on-windows-iot-core"></a>Windows IoT 核心上的设备防护

大多数 IoT 设备被构建为固定功能的设备。 这意味着设备制造商确切知道哪些固件、操作系统、驱动程序和应用程序应在给定设备上运行。 反过来，此信息可用于通过只允许执行已知的和受信任的代码来完全锁定 IoT 设备。 Windows 10 IoT 核心版上的设备防护可以确保无法在锁定的设备上运行未知或不受信任的可执行代码，从而帮助保护 IoT 设备。


## <a name="turnkey-security-on-iot-core"></a>IoT 核心安全

为了便于在 IoT Core 设备上轻松启用密钥安全功能，Microsoft 提供了一个允许设备构建商构建完全锁定的 IoT 设备的 [全包式安全包]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 。 此包将帮助你：

* 设置安全启动密钥并在支持的 IoT 平台上启用该功能
* 使用 BitLocker 设置和配置设备加密
* 启动设备锁定以仅允许执行已签名的应用程序和驱动程序

以下步骤将引导完成使用[交钥匙安全包]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity)创建锁定映像的过程

![创建锁定映像](../media/SecurityFlowAndCertificates/ImageLockDown.png)

### <a name="prerequisites"></a>先决条件

* 提供的脚本 **不** 支持运行 Windows 10 企业版 (其他 Windows 版本的电脑) 
* [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) -证书生成必需
* [Windows 10 ADK](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit) -CAB 生成必需的
* 引用平台-需要随附固件、OS、驱动程序和应用程序的版本硬件才能进行最终锁定

### <a name="development-iot-devices"></a>开发 IoT 设备

Windows 10 IoT 核心版适用于数百个设备中使用的各种 silicons。 在 [建议的 IoT 开发设备](../learn-about-hardware/SoCsAndCustomBoards.md)中，以下提供了现成的固件 TPM 功能，以及安全启动、标准启动、BitLocker 和设备防护功能：

* Qualcomm DragonBoard 410c

    若要启用安全启动，可能需要预配 RPMB。 按照[此处](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c)的说明 Windows 10 IoT 核心版 (刷新 eMMC 时，请在启动时在设备上同时按 [Power] + [Vol +] + [vol] + [vol]，并从 BDS 菜单中选择 "预配 RPMB"。 *请注意，这是一个不可逆的步骤。*

* Intel MinnowBoardMax

    对于 Intel 的 MinnowBoard Max，固件版本必须为0.82 或更高版本 (获取 [最新固件](https://firmware.intel.com/projects/minnowboard-max)) 。 若要启用 TPM 功能，请使用键盘 & 显示连接，然后按 F2 进入 UEFI 设置。 请参阅 _Device Manager-> 系统设置-> 安全配置-> PTT_ 并将其设置为 " _&lt; 启用 &gt;_"。 按 F10 保存更改并继续重新启动平台。

> [!NOTE]
> Raspberry Pi 2 或3不支持 TPM，因此我们无法配置锁定方案。

### <a name="generate-lockdown-packages"></a>生成锁定包

1. 下载 [DeviceLockDown 脚本](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 包，其中包含配置和锁定设备所需的所有其他工具和脚本
2. 在 Windows 10 电脑上启动管理 PowerShell (PS) 控制台，并导航到下载的脚本的位置。
3. 通过网络共享将你的参考硬件平台 (运行未锁定的映像) 到你的电脑上，使用

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. 使用生成设备的密钥

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * 在指定的输出文件夹中生成具有相应后缀的密钥和证书。
    * **保护生成的密钥** ，因为设备将信任仅在锁定后通过这些密钥进行签名的二进制文件。
    * 你可以跳过此步骤，并使用预先生成的密钥仅用于测试

5. 配置 _settings.xml_

    * 常规部分：指定包目录
    * 工具部分：设置工具的路径
        * Windows10KitsRoot `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`
        * WindowsSDKVersion `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`
            * 计算机上安装的 SDK 版本低于 `C:\Program Files (x86)\Windows Kits\10\`
    * SecureBoot 节：指定用于安全启动 (PK 和 SB 键的密钥) 
    * BitLocker 部分：为 BitLocker 数据恢复 (DRA 密钥指定证书) 
    * SIPolicy 节：指定应信任的证书
        * ScanPath：用于扫描二进制文件的设备的路径。 `\\a.b.c.d\C$`
        * 更新： SIPolicy (PAUTH 键的签名者) 
        * 用户模式证书 (UMCI 密钥) 
        * 内核：内核模式证书 (KMCI 密钥) 
    * 打包：指定包生成的设置

> [!IMPORTANT]
> 为了在初始开发周期中协助测试，Microsoft 在适当的位置提供了预生成的密钥和证书。  这意味着 Microsoft 测试、开发和预发布二进制文件被视为受信任。  在最终产品创建和映像生成过程中，请确保删除这些证书并使用你自己的密钥，以确保完全锁定的设备。

6. 执行以下命令以生成所需的包：
```
    powershell

    Import-Module .\IoTTurnkeySecurity.psm1

    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml

    (or)

    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
```

### <a name="test-lockdown-packages"></a>测试锁定包
你可以通过以下步骤在解锁的设备上手动安装生成的包，以对其进行测试

1. 使用解锁的映像刷新设备， (用于在先前步骤中扫描的映像) 。
2. [使用 SSH](../connect-your-device/SSH.md)或[PowerShell](../connect-your-device/PowerShell.md)) 连接到设备 (
3. 将以下 .cab 文件复制到目录下的设备（例如）。 `c:\OemInstall`
    * OEM.Custom.Cmd.cab
    * OEM.Security.BitLocker.cab
    * OEM.Security.SecureBoot.cab
    * OEM.Security.DeviceGuard.cab
4. 发出以下命令启动生成的包的暂存

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    如果使用的是自定义映像，则必须 *跳过* 此文件，并 `c:\windows\system32\oemcustomization.cmd` 使用文件中可用的内容手动编辑 `Output\OEMCustomization\OEMCustomization.cmd`

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. 设备将重新启动以更新 OS (显示齿轮) 来安装包，并再次重新启动到主操作系统。  设备重新启动到 MainOS 后，将启用安全启动并应进行 SIPolicy。
7. 再次重新启动设备以激活 BitLocker 加密。
8. 测试安全功能
    * SecureBoot：尝试 `bcdedit /debug on` ，会收到一条错误消息，指出值受安全启动策略的保护
    * BitLocker：运行 `start /wait sectask.exe -waitencryptcomplete:1` ，如果 ERRORLEVEL `-2147023436` () ERROR_TIMEOUT，则加密不完整。 从 .cmd 文件运行 sectask.exe 时省略 `start /wait` 。
    * DeviceGuard：运行任何未签名的二进制文件或使用不在 SIPolicy 列表中的证书签名的二进制文件，并确认它无法运行。

### <a name="generate-lockdown-image"></a>生成锁定映像

按照前面定义的设置验证锁定包是否正常工作后，可以按照以下给定步骤将这些包包含到映像中。 阅读 [IoT 制造指南](https://aka.ms/iotcoreguide) 了解自定义映像创建说明。

1. 在工作区目录中，从上面生成的输出目录中更新以下文件
    * SecureBoot `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`
      * SetVariable_db bin
      * SetVariable_kek bin
      * SetVariable_pk bin
    * BitLocker `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`
      * DETask.xml
      * Security.Bitlocker.wm.xml
      * setup.exe
    * DeviceGuard : `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`
      * SIPolicyOn
      * SIPolicyOff

2. 在包含锁定包功能 ID 的 ProductName 目录下添加 RetailOEMInput.xml 和 TestOEMInput.xml
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. 重新生成映像
    * `buildpkg all` (基于以上策略文件生成新的锁定包) 
    * `buildimage ProductName test(or)retail`  (生成新的 ffu) 
4. 用这个新的 ffu 闪存设备，并验证安全功能。

请参阅 [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) 作为锁定的龙板配置的示例。

或者，你可以在 IoTCore Shell 本身中生成安全包，请参阅 [添加安全包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) 获取详细信息。


### <a name="developing-with-codesigning-enforcement-enabled"></a>已启用代码签名强制开发

生成包并激活锁定后，在开发过程中引入到映像中的所有二进制文件都需要进行相应的签名。 确保用户模式的二进制文件已用密钥  _.\Keys\ * * *-UMCI_ 进行签名。 对于内核模式签名（如驱动程序），需要指定自己的签名密钥并确保它们也包含在上述 SIPolicy 中。

### <a name="unlocking-encrypted-drives"></a>解锁加密驱动器

在开发和测试期间，如果尝试从脱机的已加密设备读取内容 (例如，通过 USB 大容量存储) 模式将 SD 卡用于 MinnowBoardMax 或 DragonBoard 的 eMMC，则可以使用 "diskpart" 将驱动器号分配给 MainOS 和数据卷， (假设 v：对于 MainOS 和 w：对于数据) 。
卷将被锁定，需要手动解锁。 此操作可在安装了 OEM-DRA 证书的任何计算机上完成， (包含在 [DeviceLockDown 示例](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)) 中。 安装 PFX，并从管理命令提示符运行以下命令：

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

如果需要经常脱机访问内容，可以使用以下命令在初始解锁之后为卷设置 BitLocker autounlock：

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a>禁用 BitLocker

如果需要临时禁用 BitLocker，请使用 IoT 设备启动远程 PowerShell 会话，并运行以下命令： `sectask.exe -disable` 。  

> [!NOTE]
> 除非已禁用计划的加密任务，否则将在随后的设备启动时重新启用设备加密。
