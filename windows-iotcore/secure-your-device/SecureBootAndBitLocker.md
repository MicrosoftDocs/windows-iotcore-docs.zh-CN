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
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a><span data-ttu-id="6dcc0-104">启用安全启动、 BitLocker 和 Windows 10 IoT Core 上的设备保护</span><span class="sxs-lookup"><span data-stu-id="6dcc0-104">Enabling Secure Boot, BitLocker, and Device Guard on Windows 10 IoT Core</span></span>

## <a name="introduction"></a><span data-ttu-id="6dcc0-105">简介</span><span class="sxs-lookup"><span data-stu-id="6dcc0-105">Introduction</span></span>

<span data-ttu-id="6dcc0-106">创意者更新的版本中，Windows 10 IoT 核心版可以提高其安全性推出的功能，包括 UEFI 安全引导、 BitLocker 设备加密和 Device Guard。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-106">With the release of Creators Update, Windows 10 IoT Core improves its security feature offerings to include UEFI Secure Boot, BitLocker Device Encryption and Device Guard.</span></span>  <span data-ttu-id="6dcc0-107">这将允许设备生成器中创建完全锁定 Windows IoT 设备时可复原的许多不同类型的攻击。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-107">These will allow device builders in creating fully locked down Windows IoT devices that are resilient to many different types of attacks.</span></span>  <span data-ttu-id="6dcc0-108">同时，这些功能提供最佳保护，以确保一个平台，将启动中定义的方式，同时锁定未知的二进制文件和保护用户数据，通过使用设备加密。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-108">Together, these features provide the optimal protection that ensures that a platform will launch in a defined way, while locking out unknown binaries and protecting user data through the use of device encryption.</span></span>

### <a name="secure-boot"></a><span data-ttu-id="6dcc0-109">安全启动</span><span class="sxs-lookup"><span data-stu-id="6dcc0-109">Secure Boot</span></span>

<span data-ttu-id="6dcc0-110">UEFI 安全启动是位于 UEFI 中的第一个策略强制点。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-110">UEFI Secure Boot is the first policy enforcement point, located in UEFI.</span></span>  <span data-ttu-id="6dcc0-111">它将系统限制为仅允许执行指定颁发机构签名的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-111">It restricts the system to only allow execution of binaries signed by a specified authority.</span></span> <span data-ttu-id="6dcc0-112">此功能可以阻止在平台上执行未知代码，也可以阻止未知代码削弱它的安全状况。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-112">This feature prevents unknown code from being executed on the platform and potentially weakening the security posture of it.</span></span>

### <a name="bitlocker-device-encryption"></a><span data-ttu-id="6dcc0-113">BitLocker 设备加密</span><span class="sxs-lookup"><span data-stu-id="6dcc0-113">BitLocker Device Encryption</span></span>

<span data-ttu-id="6dcc0-114">Windows 10 IoT Core 还实现 BitLocker 设备加密，保护免受脱机攻击的 IoT 设备的轻量版本。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-114">Windows 10 IoT Core also implements a lightweight version of BitLocker Device Encryption, protecting IoT devices against offline attacks.</span></span>  <span data-ttu-id="6dcc0-115">此功能存在的平台，在执行必要的度量的 UEFI 中包括必要的 preOS 协议上的 TPM 存在强的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-115">This capability has a strong dependency on the presence of a TPM on the platform, including the necessary preOS protocol in UEFI that conducts the necessary measurements.</span></span> <span data-ttu-id="6dcc0-116">这些 preOS 测量可以确保操作系统以后可以明确记录它本身的启动方式；但是，这不会强制执行任何执行限制。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-116">These preOS measurements ensure that the OS later has a definitive record of how the OS was launched; however, it does not enforce any execution restrictions.</span></span>

> [!TIP]
> <span data-ttu-id="6dcc0-117">在 Windows 10 IoT Core 上的 BitLocker 功能允许基于 NTFS 的 OS 卷时绑定到它的所有可用 NTFS 数据卷的自动加密的。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-117">BitLocker functionality on Windows 10 IoT Core allows for automatic encryption of NTFS-based OS volume while binding all available NTFS data volumes to it.</span></span>  <span data-ttu-id="6dcc0-118">为此，它是为了确保 EFIESP 卷 GUID 将设置为_C12A7328-F81F-11D2-BA4B-00A0C93EC93B_。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-118">For this, it’s necessary to ensure that the EFIESP volume GUID is set to _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_.</span></span>

### <a name="device-guard-on-windows-iot-core"></a><span data-ttu-id="6dcc0-119">在 Windows IoT Core 上的设备保护</span><span class="sxs-lookup"><span data-stu-id="6dcc0-119">Device Guard on Windows IoT Core</span></span>

<span data-ttu-id="6dcc0-120">大多数 IoT 设备是作为固定功能的设备。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-120">Most IoT devices are built as fixed-function devices.</span></span>  <span data-ttu-id="6dcc0-121">这意味着设备构建者知道确切的固件、 操作系统、 驱动程序和应用程序应运行在给定设备上。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-121">This implies that device builders know exactly which firmware, operating system, drivers and applications should be running on a given device.</span></span>  <span data-ttu-id="6dcc0-122">随后，可以将此信息用于完全锁定 IoT 设备通过仅允许已知且受信任代码的执行。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-122">In turn, this information can be used to fully lockdown an IoT device by only allowing execution of known and trusted code.</span></span>  <span data-ttu-id="6dcc0-123">在 Windows 10 IoT Core 上的设备保护可帮助保护 IoT 设备通过确保未知或不受信任的可执行代码，不能锁定的设备上运行。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-123">Device Guard on Windows 10 IoT Core can help protect IoT devices by ensuring that unknown or untrusted executable code cannot be run on locked-down devices.</span></span>

## <a name="locking-down-iot-devices"></a><span data-ttu-id="6dcc0-124">锁定 IoT 设备</span><span class="sxs-lookup"><span data-stu-id="6dcc0-124">Locking-down IoT Devices</span></span>

<span data-ttu-id="6dcc0-125">在为锁定 Windows IoT 设备的顺序，必须进行以下注意事项...</span><span class="sxs-lookup"><span data-stu-id="6dcc0-125">In order to lockdown a Windows IoT device, the following considerations must be made...</span></span>

### <a name="uefi-platform--secure-boot"></a><span data-ttu-id="6dcc0-126">UEFI 平台和安全启动</span><span class="sxs-lookup"><span data-stu-id="6dcc0-126">UEFI Platform & Secure Boot</span></span>

<span data-ttu-id="6dcc0-127">为了充分利用设备保护功能，有必要确保启动二进制文件和 UEFI 固件进行签名，并且不会遭到篡改。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-127">In order to leverage Device Guard capabilities, it is necessary to ensure that the boot binaries and UEFI firmware are signed and cannot be tampered with.</span></span>  <span data-ttu-id="6dcc0-128">UEFI 安全启动是位于 UEFI 中的第一个策略强制点。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-128">UEFI Secure Boot is the first policy enforcement point, located in UEFI.</span></span>  <span data-ttu-id="6dcc0-129">它可以防止通过限制为只允许执行的启动二进制文件由指定的颁发机构签名的系统被篡改。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-129">It prevents tampering by restricting the system to only allow execution of boot binaries signed by a specified authority.</span></span> <span data-ttu-id="6dcc0-130">更多详细信息安全启动以及密钥创建和管理指南，位于[此处](https://technet.microsoft.com/library/dn747883.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-130">Additional details on Secure Boot, along with key creation and management guidance, is available [here](https://technet.microsoft.com/library/dn747883.aspx).</span></span>

### <a name="configurable-code-integrity-cci"></a><span data-ttu-id="6dcc0-131">可配置代码完整性 (CCI)</span><span class="sxs-lookup"><span data-stu-id="6dcc0-131">Configurable Code Integrity (CCI)</span></span>

<span data-ttu-id="6dcc0-132">代码完整性 (CI) 验证驱动程序或应用程序每次加载到内存的完整性，从而可以增强操作系统的安全性。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-132">Code Integrity (CI) improves the security of the operating system by validating the integrity of a driver or application each time it is loaded into memory.</span></span> <span data-ttu-id="6dcc0-133">CI 不含两个主要组件的内核模式代码完整性 (KMCI) 和用户模式代码完整性 (UMCI)。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-133">CI contains two main components - Kernel Mode Code Integrity (KMCI) and User Mode Code Integrity (UMCI).</span></span>

<span data-ttu-id="6dcc0-134">可配置代码完整性 (CCI) 是一项功能在 Windows 10 中，允许设备的设备构建者为锁定，并仅允许它运行和执行签名和受信任的代码。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-134">Configurable Code Integrity (CCI) is a feature in Windows 10 that allows device builders to lockdown a device and only allow it to run and execute code that is signed and trusted.</span></span>  <span data-ttu-id="6dcc0-135">若要执行此操作，设备构建者可以 golden 设备 （硬件和软件的最终版本） 上创建的代码完整性策略保护并在工厂车间的所有设备上应用此策略。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-135">To do so, device builders can create a code integrity policy on a 'golden' device (final release version of hardware and software) and then secure and apply this policy on all devices on the factory floor.</span></span>

<span data-ttu-id="6dcc0-136">若要了解有关部署代码完整性策略的详细信息，审核和强制执行，请查看最新的 technet 文档[此处](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps)。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-136">To learn more about deploying code integrity policies, auditing and enforcement, check out the latest technet documentation [here](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps).</span></span>

## <a name="turnkey-security-on-iot-core"></a><span data-ttu-id="6dcc0-137">在 IoT Core 上的关守安全</span><span class="sxs-lookup"><span data-stu-id="6dcc0-137">Turnkey Security on IoT Core</span></span>

<span data-ttu-id="6dcc0-138">为了便于轻松启用 IoT Core 设备上的主要安全功能，Microsoft 将提供统包的安全包，允许设备生成器以生成完全锁定 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-138">To facilitate easy enablement of key security features on IoT Core devices, Microsoft is providing a turnkey 'Security Package' that allows device builders to build fully locked down IoT devices.</span></span>  <span data-ttu-id="6dcc0-139">此包将帮助了解：</span><span class="sxs-lookup"><span data-stu-id="6dcc0-139">This package will help with:</span></span>

* <span data-ttu-id="6dcc0-140">预配安全启动密钥和受支持的 IoT 平台上启用功能</span><span class="sxs-lookup"><span data-stu-id="6dcc0-140">Provisioning Secure Boot keys and enabling the feature on supported IoT platforms</span></span>
* <span data-ttu-id="6dcc0-141">安装和配置使用 BitLocker 设备加密</span><span class="sxs-lookup"><span data-stu-id="6dcc0-141">Setup and configuration of device encryption using BitLocker</span></span> 
* <span data-ttu-id="6dcc0-142">启动设备锁定为只允许已签名的应用程序和驱动程序的执行</span><span class="sxs-lookup"><span data-stu-id="6dcc0-142">Initiating device lockdown to only allow execution of signed applications and drivers</span></span>

### <a name="pre-requisites"></a><span data-ttu-id="6dcc0-143">先决条件</span><span class="sxs-lookup"><span data-stu-id="6dcc0-143">Pre-requisites</span></span>

* <span data-ttu-id="6dcc0-144">运行 Windows 10 企业版的 PC</span><span class="sxs-lookup"><span data-stu-id="6dcc0-144">A PC running Windows 10 Enterprise</span></span>
* <span data-ttu-id="6dcc0-145">[Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) -必需的证书生成</span><span class="sxs-lookup"><span data-stu-id="6dcc0-145">[Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) - Required for Certificate Generation</span></span>
* <span data-ttu-id="6dcc0-146">[Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) -必需 CAB 生成</span><span class="sxs-lookup"><span data-stu-id="6dcc0-146">[Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) - Required for CAB generation</span></span>
* <span data-ttu-id="6dcc0-147">参考平台的发布的硬件与传送固件、 操作系统、 驱动程序和应用程序将是所必需的最后一个锁定</span><span class="sxs-lookup"><span data-stu-id="6dcc0-147">Reference platform - release hardware with shipping firmware, OS, drivers and applications will be required for final lockdown</span></span>

### <a name="development-iot-devices"></a><span data-ttu-id="6dcc0-148">开发 IoT 设备</span><span class="sxs-lookup"><span data-stu-id="6dcc0-148">Development IoT Devices</span></span>

<span data-ttu-id="6dcc0-149">Windows 10 IoT 核心版适用于在数百个设备中利用的各种 silicons。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-149">Windows 10 IoT Core works with various silicons that are utilized in hundreds of devices.</span></span> <span data-ttu-id="6dcc0-150">[建议的 IoT 开发设备](../learn-about-hardware/SoCsAndCustomBoards.md)，下面提供了默认情况下，安全引导、 标准引导、 BitLocker 和 Device Guard 功能以及固件 TPM 功能：</span><span class="sxs-lookup"><span data-stu-id="6dcc0-150">Of the [suggested IoT development devices](../learn-about-hardware/SoCsAndCustomBoards.md), the following provide firmware TPM functionality out of the box, along with Secure Boot, Measured Boot, BitLocker and Device Guard capabilities:</span></span>

* <span data-ttu-id="6dcc0-151">Qualcomm DragonBoard 410c</span><span class="sxs-lookup"><span data-stu-id="6dcc0-151">Qualcomm DragonBoard 410c</span></span>

    <span data-ttu-id="6dcc0-152">为了启用安全启动，可能需要预配 RPMB。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-152">In order to enable Secure Boot, it may be necessary to provision RPMB.</span></span> <span data-ttu-id="6dcc0-153">一旦已经使用 Windows 10 IoT Core 刷新 eMMC (按说明[此处](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c)，按 [Power] + [期 +] + [期-] BDS 菜单从打开电源启动并选择"预配 RPMB"时在设备上同时。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-153">Once the eMMC has been flashed with Windows 10 IoT Core (as per instructions [here](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), press [Power] + [Vol+] + [Vol-] simultaneously on the device when powering up and select "Provision RPMB" from the BDS menu.</span></span> *<span data-ttu-id="6dcc0-154">请注意，这是不可恢复的步骤。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-154">Please note that this is an irreversible step.</span></span>*

* <span data-ttu-id="6dcc0-155">Intel MinnowBoardMax</span><span class="sxs-lookup"><span data-stu-id="6dcc0-155">Intel MinnowBoardMax</span></span>

    <span data-ttu-id="6dcc0-156">Intel 的 MinnowBoard Max 固件版本必须为 0.82 或更高版本 (获取[最新的固件](https://firmware.intel.com/projects/minnowboard-max))。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-156">For Intel's MinnowBoard Max, firmware version must be 0.82 or higher (get the [latest firmware](https://firmware.intel.com/projects/minnowboard-max)).</span></span> <span data-ttu-id="6dcc0-157">若要启用 TPM 功能，请打开附加了键盘和屏幕的开发板的电源，然后按 F2 进入 UEFI 设置。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-157">To enable TPM capabilities, power up board with a keyboard & display attached and press F2 to enter UEFI setup.</span></span> <span data-ttu-id="6dcc0-158">转到_设备管理器-> 系统设置-> 安全配置-> PTT_并将其设置为_&lt;启用&gt;_。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-158">Go to _Device Manager -> System Setup -> Security Configuration -> PTT_ and set it to _&lt;Enable&gt;_.</span></span> <span data-ttu-id="6dcc0-159">按 F10 保存更改，并继续重新启动平台。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-159">Press F10 to save changes and proceed with a reboot of the platform.</span></span>

> [!NOTE]
> <span data-ttu-id="6dcc0-160">Raspberry Pi 2 或 3 不支持 TPM，因此我们不能配置锁定方案。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-160">Raspberry Pi 2 nor 3 do not support TPM and so we cannot configure Lockdown scenarios.</span></span>

### <a name="generate-lockdown-packages"></a><span data-ttu-id="6dcc0-161">生成锁定包</span><span class="sxs-lookup"><span data-stu-id="6dcc0-161">Generate Lockdown Packages</span></span>

1. <span data-ttu-id="6dcc0-162">下载[DeviceLockDown 脚本](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)包，其中包含的所有其他工具和脚本所需的配置并锁定设备</span><span class="sxs-lookup"><span data-stu-id="6dcc0-162">Download the [DeviceLockDown Script](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) package, which contains all of the additional tools and scripts required for configuring and locking down devices</span></span>
2. <span data-ttu-id="6dcc0-163">在 Windows 10 PC 上启动管理 PowerShell (PS) 控制台并导航到下载的脚本的位置。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-163">Start an Administrative PowerShell (PS) console on your Windows 10 PC and navigate to the location of the downloaded script.</span></span>
3. <span data-ttu-id="6dcc0-164">将引用硬件平台 （运行解锁的图像） 装载到您的 PC 通过使用网络共享</span><span class="sxs-lookup"><span data-stu-id="6dcc0-164">Mount your reference hardware platform (running the unlocked image) to your PC via network share using</span></span>

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. <span data-ttu-id="6dcc0-165">为设备使用生成密钥</span><span class="sxs-lookup"><span data-stu-id="6dcc0-165">Generate keys for your device using</span></span>

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * <span data-ttu-id="6dcc0-166">在具有相应后缀指定的输出文件夹中生成密钥和证书。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-166">The keys and certificates are generated in the specified output folder with appropriate suffix.</span></span>
    * <span data-ttu-id="6dcc0-167">**确保生成的密钥的安全**如设备将信任二进制文件在锁定后才使用这些密钥进行签名。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-167">**Secure your generated keys** as the device will trust binaries signed with these keys only after lockdown.</span></span>
    * <span data-ttu-id="6dcc0-168">你可以跳过此步骤和仅供测试使用预生成的密钥</span><span class="sxs-lookup"><span data-stu-id="6dcc0-168">You may skip this step and use the pre-generated keys for testing only</span></span>

5. <span data-ttu-id="6dcc0-169">安装生成的.pfx 证书通过直接单击 pfx 文件或使用以下 powershell 命令</span><span class="sxs-lookup"><span data-stu-id="6dcc0-169">Install the generated .pfx certificates by clicking on the pfx files directly or using the below powershell command</span></span>

    ```powershell
    Import-PfxCertificate -FilePath $pfxfile -CertStoreLocation Cert:\CurrentUser\My
    ```

6. <span data-ttu-id="6dcc0-170">配置_settings.xml_</span><span class="sxs-lookup"><span data-stu-id="6dcc0-170">Configure _settings.xml_</span></span>

    * <span data-ttu-id="6dcc0-171">常规部分：指定包目录</span><span class="sxs-lookup"><span data-stu-id="6dcc0-171">General section : Specify the package directories</span></span>
    * <span data-ttu-id="6dcc0-172">工具部分：设置工具的路径</span><span class="sxs-lookup"><span data-stu-id="6dcc0-172">Tools section : Set the path for the tools</span></span>
        * <span data-ttu-id="6dcc0-173">Windows10KitsRoot</span><span class="sxs-lookup"><span data-stu-id="6dcc0-173">Windows10KitsRoot</span></span> `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`
        * <span data-ttu-id="6dcc0-174">WindowsSDKVersion</span><span class="sxs-lookup"><span data-stu-id="6dcc0-174">WindowsSDKVersion</span></span> `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`
            * <span data-ttu-id="6dcc0-175">在计算机上安装的 SDK 版本低于</span><span class="sxs-lookup"><span data-stu-id="6dcc0-175">SDK version installed on your machine is under</span></span> `C:\Program Files (x86)\Windows Kits\10\`
    * <span data-ttu-id="6dcc0-176">SecureBoot 部分：指定要用于安全启动 （PK 和 SB 键） 的键</span><span class="sxs-lookup"><span data-stu-id="6dcc0-176">SecureBoot section : Specify which keys to use for secure boot (PK and SB keys)</span></span>
    * <span data-ttu-id="6dcc0-177">BitLocker 部分：指定 Bitlocker 数据恢复 （DRA 密钥） 的证书</span><span class="sxs-lookup"><span data-stu-id="6dcc0-177">BitLocker section : Specify a certificate for Bitlocker data recovery (DRA key)</span></span>
    * <span data-ttu-id="6dcc0-178">SIPolicy 部分：指定应为受信任的证书</span><span class="sxs-lookup"><span data-stu-id="6dcc0-178">SIPolicy section : Specify certs that should be trusted</span></span>
        * <span data-ttu-id="6dcc0-179">ScanPath:用于扫描二进制文件，设备的路径</span><span class="sxs-lookup"><span data-stu-id="6dcc0-179">ScanPath : Path of the device for scanning binaries ,</span></span> `\\a.b.c.d\C$`
        * <span data-ttu-id="6dcc0-180">更新：签名者的 SIPolicy （PAUTH 键）</span><span class="sxs-lookup"><span data-stu-id="6dcc0-180">Update   : Signer of the SIPolicy (PAUTH keys)</span></span>
        * <span data-ttu-id="6dcc0-181">用户：用户模式证书 （UMCI 键）</span><span class="sxs-lookup"><span data-stu-id="6dcc0-181">User     : User mode certificates (UMCI keys)</span></span> 
        * <span data-ttu-id="6dcc0-182">内核：内核模式证书 （KMCI 键）</span><span class="sxs-lookup"><span data-stu-id="6dcc0-182">Kernel   : Kernel mode certificates (KMCI keys)</span></span>
    * <span data-ttu-id="6dcc0-183">打包：指定包生成设置</span><span class="sxs-lookup"><span data-stu-id="6dcc0-183">Packaging : Specify the settings for the package generation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6dcc0-184">为了帮助测试初始开发周期内，Microsoft 已提供预生成的密钥和证书，在适当的位置。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-184">In order to assist with testing during the initial development cycle, Microsoft has provided pre-generated keys and certificates where appropriate.</span></span>  <span data-ttu-id="6dcc0-185">这意味着 Microsoft 测试、 开发和预发布二进制文件被视为受信任。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-185">This implies that Microsoft Test, Development and Pre-Release binaries are considered trusted.</span></span>  <span data-ttu-id="6dcc0-186">在最终产品创建和生成图像，请确保删除这些证书并使用你自己的密钥以确保完全锁定的设备。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-186">During final product creation and image generation, be sure to remove these certifcates and use your own keys to ensure a fully locked down device.</span></span>

> [!TIP]
> <span data-ttu-id="6dcc0-187">可以通过在配置中包括的 Microsoft 应用商店 PCA 2011 证书允许从 Microsoft 应用商店应用_settings.xml_:</span><span class="sxs-lookup"><span data-stu-id="6dcc0-187">The apps from Microsoft App Store can be allowed by including the Microsoft Marketplace PCA 2011 certificate in the configuration _settings.xml_:</span></span> 
    ```xml
    <Cert>db\MicrosoftMarketPlacePCA2011.cer</Cert>              <!-- Microsoft MarketPlace PCA 2011 -->
    ```

<span data-ttu-id="6dcc0-188">6.执行以下命令以生成所需的包：</span><span class="sxs-lookup"><span data-stu-id="6dcc0-188">6.Execute the following commands to generate required packages:</span></span>

    ```powershell
    Import-Module .\IoTTurnkeySecurity.psm1
    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml
    (or)
    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
    ```

### <a name="test-lockdown-packages"></a><span data-ttu-id="6dcc0-189">测试锁定包</span><span class="sxs-lookup"><span data-stu-id="6dcc0-189">Test Lockdown packages</span></span>
<span data-ttu-id="6dcc0-190">可以通过手动安装它们未锁定的设备上通过以下步骤来测试生成的包</span><span class="sxs-lookup"><span data-stu-id="6dcc0-190">You can test the generated packages by manually installing them on a unlocked device by the following steps</span></span>

1. <span data-ttu-id="6dcc0-191">Flash 解锁映像 （用于扫描前面的步骤中的映像） 的设备。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-191">Flash the device with the unlocked image (image used for scanning in earlier step).</span></span>
2. <span data-ttu-id="6dcc0-192">连接到设备 ([使用 SSH](../connect-your-device/SSH.md)或使用[Powershell](../connect-your-device/PowerShell.md))</span><span class="sxs-lookup"><span data-stu-id="6dcc0-192">Connect to the device ([using SSH](../connect-your-device/SSH.md) or using [Powershell](../connect-your-device/PowerShell.md))</span></span>
3. <span data-ttu-id="6dcc0-193">例如以下的.cab 文件复制到的目录下的设备</span><span class="sxs-lookup"><span data-stu-id="6dcc0-193">Copy the following .cab files to the device under a directory e.g.</span></span> `c:\OemInstall`
    * <span data-ttu-id="6dcc0-194">OEM.Custom.Cmd.cab</span><span class="sxs-lookup"><span data-stu-id="6dcc0-194">OEM.Custom.Cmd.cab</span></span>
    * <span data-ttu-id="6dcc0-195">OEM.Security.BitLocker.cab</span><span class="sxs-lookup"><span data-stu-id="6dcc0-195">OEM.Security.BitLocker.cab</span></span>
    * <span data-ttu-id="6dcc0-196">OEM.Security.SecureBoot.cab</span><span class="sxs-lookup"><span data-stu-id="6dcc0-196">OEM.Security.SecureBoot.cab</span></span>
    * <span data-ttu-id="6dcc0-197">OEM.Security.DeviceGuard.cab</span><span class="sxs-lookup"><span data-stu-id="6dcc0-197">OEM.Security.DeviceGuard.cab</span></span>
4. <span data-ttu-id="6dcc0-198">启动临时生成的包的正在发送的以下命令</span><span class="sxs-lookup"><span data-stu-id="6dcc0-198">Initiate staging of the generated packages by issueing the following commands</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    <span data-ttu-id="6dcc0-199">如果你使用自定义映像，则你将需要*跳过*此文件，并手动编辑`c:\windows\system32\oemcustomization.cmd`中提供的内容`Output\OEMCustomization\OEMCustomization.cmd`文件</span><span class="sxs-lookup"><span data-stu-id="6dcc0-199">If you are using custom image, then you will have to *skip* this file and manually edit the `c:\windows\system32\oemcustomization.cmd` with the contents available in `Output\OEMCustomization\OEMCustomization.cmd` file</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. <span data-ttu-id="6dcc0-200">设备将重新启动进入更新 OS （显示齿轮） 来安装包，并将再次重新启动到主操作系统。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-200">The device will reboot into update OS (showing gears) to install the packages and will reboot again to main OS.</span></span>  <span data-ttu-id="6dcc0-201">设备重启后恢复到 MainOS，将启用安全启动，并且应按 SIPolicy。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-201">Once the device reboots back into MainOS, Secure Boot will be enabled and SIPolicy should be engaged.</span></span>
7. <span data-ttu-id="6dcc0-202">重新启动设备再次激活 Bitlocker 加密。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-202">Reboot the device again to activate the Bitlocker encryption.</span></span>
8. <span data-ttu-id="6dcc0-203">测试的安全功能</span><span class="sxs-lookup"><span data-stu-id="6dcc0-203">Test the security features</span></span>
    * <span data-ttu-id="6dcc0-204">**SecureBoot** ： 尝试`bcdedit /debug on`，您将获得一个错误，指出值受安全启动策略。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-204">**SecureBoot** : try `bcdedit /debug on` , you will get an error stating that the value is protected by secure boot policy.</span></span>
   * <span data-ttu-id="6dcc0-205">**BitLocker** :若要验证的 bitlocker 加密完成后，运行</span><span class="sxs-lookup"><span data-stu-id="6dcc0-205">**BitLocker** : To validate that bitlocker encryption has been completed, run</span></span><p>
        `sectask.exe -waitenableforcompletion 1`<p>
        <span data-ttu-id="6dcc0-206">如果它返回 0，这意味着已成功在系统上的所有驱动器都已位置。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-206">If it returns 0, that means all drives on the system have been bitlockered successfully.</span></span>  <span data-ttu-id="6dcc0-207">任何其他返回代码是失败。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-207">Any other return code is failure.</span></span><p>
        *<span data-ttu-id="6dcc0-208">其他语法</span><span class="sxs-lookup"><span data-stu-id="6dcc0-208">Additional Syntax</span></span>*<p>
         `-waitenableforcompletion [timeout]` <p>
        <span data-ttu-id="6dcc0-209">= > 耐心等待，直到所有 NTFS 卷上完成 BitLocker 加密。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-209">=> Wait until BitLocker encryption is completed on all NTFS volumes.</span></span><p>
        <span data-ttu-id="6dcc0-210">= > 超时 （秒） 为启用。 若要完成等待。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-210">=> Timeout in seconds to wait for enable to complete.</span></span><p>
        <span data-ttu-id="6dcc0-211">= > 如果不指定超时，它将无限期地或启用完成前一直等待。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-211">=> If timeout not specified, it will wait indefinitely or until enable completes.</span></span><p>
        <span data-ttu-id="6dcc0-212">返回：</span><span class="sxs-lookup"><span data-stu-id="6dcc0-212">Returns:</span></span> <p>
        <span data-ttu-id="6dcc0-213">0 :已成功完成的 BitLocker 加密卷是 Bitlocker 加密。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-213">0 : BitLocker encryption successfully completed, volume is Bitlocker encrypted.</span></span><p>
        <span data-ttu-id="6dcc0-214">ERROR_TIMEOUT:等待完成后，仍在进行加密时超时。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-214">ERROR_TIMEOUT: Timeout waiting for completion, encryption still in progress.</span></span><p>
        <span data-ttu-id="6dcc0-215">失败 / 其他代码： 返回位保险箱服务返回的失败错误代码。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-215">Failure/Other code: returns the failure error code returned by the bit locker service.</span></span>

    * <span data-ttu-id="6dcc0-216">**DeviceGuard** :运行未签名的任何二进制文件或使用不在 SIPolicy 列表中的证书签名的二进制文件并确认它无法运行。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-216">**DeviceGuard** : Run any unsigned binary or a binary signed with certificate not in the SIPolicy list and confirm that it fails to run.</span></span>

### <a name="generate-lockdown-image"></a><span data-ttu-id="6dcc0-217">生成锁定映像</span><span class="sxs-lookup"><span data-stu-id="6dcc0-217">Generate Lockdown image</span></span>

<span data-ttu-id="6dcc0-218">在验证之后锁定包正在根据前面定义的设置，然后，可以包括这些包到映像按照下面给出的步骤。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-218">After validating that the lockdown packages are working as per the settings defined earlier, you can then include these packages into the image by following the below given steps.</span></span> <span data-ttu-id="6dcc0-219">读取[IoT 制造指南](https://aka.ms/iotcoreguide)有关自定义映像创建的说明。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-219">Read [IoT manufacturing guide](https://aka.ms/iotcoreguide) for custom image creation instructions.</span></span>

1. <span data-ttu-id="6dcc0-220">在工作区目录中，更新将在上述生成的输出目录中的以下文件</span><span class="sxs-lookup"><span data-stu-id="6dcc0-220">In the workspace directory, update the following files from the generated output directory above</span></span>
    * <span data-ttu-id="6dcc0-221">SecureBoot:</span><span class="sxs-lookup"><span data-stu-id="6dcc0-221">SecureBoot :</span></span> `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`
      * <span data-ttu-id="6dcc0-222">SetVariable_db.bin</span><span class="sxs-lookup"><span data-stu-id="6dcc0-222">SetVariable_db.bin</span></span>
      * <span data-ttu-id="6dcc0-223">SetVariable_kek.bin</span><span class="sxs-lookup"><span data-stu-id="6dcc0-223">SetVariable_kek.bin</span></span>
      * <span data-ttu-id="6dcc0-224">SetVariable_pk.bin</span><span class="sxs-lookup"><span data-stu-id="6dcc0-224">SetVariable_pk.bin</span></span>
    * <span data-ttu-id="6dcc0-225">BitLocker:</span><span class="sxs-lookup"><span data-stu-id="6dcc0-225">BitLocker :</span></span> `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`
      * <span data-ttu-id="6dcc0-226">DETask.xml</span><span class="sxs-lookup"><span data-stu-id="6dcc0-226">DETask.xml</span></span>
      * <span data-ttu-id="6dcc0-227">Security.Bitlocker.wm.xml</span><span class="sxs-lookup"><span data-stu-id="6dcc0-227">Security.Bitlocker.wm.xml</span></span>
      * <span data-ttu-id="6dcc0-228">setup.bitlocker.cmd</span><span class="sxs-lookup"><span data-stu-id="6dcc0-228">setup.bitlocker.cmd</span></span>
    * <span data-ttu-id="6dcc0-229">DeviceGuard:</span><span class="sxs-lookup"><span data-stu-id="6dcc0-229">DeviceGuard :</span></span> `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`
      * <span data-ttu-id="6dcc0-230">SIPolicyOn.p7b</span><span class="sxs-lookup"><span data-stu-id="6dcc0-230">SIPolicyOn.p7b</span></span>
      * <span data-ttu-id="6dcc0-231">SIPolicyOff.p7b</span><span class="sxs-lookup"><span data-stu-id="6dcc0-231">SIPolicyOff.p7b</span></span>
  
2. <span data-ttu-id="6dcc0-232">锁定包功能 id 为 ProductName 目录下添加 RetailOEMInput.xml 和 TestOEMInput.xml</span><span class="sxs-lookup"><span data-stu-id="6dcc0-232">Add RetailOEMInput.xml and TestOEMInput.xml under the ProductName directory with lockdown package feature ID</span></span>
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. <span data-ttu-id="6dcc0-233">重新生成映像</span><span class="sxs-lookup"><span data-stu-id="6dcc0-233">Re-generate Image</span></span>
    * `buildpkg all` <span data-ttu-id="6dcc0-234">（这将生成基于以上策略文件的新锁定包）</span><span class="sxs-lookup"><span data-stu-id="6dcc0-234">(this generates new lockdown packages based on above policy files)</span></span>
    * `buildimage ProductName test(or)retail`  <span data-ttu-id="6dcc0-235">（这将生成新 Flash.ffu）</span><span class="sxs-lookup"><span data-stu-id="6dcc0-235">(this generates new Flash.ffu)</span></span>
4. <span data-ttu-id="6dcc0-236">Flash 与此新 Flash.ffu 设备并验证的安全功能。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-236">Flash the device with this new Flash.ffu and validate the security features.</span></span>

<span data-ttu-id="6dcc0-237">请参阅[SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample)作为锁定龙板配置的一个示例。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-237">See [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) as an example of a lockdown dragon board configuration.</span></span>

<span data-ttu-id="6dcc0-238">或者，您可以在 IoTCore 外壳本身中生成的安全包，请参阅[添加的安全包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages)有关详细信息。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-238">Alternatively, you can generate the security packages in the IoTCore Shell itself, see [adding security packages](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) for the details.</span></span>


### <a name="developing-with-codesigning-enforcement-enabled"></a><span data-ttu-id="6dcc0-239">使用已启用的代码签名强制进行开发</span><span class="sxs-lookup"><span data-stu-id="6dcc0-239">Developing with CodeSigning Enforcement Enabled</span></span>

<span data-ttu-id="6dcc0-240">生成包并激活锁定后，任何开发过程中引入到映像中的二进制文件需要正确地签名。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-240">Once the packages are generated and lockdown is activated, any binaries introduced into the image during development will need to be signed appropriately.</span></span> <span data-ttu-id="6dcc0-241">确保您的用户模式的二进制文件进行签名具有键 _。 \Keys\ \* \* \*-UMCI.pfx_。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-241">Ensure that your user-mode binaries are signed with the key  _.\Keys\ \*\*\*-UMCI.pfx_.</span></span> <span data-ttu-id="6dcc0-242">适用于签名的内核模式，如驱动程序，你将需要指定自己的签名密钥，请确保它们也包括上述 SIPolicy 中。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-242">For kernel-mode signing, such as for drivers, you’ll need to specify your own signing keys and make sure that they are also included in the SIPolicy above.</span></span>

### <a name="unlocking-encrypted-drives"></a><span data-ttu-id="6dcc0-243">解锁加密的驱动器</span><span class="sxs-lookup"><span data-stu-id="6dcc0-243">Unlocking Encrypted Drives</span></span>

<span data-ttu-id="6dcc0-244">在开发和测试，当尝试读取内容从加密设备脱机 （例如 SD 卡 MinnowBoardMax 或 DragonBoard 的 eMMC 通过 USB 大容量存储模式为），diskpart 可用于将驱动器号分配给 MainOS 和数据量 （让我们假定 v 部分： MainOS 和 w： 数据）。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-244">During development and testing, when attempting to read contents from an encrypted device offline (e.g. SD card for MinnowBoardMax or DragonBoard's eMMC through USB mass storage mode), 'diskpart' may be used to assign a drive letter to MainOS and Data volume (let's assume v: for MainOS and w: for Data).</span></span>
<span data-ttu-id="6dcc0-245">卷会显示为已锁定，并且需要手动解锁。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-245">The volumes will appear locked and need to be manually unlocked.</span></span> <span data-ttu-id="6dcc0-246">这可以在安装了 OEM DRA.pfx 证书的任何计算机上 (包含在[DeviceLockDown 示例](https://github.com/ms-iot/security/tree/master/TurnkeySecurity))。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-246">This can be done on any machine that has the OEM-DRA.pfx certificate installed (included in the [DeviceLockDown sample](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)).</span></span> <span data-ttu-id="6dcc0-247">安装 PFX，然后在管理 CMD 提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="6dcc0-247">Install the PFX and then run the following commands from an administrative CMD prompt:</span></span>

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

<span data-ttu-id="6dcc0-248">如果要经常离线访问内容，可以使用以下命令在初始解锁后设置卷的 BitLocker 自动解锁：</span><span class="sxs-lookup"><span data-stu-id="6dcc0-248">If the contents need to be frequently accessed offline, BitLocker autounlock can be set up for the volumes after the initial unlock using the following commands:</span></span>

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a><span data-ttu-id="6dcc0-249">禁用 BitLocker</span><span class="sxs-lookup"><span data-stu-id="6dcc0-249">Disabling BitLocker</span></span>

<span data-ttu-id="6dcc0-250">一旦要临时禁用 BitLocker，请通过 IoT 设备初始化远程 PowerShell 会话，并运行以下命令：`sectask.exe -disable`。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-250">Should there arise a need to temporarily disable BitLocker, initate a remote PowerShell session with your IoT device and run the following command: `sectask.exe -disable`.</span></span>  
<span data-ttu-id="6dcc0-251">**注意：** 除非计划的加密任务处于禁用状态，将在以后的设备启动重新启用设备加密。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-251">**Note:** Device encryption will be re-enabled on subsequent device boot unless the scheduled encryption task is disabled.</span></span>

### <a name="disabling-device-guard"></a><span data-ttu-id="6dcc0-252">禁用 Device Guard</span><span class="sxs-lookup"><span data-stu-id="6dcc0-252">Disabling Device Guard</span></span>

<span data-ttu-id="6dcc0-253">交钥匙安全脚本的文件夹中生成 SIPolicyOn.p7b 和 SIPolicyOff.p7b 文件。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-253">The turnkey security script generates SIPolicyOn.p7b and SIPolicyOff.p7b files in the folder.</span></span>
<span data-ttu-id="6dcc0-254">Wm.xml 打包 SIPolicyOn.p7b，并将其放在与 SIPolicy.p7b 系统上。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-254">The wm.xml packages the SIPolicyOn.p7b and places it on the system as SIPolicy.p7b.</span></span>

<span data-ttu-id="6dcc0-255">例如：</span><span class="sxs-lookup"><span data-stu-id="6dcc0-255">For example:</span></span>

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

<span data-ttu-id="6dcc0-256">如果创建的包将 SIPolicyOff.p7b 文件并将其放置作为 SIPolicy.p7b，它会应用于此包和 Device Guard 将关闭。</span><span class="sxs-lookup"><span data-stu-id="6dcc0-256">If you create a package that takes the SIPolicyOff.p7b file and places it as a SIPolicy.p7b, it will apply this package and the Device Guard will be turned off.</span></span>



