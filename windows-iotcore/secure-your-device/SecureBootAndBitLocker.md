---
title: 启用安全启动、 BitLocker 和 Windows 10 IoT Core 上的设备保护
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何启用安全引导、 BitLocker 和 Windows 10 IoT Core 上的 Device Guard
keywords: windows iot，安全启动，BitLocker，设备保护、 安全性、 交钥匙安全
ms.openlocfilehash: 957b81a0a5bc032c62fa75598418778862fdf76d
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533345"
---
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a><span data-ttu-id="bfd15-104">启用安全启动、 BitLocker 和 Windows 10 IoT Core 上的设备保护</span><span class="sxs-lookup"><span data-stu-id="bfd15-104">Enabling Secure Boot, BitLocker, and Device Guard on Windows 10 IoT Core</span></span>

<span data-ttu-id="bfd15-105">Windows 10 IoT Core 现在包括如 UEFI 安全引导、 BitLocker 设备加密和 Device Guard 推出的安全功能。</span><span class="sxs-lookup"><span data-stu-id="bfd15-105">Windows 10 IoT Core now includes security feature offerings such as UEFI Secure Boot, BitLocker Device Encryption and Device Guard.</span></span>  <span data-ttu-id="bfd15-106">这些将帮助设备构建者创建完全锁定 Windows IoT 设备时可复原的许多不同类型的攻击。</span><span class="sxs-lookup"><span data-stu-id="bfd15-106">These will assist device builders in creating fully locked down Windows IoT devices that are resilient to many different types of attacks.</span></span>  <span data-ttu-id="bfd15-107">同时，这些功能提供最佳保护，以确保一个平台，将启动中定义的方式，同时锁定未知的二进制文件和保护用户数据，通过使用设备加密。</span><span class="sxs-lookup"><span data-stu-id="bfd15-107">Together, these features provide the optimal protection that ensures that a platform will launch in a defined way, while locking out unknown binaries and protecting user data through the use of device encryption.</span></span>

## <a name="boot-order"></a><span data-ttu-id="bfd15-108">启动顺序</span><span class="sxs-lookup"><span data-stu-id="bfd15-108">Boot Order</span></span>

<span data-ttu-id="bfd15-109">我们可以深入了解为 IoT 设备提供安全的平台的各个组件，还需要了解的 Windows 10 IoT Core 设备上的启动顺序。</span><span class="sxs-lookup"><span data-stu-id="bfd15-109">An understanding of the boot order on a Windows 10 IoT Core device is needed before we can delve into the individual components that provide a secure platform for the IoT device.</span></span>

<span data-ttu-id="bfd15-110">有三个主要区域发生从 IoT 设备时已启动的一直到 OS 内核加载和已安装的应用程序的执行。</span><span class="sxs-lookup"><span data-stu-id="bfd15-110">There are three main areas that occur from when an IoT device is powered on, all the way through to the OS kernel loading and execution of installed application.</span></span>

* <span data-ttu-id="bfd15-111">平台安全启动</span><span class="sxs-lookup"><span data-stu-id="bfd15-111">Platform Secure Boot</span></span>
* <span data-ttu-id="bfd15-112">统一可扩展固件接口 (UEFI) 安全启动</span><span class="sxs-lookup"><span data-stu-id="bfd15-112">Unified Extensible Firmware Interface (UEFI) Secure Boot</span></span>
* <span data-ttu-id="bfd15-113">Windows 代码完整性</span><span class="sxs-lookup"><span data-stu-id="bfd15-113">Windows Code Integrity</span></span>

![仪表板的屏幕截图](../media/SecureBootAndBitLocker/BootOrder.jpg)

<span data-ttu-id="bfd15-115">可在 Windows 10 启动过程的其他信息[此处](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process)。</span><span class="sxs-lookup"><span data-stu-id="bfd15-115">Additional information on the Windows 10 boot process can be found [here](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process).</span></span>

## <a name="locking-down-iot-devices"></a><span data-ttu-id="bfd15-116">锁定 IoT 设备</span><span class="sxs-lookup"><span data-stu-id="bfd15-116">Locking-down IoT Devices</span></span>

<span data-ttu-id="bfd15-117">为了锁定 Windows IoT 设备，必须考虑以下注意事项。</span><span class="sxs-lookup"><span data-stu-id="bfd15-117">In order to lockdown a Windows IoT device, the following considerations must be made.</span></span>

### <a name="platform-secure-boot"></a><span data-ttu-id="bfd15-118">平台安全启动</span><span class="sxs-lookup"><span data-stu-id="bfd15-118">Platform Secure Boot</span></span>

<span data-ttu-id="bfd15-119">第一次打开设备，整个引导过程的第一步时，加载并运行固件的引导加载程序，在初始化硬件设备，并提供紧急闪烁的功能。</span><span class="sxs-lookup"><span data-stu-id="bfd15-119">When the device is first powered on, the first step in the overall boot process is to load and run firmware boot loaders, which initialize the hardware on the devies and provide emergency flashing functionality.</span></span> <span data-ttu-id="bfd15-120">然后加载 UEFI 环境，控制将传递。</span><span class="sxs-lookup"><span data-stu-id="bfd15-120">The UEFI environment is then loaded and control is handed over.</span></span>

<span data-ttu-id="bfd15-121">这些固件的引导加载程序是特定于 SoC 的因此将需要使用适当的设备制造商能够在设备上创建这些的引导加载程序。</span><span class="sxs-lookup"><span data-stu-id="bfd15-121">These firmware boot loaders are SoC-specific, so you will need to work with the appropriate device manufacturer to have these boot loaders created on the device.</span></span>

### <a name="uefi-secure-boot"></a><span data-ttu-id="bfd15-122">UEFI 安全启动</span><span class="sxs-lookup"><span data-stu-id="bfd15-122">UEFI Secure Boot</span></span>

<span data-ttu-id="bfd15-123">UEFI 安全启动是第一个策略强制点，并且位于在 UEFI 中。</span><span class="sxs-lookup"><span data-stu-id="bfd15-123">UEFI Secure Boot is the first policy enforcement point, and is located in UEFI.</span></span>  <span data-ttu-id="bfd15-124">它将限制为只允许指定的颁发机构，如固件驱动程序、 选项 Rom、 UEFI 驱动程序或应用程序和 UEFI 的引导加载程序签名的二进制文件执行的系统。</span><span class="sxs-lookup"><span data-stu-id="bfd15-124">It restricts the system to only allow execution of binaries signed by a specified authority, such as firmware drivers, option ROMs, UEFI drivers or applications, and UEFI boot loaders.</span></span> <span data-ttu-id="bfd15-125">此功能可以阻止在平台上执行未知代码，也可以阻止未知代码削弱它的安全状况。</span><span class="sxs-lookup"><span data-stu-id="bfd15-125">This feature prevents unknown code from being executed on the platform and potentially weakening the security posture of it.</span></span> <span data-ttu-id="bfd15-126">安全启动到该设备，如 rootkit 减少预启动恶意软件攻击的风险。</span><span class="sxs-lookup"><span data-stu-id="bfd15-126">Secure Boot reduces the risk of pre-boot malware attacks to the device, such as rootkits.</span></span> 

<span data-ttu-id="bfd15-127">作为 OEM，您需要用于存储数据库上的 IoT 设备制造时间 UEFI 安全引导。</span><span class="sxs-lookup"><span data-stu-id="bfd15-127">As the OEM, you need to store the UEFI Secure Boot databases on the IoT device at manufacture time.</span></span> <span data-ttu-id="bfd15-128">这些数据库包括签名数据库 (db)、 撤消签名数据库 (dbx) 和密钥注册密钥数据库 (KEK)。</span><span class="sxs-lookup"><span data-stu-id="bfd15-128">These databases include the Signature database (db), Revoked Signature database (dbx), and the Key Enrollment Key database (KEK).</span></span> <span data-ttu-id="bfd15-129">这些数据库存储在设备的固件非易失性内存 （NV 内存）。</span><span class="sxs-lookup"><span data-stu-id="bfd15-129">These databases are stored on the firmware nonvolatile RAM (NV-RAM) of the device.</span></span>

* <span data-ttu-id="bfd15-130">**签名数据库 (db):** 这将列出的签名者或操作系统加载程序、 UEFI 应用程序和 UEFI 驱动程序允许在设备上加载的映像哈希</span><span class="sxs-lookup"><span data-stu-id="bfd15-130">**Signature Database (db):** This lists the signers or image hashes of operating system loaders, UEFI applications and UEFI drivers that are allowed to be loaded on the device</span></span>

* <span data-ttu-id="bfd15-131">**已撤消的签名数据库 (dbx):** 这将列出的签名者或操作系统加载程序、 UEFI 应用程序和 UEFI 驱动程序，将不再受信任的它们是映像哈希*不*允许在设备上加载</span><span class="sxs-lookup"><span data-stu-id="bfd15-131">**Revoked Signature Database (dbx):** This lists the signers or image hashes of operating system loaders, UEFI applications and UEFI drivers that are no longer trusted, and are *NOT* allowed to be loaded on the device</span></span> 

* <span data-ttu-id="bfd15-132">**密钥注册密钥数据库 (KEK):** 包含签名密钥，可用于更新签名且撤消签名数据库的列表。</span><span class="sxs-lookup"><span data-stu-id="bfd15-132">**Key Enrollment Key database (KEK):** Contains a list of signing keys that can be used to update the signature and revoked signature databases.</span></span>

<span data-ttu-id="bfd15-133">一旦这些数据库都创建并添加到设备，OEM 锁定编辑，固件，并生成一个签名密钥 (PK) 的平台。</span><span class="sxs-lookup"><span data-stu-id="bfd15-133">Once these databases are created and added to the device, the OEM locks the firmware from editing, and generates a platform signing key (PK).</span></span> <span data-ttu-id="bfd15-134">Kek 的更新进行签名，或禁用 UEFI 安全引导，可以使用此密钥。</span><span class="sxs-lookup"><span data-stu-id="bfd15-134">This key can be used to sign updates to the KEK or to disable UEFI Secure Boot.</span></span>

<span data-ttu-id="bfd15-135">下面是 UEFI 安全引导所采取的步骤：</span><span class="sxs-lookup"><span data-stu-id="bfd15-135">Here are the steps taken by UEFI Secure Boot:</span></span>

1. <span data-ttu-id="bfd15-136">设备已开机后，签名数据库每个检查针对签名密钥 (PK) 平台。</span><span class="sxs-lookup"><span data-stu-id="bfd15-136">After the device is powered on, the signature databases are each checked against the platform signing key (PK).</span></span>
2. <span data-ttu-id="bfd15-137">如果固件不受信任，UEFI 固件启动特定于 OEM 恢复以还原受信任的固件。</span><span class="sxs-lookup"><span data-stu-id="bfd15-137">If the firmware isn't trusted, UEFI firmware initiates OEM-specific recovery to restore trusted firmware.</span></span>
3. <span data-ttu-id="bfd15-138">如果无法加载 Windows 启动管理器，固件将尝试启动的 Windows 启动管理器中的备份副本。</span><span class="sxs-lookup"><span data-stu-id="bfd15-138">If Windows Boot Manager cannot be loaded, the firmware will attempt to boot a backup copy of Windows Boot Manager.</span></span> <span data-ttu-id="bfd15-139">如果这也将失败，UEFI 固件启动特定于 OEM 的修正。</span><span class="sxs-lookup"><span data-stu-id="bfd15-139">If this also fails, the UEFI firmware initiates OEM-specific remediation.</span></span>
4. <span data-ttu-id="bfd15-140">Windows 启动管理器运行和验证 Windows 内核的数字签名。</span><span class="sxs-lookup"><span data-stu-id="bfd15-140">Windows Boot Manager runs and verifies the digital signature of the Windows Kernel.</span></span> <span data-ttu-id="bfd15-141">如果受信任的 Windows 启动管理器会将控制传递给 Windows 内核中。</span><span class="sxs-lookup"><span data-stu-id="bfd15-141">If trusted, Windows Boot Manager passes control to the Windows Kernel.</span></span>


<span data-ttu-id="bfd15-142">更多详细信息安全启动以及密钥创建和管理指南，位于[此处](https://technet.microsoft.com/library/dn747883.aspx)。</span><span class="sxs-lookup"><span data-stu-id="bfd15-142">Additional details on Secure Boot, along with key creation and management guidance, is available [here](https://technet.microsoft.com/library/dn747883.aspx).</span></span>

### <a name="windows-code-integrity"></a><span data-ttu-id="bfd15-143">Windows 代码完整性</span><span class="sxs-lookup"><span data-stu-id="bfd15-143">Windows Code Integrity</span></span>

<span data-ttu-id="bfd15-144">Windows 代码完整性 (WCI) 验证驱动程序或应用程序每次加载到内存的完整性，从而可以增强操作系统的安全性。</span><span class="sxs-lookup"><span data-stu-id="bfd15-144">Windows Code Integrity (WCI) improves the security of the operating system by validating the integrity of a driver or application each time it is loaded into memory.</span></span> <span data-ttu-id="bfd15-145">CI 不含两个主要组件的内核模式代码完整性 (KMCI) 和用户模式代码完整性 (UMCI)。</span><span class="sxs-lookup"><span data-stu-id="bfd15-145">CI contains two main components - Kernel Mode Code Integrity (KMCI) and User Mode Code Integrity (UMCI).</span></span>

<span data-ttu-id="bfd15-146">可配置代码完整性 (CCI) 是一项功能在 Windows 10 中，允许设备的设备构建者为锁定，并仅允许它运行和执行签名和受信任的代码。</span><span class="sxs-lookup"><span data-stu-id="bfd15-146">Configurable Code Integrity (CCI) is a feature in Windows 10 that allows device builders to lockdown a device and only allow it to run and execute code that is signed and trusted.</span></span>  <span data-ttu-id="bfd15-147">若要执行此操作，设备构建者可以 golden 设备 （硬件和软件的最终版本） 上创建的代码完整性策略保护并在工厂车间的所有设备上应用此策略。</span><span class="sxs-lookup"><span data-stu-id="bfd15-147">To do so, device builders can create a code integrity policy on a 'golden' device (final release version of hardware and software) and then secure and apply this policy on all devices on the factory floor.</span></span>

<span data-ttu-id="bfd15-148">若要了解有关部署代码完整性策略的详细信息，审核和强制执行，请查看最新的 technet 文档[此处](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps)。</span><span class="sxs-lookup"><span data-stu-id="bfd15-148">To learn more about deploying code integrity policies, auditing and enforcement, check out the latest technet documentation [here](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps).</span></span>

<span data-ttu-id="bfd15-149">下面是由 Windows 代码完整性所采取的步骤：</span><span class="sxs-lookup"><span data-stu-id="bfd15-149">Here are the steps taken by Windows Code Integrity:</span></span>

1. <span data-ttu-id="bfd15-150">Windows 内核将验证对签名的数据库加载之前的所有其他组件。</span><span class="sxs-lookup"><span data-stu-id="bfd15-150">Windows Kernel will verify all other components against the signature database before loading.</span></span> <span data-ttu-id="bfd15-151">这包括驱动程序、 启动文件和 ELAM （早期启动反恶意软件）。</span><span class="sxs-lookup"><span data-stu-id="bfd15-151">This includes drivers, startup files and ELAM (Early Launch Anti-Malware).</span></span>
2. <span data-ttu-id="bfd15-152">Windows 内核将加载在启动过程中，受信任的组件，并禁止不受信任的组件的加载。</span><span class="sxs-lookup"><span data-stu-id="bfd15-152">Windows Kernel will load the trusted components in the startup process, and prohibit loading of the untrusted components.</span></span>
3. <span data-ttu-id="bfd15-153">将加载 Windows 10 IoT 核心版操作系统，以及任何已安装的应用程序。</span><span class="sxs-lookup"><span data-stu-id="bfd15-153">Windows 10 IoT Core operating system loads, along with any installed applications.</span></span>

### <a name="bitlocker-device-encryption"></a><span data-ttu-id="bfd15-154">BitLocker 设备加密</span><span class="sxs-lookup"><span data-stu-id="bfd15-154">BitLocker Device Encryption</span></span>

<span data-ttu-id="bfd15-155">Windows 10 IoT Core 还实现 BitLocker 设备加密，保护免受脱机攻击的 IoT 设备的轻量版本。</span><span class="sxs-lookup"><span data-stu-id="bfd15-155">Windows 10 IoT Core also implements a lightweight version of BitLocker Device Encryption, protecting IoT devices against offline attacks.</span></span> <span data-ttu-id="bfd15-156">此功能存在的平台，包括执行必要的度量的 UEFI 中的必要预操作系统协议上的 TPM 存在强的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="bfd15-156">This capability has a strong dependency on the presence of a TPM on the platform, including the necessary pre-OS protocol in UEFI that conducts the necessary measurements.</span></span> <span data-ttu-id="bfd15-157">这些预操作系统度量可确保 OS 今后拥有的操作系统已启动方式; 明确记录但是，它不会强制执行的任何限制。</span><span class="sxs-lookup"><span data-stu-id="bfd15-157">These pre-OS measurements ensure that the OS later has a definitive record of how the OS was launched; however, it does not enforce any execution restrictions.</span></span>

> [!TIP]
> <span data-ttu-id="bfd15-158">在 Windows 10 IoT Core 上的 BitLocker 功能允许基于 NTFS 的 OS 卷时绑定到它的所有可用 NTFS 数据卷的自动加密的。</span><span class="sxs-lookup"><span data-stu-id="bfd15-158">BitLocker functionality on Windows 10 IoT Core allows for automatic encryption of NTFS-based OS volume while binding all available NTFS data volumes to it.</span></span> <span data-ttu-id="bfd15-159">为此，它是为了确保 EFIESP 卷 GUID 将设置为_C12A7328-F81F-11D2-BA4B-00A0C93EC93B_。</span><span class="sxs-lookup"><span data-stu-id="bfd15-159">For this, it’s necessary to ensure that the EFIESP volume GUID is set to _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_.</span></span>

### <a name="device-guard-on-windows-iot-core"></a><span data-ttu-id="bfd15-160">在 Windows IoT Core 上的设备保护</span><span class="sxs-lookup"><span data-stu-id="bfd15-160">Device Guard on Windows IoT Core</span></span>

<span data-ttu-id="bfd15-161">大多数 IoT 设备是作为固定功能的设备。</span><span class="sxs-lookup"><span data-stu-id="bfd15-161">Most IoT devices are built as fixed-function devices.</span></span> <span data-ttu-id="bfd15-162">这意味着设备构建者知道确切的固件、 操作系统、 驱动程序和应用程序应运行在给定设备上。</span><span class="sxs-lookup"><span data-stu-id="bfd15-162">This implies that device builders know exactly which firmware, operating system, drivers and applications should be running on a given device.</span></span> <span data-ttu-id="bfd15-163">随后，可以将此信息用于完全锁定 IoT 设备通过仅允许已知且受信任代码的执行。</span><span class="sxs-lookup"><span data-stu-id="bfd15-163">In turn, this information can be used to fully lockdown an IoT device by only allowing execution of known and trusted code.</span></span> <span data-ttu-id="bfd15-164">在 Windows 10 IoT Core 上的设备保护可帮助保护 IoT 设备通过确保未知或不受信任的可执行代码，不能锁定的设备上运行。</span><span class="sxs-lookup"><span data-stu-id="bfd15-164">Device Guard on Windows 10 IoT Core can help protect IoT devices by ensuring that unknown or untrusted executable code cannot be run on locked-down devices.</span></span>


## <a name="turnkey-security-on-iot-core"></a><span data-ttu-id="bfd15-165">在 IoT Core 上的关守安全</span><span class="sxs-lookup"><span data-stu-id="bfd15-165">Turnkey Security on IoT Core</span></span>

<span data-ttu-id="bfd15-166">为了便于轻松启用 IoT Core 设备上的主要安全功能，Microsoft 将提供统包的安全包，允许设备生成器以生成完全锁定 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="bfd15-166">To facilitate easy enablement of key security features on IoT Core devices, Microsoft is providing a turnkey 'Security Package' that allows device builders to build fully locked down IoT devices.</span></span>  <span data-ttu-id="bfd15-167">此包将帮助了解：</span><span class="sxs-lookup"><span data-stu-id="bfd15-167">This package will help with:</span></span>

* <span data-ttu-id="bfd15-168">预配安全启动密钥和受支持的 IoT 平台上启用功能</span><span class="sxs-lookup"><span data-stu-id="bfd15-168">Provisioning Secure Boot keys and enabling the feature on supported IoT platforms</span></span>
* <span data-ttu-id="bfd15-169">安装和配置使用 BitLocker 设备加密</span><span class="sxs-lookup"><span data-stu-id="bfd15-169">Setup and configuration of device encryption using BitLocker</span></span> 
* <span data-ttu-id="bfd15-170">启动设备锁定为只允许已签名的应用程序和驱动程序的执行</span><span class="sxs-lookup"><span data-stu-id="bfd15-170">Initiating device lockdown to only allow execution of signed applications and drivers</span></span>

### <a name="prerequisites"></a><span data-ttu-id="bfd15-171">先决条件</span><span class="sxs-lookup"><span data-stu-id="bfd15-171">Prerequisites</span></span>

* <span data-ttu-id="bfd15-172">运行 Windows 10 企业版的 PC</span><span class="sxs-lookup"><span data-stu-id="bfd15-172">A PC running Windows 10 Enterprise</span></span>
* <span data-ttu-id="bfd15-173">[Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) -必需的证书生成</span><span class="sxs-lookup"><span data-stu-id="bfd15-173">[Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) - Required for Certificate Generation</span></span>
* <span data-ttu-id="bfd15-174">[Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) -必需 CAB 生成</span><span class="sxs-lookup"><span data-stu-id="bfd15-174">[Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) - Required for CAB generation</span></span>
* <span data-ttu-id="bfd15-175">参考平台的发布的硬件与传送固件、 操作系统、 驱动程序和应用程序将是所必需的最后一个锁定</span><span class="sxs-lookup"><span data-stu-id="bfd15-175">Reference platform - release hardware with shipping firmware, OS, drivers and applications will be required for final lockdown</span></span>

### <a name="development-iot-devices"></a><span data-ttu-id="bfd15-176">开发 IoT 设备</span><span class="sxs-lookup"><span data-stu-id="bfd15-176">Development IoT Devices</span></span>

<span data-ttu-id="bfd15-177">Windows 10 IoT 核心版适用于在数百个设备中利用的各种 silicons。</span><span class="sxs-lookup"><span data-stu-id="bfd15-177">Windows 10 IoT Core works with various silicons that are utilized in hundreds of devices.</span></span> <span data-ttu-id="bfd15-178">[建议的 IoT 开发设备](../learn-about-hardware/SoCsAndCustomBoards.md)，下面提供了默认情况下，安全引导、 标准引导、 BitLocker 和 Device Guard 功能以及固件 TPM 功能：</span><span class="sxs-lookup"><span data-stu-id="bfd15-178">Of the [suggested IoT development devices](../learn-about-hardware/SoCsAndCustomBoards.md), the following provide firmware TPM functionality out of the box, along with Secure Boot, Measured Boot, BitLocker and Device Guard capabilities:</span></span>

* <span data-ttu-id="bfd15-179">Qualcomm DragonBoard 410c</span><span class="sxs-lookup"><span data-stu-id="bfd15-179">Qualcomm DragonBoard 410c</span></span>

    <span data-ttu-id="bfd15-180">为了启用安全启动，可能需要预配 RPMB。</span><span class="sxs-lookup"><span data-stu-id="bfd15-180">In order to enable Secure Boot, it may be necessary to provision RPMB.</span></span> <span data-ttu-id="bfd15-181">一旦已经使用 Windows 10 IoT Core 刷新 eMMC (按说明[此处](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c)，按 [Power] + [期 +] + [期-] BDS 菜单从打开电源启动并选择"预配 RPMB"时在设备上同时。</span><span class="sxs-lookup"><span data-stu-id="bfd15-181">Once the eMMC has been flashed with Windows 10 IoT Core (as per instructions [here](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), press [Power] + [Vol+] + [Vol-] simultaneously on the device when powering up and select "Provision RPMB" from the BDS menu.</span></span> <span data-ttu-id="bfd15-182">*请注意此步骤不可恢复。*</span><span class="sxs-lookup"><span data-stu-id="bfd15-182">*Please note that this is an irreversible step.*</span></span>

* <span data-ttu-id="bfd15-183">Intel MinnowBoardMax</span><span class="sxs-lookup"><span data-stu-id="bfd15-183">Intel MinnowBoardMax</span></span>

    <span data-ttu-id="bfd15-184">Intel 的 MinnowBoard Max 固件版本必须为 0.82 或更高版本 (获取[最新的固件](https://firmware.intel.com/projects/minnowboard-max))。</span><span class="sxs-lookup"><span data-stu-id="bfd15-184">For Intel's MinnowBoard Max, firmware version must be 0.82 or higher (get the [latest firmware](https://firmware.intel.com/projects/minnowboard-max)).</span></span> <span data-ttu-id="bfd15-185">若要启用 TPM 功能，请打开附加了键盘和屏幕的开发板的电源，然后按 F2 进入 UEFI 设置。</span><span class="sxs-lookup"><span data-stu-id="bfd15-185">To enable TPM capabilities, power up board with a keyboard & display attached and press F2 to enter UEFI setup.</span></span> <span data-ttu-id="bfd15-186">转到_设备管理器-> 系统设置-> 安全配置-> PTT_并将其设置为_&lt;启用&gt;_。</span><span class="sxs-lookup"><span data-stu-id="bfd15-186">Go to _Device Manager -> System Setup -> Security Configuration -> PTT_ and set it to _&lt;Enable&gt;_.</span></span> <span data-ttu-id="bfd15-187">按 F10 保存更改，并继续重新启动平台。</span><span class="sxs-lookup"><span data-stu-id="bfd15-187">Press F10 to save changes and proceed with a reboot of the platform.</span></span>

> [!NOTE]
> <span data-ttu-id="bfd15-188">Raspberry Pi 2 或 3 不支持 TPM，因此我们不能配置锁定方案。</span><span class="sxs-lookup"><span data-stu-id="bfd15-188">Raspberry Pi 2 nor 3 do not support TPM and so we cannot configure Lockdown scenarios.</span></span>

### <a name="generate-lockdown-packages"></a><span data-ttu-id="bfd15-189">生成锁定包</span><span class="sxs-lookup"><span data-stu-id="bfd15-189">Generate Lockdown Packages</span></span>

1. <span data-ttu-id="bfd15-190">下载[DeviceLockDown 脚本](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)包，其中包含的所有其他工具和脚本所需的配置并锁定设备</span><span class="sxs-lookup"><span data-stu-id="bfd15-190">Download the [DeviceLockDown Script](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) package, which contains all of the additional tools and scripts required for configuring and locking down devices</span></span>
2. <span data-ttu-id="bfd15-191">在 Windows 10 PC 上启动管理 PowerShell (PS) 控制台并导航到下载的脚本的位置。</span><span class="sxs-lookup"><span data-stu-id="bfd15-191">Start an Administrative PowerShell (PS) console on your Windows 10 PC and navigate to the location of the downloaded script.</span></span>
3. <span data-ttu-id="bfd15-192">将引用硬件平台 （运行解锁的图像） 装载到您的 PC 通过使用网络共享</span><span class="sxs-lookup"><span data-stu-id="bfd15-192">Mount your reference hardware platform (running the unlocked image) to your PC via network share using</span></span>

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. <span data-ttu-id="bfd15-193">为设备使用生成密钥</span><span class="sxs-lookup"><span data-stu-id="bfd15-193">Generate keys for your device using</span></span>

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * <span data-ttu-id="bfd15-194">在具有相应后缀指定的输出文件夹中生成密钥和证书。</span><span class="sxs-lookup"><span data-stu-id="bfd15-194">The keys and certificates are generated in the specified output folder with appropriate suffix.</span></span>
    * <span data-ttu-id="bfd15-195">**确保生成的密钥的安全**如设备将信任二进制文件在锁定后才使用这些密钥进行签名。</span><span class="sxs-lookup"><span data-stu-id="bfd15-195">**Secure your generated keys** as the device will trust binaries signed with these keys only after lockdown.</span></span>
    * <span data-ttu-id="bfd15-196">你可以跳过此步骤和仅供测试使用预生成的密钥</span><span class="sxs-lookup"><span data-stu-id="bfd15-196">You may skip this step and use the pre-generated keys for testing only</span></span>

5. <span data-ttu-id="bfd15-197">配置_settings.xml_</span><span class="sxs-lookup"><span data-stu-id="bfd15-197">Configure _settings.xml_</span></span>

    * <span data-ttu-id="bfd15-198">常规部分：指定包目录</span><span class="sxs-lookup"><span data-stu-id="bfd15-198">General section : Specify the package directories</span></span>
    * <span data-ttu-id="bfd15-199">工具部分：设置工具的路径</span><span class="sxs-lookup"><span data-stu-id="bfd15-199">Tools section : Set the path for the tools</span></span>
        * <span data-ttu-id="bfd15-200">Windows10KitsRoot `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`</span><span class="sxs-lookup"><span data-stu-id="bfd15-200">Windows10KitsRoot `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`</span></span>
        * <span data-ttu-id="bfd15-201">WindowsSDKVersion `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`</span><span class="sxs-lookup"><span data-stu-id="bfd15-201">WindowsSDKVersion `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`</span></span>
            * <span data-ttu-id="bfd15-202">在计算机上安装的 SDK 版本低于 `C:\Program Files (x86)\Windows Kits\10\`</span><span class="sxs-lookup"><span data-stu-id="bfd15-202">SDK version installed on your machine is under `C:\Program Files (x86)\Windows Kits\10\`</span></span>
    * <span data-ttu-id="bfd15-203">SecureBoot 部分：指定要用于安全启动 （PK 和 SB 键） 的键</span><span class="sxs-lookup"><span data-stu-id="bfd15-203">SecureBoot section : Specify which keys to use for secure boot (PK and SB keys)</span></span>
    * <span data-ttu-id="bfd15-204">BitLocker 部分：指定 Bitlocker 数据恢复 （DRA 密钥） 的证书</span><span class="sxs-lookup"><span data-stu-id="bfd15-204">BitLocker section : Specify a certificate for Bitlocker data recovery (DRA key)</span></span>
    * <span data-ttu-id="bfd15-205">SIPolicy 部分：指定应为受信任的证书</span><span class="sxs-lookup"><span data-stu-id="bfd15-205">SIPolicy section : Specify certs that should be trusted</span></span>
        * <span data-ttu-id="bfd15-206">ScanPath:用于扫描二进制文件，设备的路径 `\\a.b.c.d\C$`</span><span class="sxs-lookup"><span data-stu-id="bfd15-206">ScanPath : Path of the device for scanning binaries , `\\a.b.c.d\C$`</span></span>
        * <span data-ttu-id="bfd15-207">更新：签名者的 SIPolicy （PAUTH 键）</span><span class="sxs-lookup"><span data-stu-id="bfd15-207">Update   : Signer of the SIPolicy (PAUTH keys)</span></span>
        * <span data-ttu-id="bfd15-208">用户：用户模式证书 （UMCI 键）</span><span class="sxs-lookup"><span data-stu-id="bfd15-208">User     : User mode certificates (UMCI keys)</span></span> 
        * <span data-ttu-id="bfd15-209">内核：内核模式证书 （KMCI 键）</span><span class="sxs-lookup"><span data-stu-id="bfd15-209">Kernel   : Kernel mode certificates (KMCI keys)</span></span>
    * <span data-ttu-id="bfd15-210">打包：指定包生成设置</span><span class="sxs-lookup"><span data-stu-id="bfd15-210">Packaging : Specify the settings for the package generation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bfd15-211">为了帮助测试初始开发周期内，Microsoft 已提供预生成的密钥和证书，在适当的位置。</span><span class="sxs-lookup"><span data-stu-id="bfd15-211">In order to assist with testing during the initial development cycle, Microsoft has provided pre-generated keys and certificates where appropriate.</span></span>  <span data-ttu-id="bfd15-212">这意味着 Microsoft 测试、 开发和预发布二进制文件被视为受信任。</span><span class="sxs-lookup"><span data-stu-id="bfd15-212">This implies that Microsoft Test, Development and Pre-Release binaries are considered trusted.</span></span>  <span data-ttu-id="bfd15-213">在最终产品创建和生成图像，请确保删除这些证书并使用你自己的密钥以确保完全锁定的设备。</span><span class="sxs-lookup"><span data-stu-id="bfd15-213">During final product creation and image generation, be sure to remove these certifcates and use your own keys to ensure a fully locked down device.</span></span>

<span data-ttu-id="bfd15-214">6.执行以下命令以生成所需的包：</span><span class="sxs-lookup"><span data-stu-id="bfd15-214">6.Execute the following commands to generate required packages:</span></span>

    ```powershell
    Import-Module .\IoTTurnkeySecurity.psm1
    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml
    (or)
    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
    ```

### <a name="test-lockdown-packages"></a><span data-ttu-id="bfd15-215">测试锁定包</span><span class="sxs-lookup"><span data-stu-id="bfd15-215">Test Lockdown packages</span></span>
<span data-ttu-id="bfd15-216">可以通过手动安装它们未锁定的设备上通过以下步骤来测试生成的包</span><span class="sxs-lookup"><span data-stu-id="bfd15-216">You can test the generated packages by manually installing them on a unlocked device by the following steps</span></span>

1. <span data-ttu-id="bfd15-217">Flash 解锁映像 （用于扫描前面的步骤中的映像） 的设备。</span><span class="sxs-lookup"><span data-stu-id="bfd15-217">Flash the device with the unlocked image (image used for scanning in earlier step).</span></span>
2. <span data-ttu-id="bfd15-218">连接到设备 ([使用 SSH](../connect-your-device/SSH.md)或使用[Powershell](../connect-your-device/PowerShell.md))</span><span class="sxs-lookup"><span data-stu-id="bfd15-218">Connect to the device ([using SSH](../connect-your-device/SSH.md) or using [Powershell](../connect-your-device/PowerShell.md))</span></span>
3. <span data-ttu-id="bfd15-219">例如以下的.cab 文件复制到的目录下的设备 `c:\OemInstall`</span><span class="sxs-lookup"><span data-stu-id="bfd15-219">Copy the following .cab files to the device under a directory e.g. `c:\OemInstall`</span></span>
    * <span data-ttu-id="bfd15-220">OEM.Custom.Cmd.cab</span><span class="sxs-lookup"><span data-stu-id="bfd15-220">OEM.Custom.Cmd.cab</span></span>
    * <span data-ttu-id="bfd15-221">OEM.Security.BitLocker.cab</span><span class="sxs-lookup"><span data-stu-id="bfd15-221">OEM.Security.BitLocker.cab</span></span>
    * <span data-ttu-id="bfd15-222">OEM.Security.SecureBoot.cab</span><span class="sxs-lookup"><span data-stu-id="bfd15-222">OEM.Security.SecureBoot.cab</span></span>
    * <span data-ttu-id="bfd15-223">OEM.Security.DeviceGuard.cab</span><span class="sxs-lookup"><span data-stu-id="bfd15-223">OEM.Security.DeviceGuard.cab</span></span>
4. <span data-ttu-id="bfd15-224">启动临时生成的包的正在发送的以下命令</span><span class="sxs-lookup"><span data-stu-id="bfd15-224">Initiate staging of the generated packages by issueing the following commands</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    <span data-ttu-id="bfd15-225">如果你使用自定义映像，则你将需要*跳过*此文件，并手动编辑`c:\windows\system32\oemcustomization.cmd`中提供的内容`Output\OEMCustomization\OEMCustomization.cmd`文件</span><span class="sxs-lookup"><span data-stu-id="bfd15-225">If you are using custom image, then you will have to *skip* this file and manually edit the `c:\windows\system32\oemcustomization.cmd` with the contents available in `Output\OEMCustomization\OEMCustomization.cmd` file</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. <span data-ttu-id="bfd15-226">设备将重新启动进入更新 OS （显示齿轮） 来安装包，并将再次重新启动到主操作系统。</span><span class="sxs-lookup"><span data-stu-id="bfd15-226">The device will reboot into update OS (showing gears) to install the packages and will reboot again to main OS.</span></span>  <span data-ttu-id="bfd15-227">设备重启后恢复到 MainOS，将启用安全启动，并且应按 SIPolicy。</span><span class="sxs-lookup"><span data-stu-id="bfd15-227">Once the device reboots back into MainOS, Secure Boot will be enabled and SIPolicy should be engaged.</span></span>
7. <span data-ttu-id="bfd15-228">重新启动设备再次激活 Bitlocker 加密。</span><span class="sxs-lookup"><span data-stu-id="bfd15-228">Reboot the device again to activate the Bitlocker encryption.</span></span>
8. <span data-ttu-id="bfd15-229">测试的安全功能</span><span class="sxs-lookup"><span data-stu-id="bfd15-229">Test the security features</span></span>
    * <span data-ttu-id="bfd15-230">SecureBoot： 尝试`bcdedit /debug on`，您将获得一个错误，指出值受安全启动策略</span><span class="sxs-lookup"><span data-stu-id="bfd15-230">SecureBoot: try `bcdedit /debug on` , you will get an error stating that the value is protected by secure boot policy</span></span>
    * <span data-ttu-id="bfd15-231">BitLocker：运行`fvecon -status c:`，你将获得状态提及*上加密、 已恢复数据 （外部密钥）、 具有 TPM 数据、 安全、 启动分区、 仅已用空间*</span><span class="sxs-lookup"><span data-stu-id="bfd15-231">BitLocker: Run `fvecon -status c:`, you will get the status mentioning *On, Encrypted, Has Recovery Data (external key), Has TPM Data, Secure, Boot Partition, Used Space Only*</span></span>
    * <span data-ttu-id="bfd15-232">DeviceGuard:运行未签名的任何二进制文件或使用不在 SIPolicy 列表中的证书签名的二进制文件并确认它无法运行。</span><span class="sxs-lookup"><span data-stu-id="bfd15-232">DeviceGuard : Run any unsigned binary or a binary signed with certificate not in the SIPolicy list and confirm that it fails to run.</span></span>

### <a name="generate-lockdown-image"></a><span data-ttu-id="bfd15-233">生成锁定映像</span><span class="sxs-lookup"><span data-stu-id="bfd15-233">Generate Lockdown image</span></span>

<span data-ttu-id="bfd15-234">在验证之后锁定包正在根据前面定义的设置，然后，可以包括这些包到映像按照下面给出的步骤。</span><span class="sxs-lookup"><span data-stu-id="bfd15-234">After validating that the lockdown packages are working as per the settings defined earlier, you can then include these packages into the image by following the below given steps.</span></span> <span data-ttu-id="bfd15-235">读取[IoT 制造指南](https://aka.ms/iotcoreguide)有关自定义映像创建的说明。</span><span class="sxs-lookup"><span data-stu-id="bfd15-235">Read the [IoT manufacturing guide](https://aka.ms/iotcoreguide) for custom image creation instructions.</span></span>

1. <span data-ttu-id="bfd15-236">在工作区目录中，更新将在上述生成的输出目录中的以下文件</span><span class="sxs-lookup"><span data-stu-id="bfd15-236">In the workspace directory, update the following files from the generated output directory above</span></span>
    * <span data-ttu-id="bfd15-237">SecureBoot: `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`</span><span class="sxs-lookup"><span data-stu-id="bfd15-237">SecureBoot : `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`</span></span>
      * <span data-ttu-id="bfd15-238">SetVariable_db.bin</span><span class="sxs-lookup"><span data-stu-id="bfd15-238">SetVariable_db.bin</span></span>
      * <span data-ttu-id="bfd15-239">SetVariable_kek.bin</span><span class="sxs-lookup"><span data-stu-id="bfd15-239">SetVariable_kek.bin</span></span>
      * <span data-ttu-id="bfd15-240">SetVariable_pk.bin</span><span class="sxs-lookup"><span data-stu-id="bfd15-240">SetVariable_pk.bin</span></span>
    * <span data-ttu-id="bfd15-241">BitLocker: `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`</span><span class="sxs-lookup"><span data-stu-id="bfd15-241">BitLocker : `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`</span></span>
      * <span data-ttu-id="bfd15-242">DETask.xml</span><span class="sxs-lookup"><span data-stu-id="bfd15-242">DETask.xml</span></span>
      * <span data-ttu-id="bfd15-243">Security.Bitlocker.wm.xml</span><span class="sxs-lookup"><span data-stu-id="bfd15-243">Security.Bitlocker.wm.xml</span></span>
      * <span data-ttu-id="bfd15-244">setup.bitlocker.cmd</span><span class="sxs-lookup"><span data-stu-id="bfd15-244">setup.bitlocker.cmd</span></span>
    * <span data-ttu-id="bfd15-245">DeviceGuard: `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`</span><span class="sxs-lookup"><span data-stu-id="bfd15-245">DeviceGuard : `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`</span></span>
      * <span data-ttu-id="bfd15-246">SIPolicyOn.p7b</span><span class="sxs-lookup"><span data-stu-id="bfd15-246">SIPolicyOn.p7b</span></span>
      * <span data-ttu-id="bfd15-247">SIPolicyOff.p7b</span><span class="sxs-lookup"><span data-stu-id="bfd15-247">SIPolicyOff.p7b</span></span>
  
2. <span data-ttu-id="bfd15-248">锁定包功能 id 为 ProductName 目录下添加 RetailOEMInput.xml 和 TestOEMInput.xml</span><span class="sxs-lookup"><span data-stu-id="bfd15-248">Add RetailOEMInput.xml and TestOEMInput.xml under the ProductName directory with lockdown package feature ID</span></span>
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. <span data-ttu-id="bfd15-249">重新生成映像</span><span class="sxs-lookup"><span data-stu-id="bfd15-249">Re-generate Image</span></span>
    * <span data-ttu-id="bfd15-250">`buildpkg all` （这将生成基于以上策略文件的新锁定包）</span><span class="sxs-lookup"><span data-stu-id="bfd15-250">`buildpkg all` (this generates new lockdown packages based on above policy files)</span></span>
    * <span data-ttu-id="bfd15-251">`buildimage ProductName test(or)retail`  （这将生成新 Flash.ffu）</span><span class="sxs-lookup"><span data-stu-id="bfd15-251">`buildimage ProductName test(or)retail`  (this generates new Flash.ffu)</span></span>
4. <span data-ttu-id="bfd15-252">Flash 与此新 Flash.ffu 设备并验证的安全功能。</span><span class="sxs-lookup"><span data-stu-id="bfd15-252">Flash the device with this new Flash.ffu and validate the security features.</span></span>

<span data-ttu-id="bfd15-253">请参阅[SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample)作为锁定龙板配置的一个示例。</span><span class="sxs-lookup"><span data-stu-id="bfd15-253">See [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) as an example of a lockdown dragon board configuration.</span></span>

<span data-ttu-id="bfd15-254">或者，您可以在 IoTCore 外壳本身中生成的安全包，请参阅[添加的安全包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages)有关详细信息。</span><span class="sxs-lookup"><span data-stu-id="bfd15-254">Alternatively, you can generate the security packages in the IoTCore Shell itself, see [adding security packages](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) for the details.</span></span>


### <a name="developing-with-codesigning-enforcement-enabled"></a><span data-ttu-id="bfd15-255">使用已启用的代码签名强制进行开发</span><span class="sxs-lookup"><span data-stu-id="bfd15-255">Developing with CodeSigning Enforcement Enabled</span></span>

<span data-ttu-id="bfd15-256">生成包并激活锁定后，任何开发过程中引入到映像中的二进制文件需要正确地签名。</span><span class="sxs-lookup"><span data-stu-id="bfd15-256">Once the packages are generated and lockdown is activated, any binaries introduced into the image during development will need to be signed appropriately.</span></span> <span data-ttu-id="bfd15-257">确保您的用户模式的二进制文件进行签名具有键 _。 \Keys\ \* \* \*-UMCI.pfx_。</span><span class="sxs-lookup"><span data-stu-id="bfd15-257">Ensure that your user-mode binaries are signed with the key  _.\Keys\ \*\*\*-UMCI.pfx_.</span></span> <span data-ttu-id="bfd15-258">适用于签名的内核模式，如驱动程序，你将需要指定自己的签名密钥，请确保它们也包括上述 SIPolicy 中。</span><span class="sxs-lookup"><span data-stu-id="bfd15-258">For kernel-mode signing, such as for drivers, you’ll need to specify your own signing keys and make sure that they are also included in the SIPolicy above.</span></span>

### <a name="unlocking-encrypted-drives"></a><span data-ttu-id="bfd15-259">解锁加密的驱动器</span><span class="sxs-lookup"><span data-stu-id="bfd15-259">Unlocking Encrypted Drives</span></span>

<span data-ttu-id="bfd15-260">在开发和测试，当尝试读取内容从加密设备脱机 （例如 SD 卡 MinnowBoardMax 或 DragonBoard 的 eMMC 通过 USB 大容量存储模式为），diskpart 可用于将驱动器号分配给 MainOS 和数据量 （让我们假定 v 部分： MainOS 和 w： 数据）。</span><span class="sxs-lookup"><span data-stu-id="bfd15-260">During development and testing, when attempting to read contents from an encrypted device offline (e.g. SD card for MinnowBoardMax or DragonBoard's eMMC through USB mass storage mode), 'diskpart' may be used to assign a drive letter to MainOS and Data volume (let's assume v: for MainOS and w: for Data).</span></span>
<span data-ttu-id="bfd15-261">卷会显示为已锁定，并且需要手动解锁。</span><span class="sxs-lookup"><span data-stu-id="bfd15-261">The volumes will appear locked and need to be manually unlocked.</span></span> <span data-ttu-id="bfd15-262">这可以在安装了 OEM DRA.pfx 证书的任何计算机上 (包含在[DeviceLockDown 示例](https://github.com/ms-iot/security/tree/master/TurnkeySecurity))。</span><span class="sxs-lookup"><span data-stu-id="bfd15-262">This can be done on any machine that has the OEM-DRA.pfx certificate installed (included in the [DeviceLockDown sample](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)).</span></span> <span data-ttu-id="bfd15-263">安装 PFX，然后在管理 CMD 提示符中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="bfd15-263">Install the PFX and then run the following commands from an administrative CMD prompt:</span></span>

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

<span data-ttu-id="bfd15-264">如果要经常离线访问内容，可以使用以下命令在初始解锁后设置卷的 BitLocker 自动解锁：</span><span class="sxs-lookup"><span data-stu-id="bfd15-264">If the contents need to be frequently accessed offline, BitLocker autounlock can be set up for the volumes after the initial unlock using the following commands:</span></span>

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a><span data-ttu-id="bfd15-265">禁用 BitLocker</span><span class="sxs-lookup"><span data-stu-id="bfd15-265">Disabling BitLocker</span></span>

<span data-ttu-id="bfd15-266">一旦要临时禁用 BitLocker，请通过 IoT 设备初始化远程 PowerShell 会话，并运行以下命令：`sectask.exe -disable`。</span><span class="sxs-lookup"><span data-stu-id="bfd15-266">Should there arise a need to temporarily disable BitLocker, initate a remote PowerShell session with your IoT device and run the following command: `sectask.exe -disable`.</span></span>  

> [!NOTE]
> <span data-ttu-id="bfd15-267">除非计划的加密任务处于禁用状态，将在以后的设备启动重新启用设备加密。</span><span class="sxs-lookup"><span data-stu-id="bfd15-267">Device encryption will be re-enabled on subsequent device boot unless the scheduled encryption task is disabled.</span></span>


