---
title: 在 Windows 10 IoT Core 上启用安全启动、BitLocker 和 Device Guard
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何在 Windows 10 IoT Core 上启用安全启动、BitLocker 和 Device Guard
keywords: windows iot，安全启动，BitLocker，device guard，安全性，全包式安全
ms.openlocfilehash: 716d3f62c29af34fe9cce87e60dbb0b5a9287850
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91657343"
---
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a><span data-ttu-id="d47ee-104">在 Windows 10 IoT Core 上启用安全启动、BitLocker 和 Device Guard</span><span class="sxs-lookup"><span data-stu-id="d47ee-104">Enabling Secure Boot, BitLocker, and Device Guard on Windows 10 IoT Core</span></span>

<span data-ttu-id="d47ee-105">Windows 10 IoT Core 包含安全功能产品/服务，如 UEFI 安全启动、BitLocker 设备加密和设备防护。</span><span class="sxs-lookup"><span data-stu-id="d47ee-105">Windows 10 IoT Core includes security feature offerings such as UEFI Secure Boot, BitLocker Device Encryption and Device Guard.</span></span>  <span data-ttu-id="d47ee-106">这将帮助设备构建者创建完全锁定的 Windows IoT 设备，这些设备可灵活应对多种不同类型的攻击。</span><span class="sxs-lookup"><span data-stu-id="d47ee-106">These will assist device builders in creating fully locked down Windows IoT devices that are resilient to many different types of attacks.</span></span>  <span data-ttu-id="d47ee-107">这些功能结合在一起，可确保平台以定义的方式启动，同时锁定未知的二进制文件并通过使用设备加密来保护用户数据。</span><span class="sxs-lookup"><span data-stu-id="d47ee-107">Together, these features provide the optimal protection that ensures that a platform will launch in a defined way, while locking out unknown binaries and protecting user data through the use of device encryption.</span></span>

## <a name="boot-order"></a><span data-ttu-id="d47ee-108">启动顺序</span><span class="sxs-lookup"><span data-stu-id="d47ee-108">Boot Order</span></span>

<span data-ttu-id="d47ee-109">需要先了解 Windows 10 IoT Core 设备上的启动顺序，然后才能深入了解为 IoT 设备提供安全平台的单个组件。</span><span class="sxs-lookup"><span data-stu-id="d47ee-109">An understanding of the boot order on a Windows 10 IoT Core device is needed before we can delve into the individual components that provide a secure platform for the IoT device.</span></span>

<span data-ttu-id="d47ee-110">有三个主要方面发生在 IoT 设备打开时，一直到操作系统内核加载和执行安装的应用程序。</span><span class="sxs-lookup"><span data-stu-id="d47ee-110">There are three main areas that occur from when an IoT device is powered on, all the way through to the OS kernel loading and execution of installed application.</span></span>

* <span data-ttu-id="d47ee-111">平台安全启动</span><span class="sxs-lookup"><span data-stu-id="d47ee-111">Platform Secure Boot</span></span>
* <span data-ttu-id="d47ee-112">统一可扩展固件接口 (UEFI) 安全启动</span><span class="sxs-lookup"><span data-stu-id="d47ee-112">Unified Extensible Firmware Interface (UEFI) Secure Boot</span></span>
* <span data-ttu-id="d47ee-113">Windows 代码完整性</span><span class="sxs-lookup"><span data-stu-id="d47ee-113">Windows Code Integrity</span></span>

![启动顺序](../media/SecureBootAndBitLocker/BootOrder.jpg)

<span data-ttu-id="d47ee-115">有关 Windows 10 启动过程的其他信息，请参阅 [此处](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process)。</span><span class="sxs-lookup"><span data-stu-id="d47ee-115">Additional information on the Windows 10 boot process can be found [here](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process).</span></span>

## <a name="locking-down-iot-devices"></a><span data-ttu-id="d47ee-116">锁定 IoT 设备</span><span class="sxs-lookup"><span data-stu-id="d47ee-116">Locking-down IoT Devices</span></span>

<span data-ttu-id="d47ee-117">为了锁定 Windows IoT 设备，必须注意以下事项。</span><span class="sxs-lookup"><span data-stu-id="d47ee-117">In order to lockdown a Windows IoT device, the following considerations must be made.</span></span>

### <a name="platform-secure-boot"></a><span data-ttu-id="d47ee-118">平台安全启动</span><span class="sxs-lookup"><span data-stu-id="d47ee-118">Platform Secure Boot</span></span>

<span data-ttu-id="d47ee-119">第一次打开设备时，整个启动过程中的第一步是加载并运行固件启动加载程序，它们会初始化设备上的硬件并提供紧急闪烁功能。</span><span class="sxs-lookup"><span data-stu-id="d47ee-119">When the device is first powered on, the first step in the overall boot process is to load and run firmware boot loaders, which initialize the hardware on the devies and provide emergency flashing functionality.</span></span> <span data-ttu-id="d47ee-120">然后，将加载 UEFI 环境并移交控制权。</span><span class="sxs-lookup"><span data-stu-id="d47ee-120">The UEFI environment is then loaded and control is handed over.</span></span>

<span data-ttu-id="d47ee-121">这些固件启动加载程序是 SoC 特定的，因此您需要与相应的设备制造商合作，以便在设备上创建这些启动加载程序。</span><span class="sxs-lookup"><span data-stu-id="d47ee-121">These firmware boot loaders are SoC-specific, so you will need to work with the appropriate device manufacturer to have these boot loaders created on the device.</span></span>

### <a name="uefi-secure-boot"></a><span data-ttu-id="d47ee-122">UEFI 安全启动</span><span class="sxs-lookup"><span data-stu-id="d47ee-122">UEFI Secure Boot</span></span>

<span data-ttu-id="d47ee-123">UEFI 安全启动是第一个策略强制点，位于 UEFI。</span><span class="sxs-lookup"><span data-stu-id="d47ee-123">UEFI Secure Boot is the first policy enforcement point, and is located in UEFI.</span></span>  <span data-ttu-id="d47ee-124">它将系统限制为仅允许执行由指定的颁发机构（如固件驱动程序、选项 Rom、UEFI 驱动程序或应用程序）和 UEFI 启动加载程序所签名的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="d47ee-124">It restricts the system to only allow execution of binaries signed by a specified authority, such as firmware drivers, option ROMs, UEFI drivers or applications, and UEFI boot loaders.</span></span> <span data-ttu-id="d47ee-125">此功能可防止在平台上执行未知的代码，潜在地削弱这种代码的安全风险。</span><span class="sxs-lookup"><span data-stu-id="d47ee-125">This feature prevents unknown code from being executed on the platform and potentially weakening the security posture of it.</span></span> <span data-ttu-id="d47ee-126">安全启动降低了对设备进行预启动恶意软件攻击的风险，例如 rootkit。</span><span class="sxs-lookup"><span data-stu-id="d47ee-126">Secure Boot reduces the risk of pre-boot malware attacks to the device, such as rootkits.</span></span>

<span data-ttu-id="d47ee-127">作为 OEM，需要在生产时将 UEFI 安全启动数据库存储在 IoT 设备上。</span><span class="sxs-lookup"><span data-stu-id="d47ee-127">As the OEM, you need to store the UEFI Secure Boot databases on the IoT device at manufacture time.</span></span> <span data-ttu-id="d47ee-128">这些数据库包括签名数据库 (db) 、已吊销的签名数据库 (.dbx) 和密钥注册密钥数据库 (KEK) 。</span><span class="sxs-lookup"><span data-stu-id="d47ee-128">These databases include the Signature database (db), Revoked Signature database (dbx), and the Key Enrollment Key database (KEK).</span></span> <span data-ttu-id="d47ee-129">这些数据库存储在设备 (NV RAM) 的固件非易失性 RAM 中。</span><span class="sxs-lookup"><span data-stu-id="d47ee-129">These databases are stored on the firmware nonvolatile RAM (NV-RAM) of the device.</span></span>

* <span data-ttu-id="d47ee-130">\*\* (db) 的签名数据库：\*\* 这列出了允许在设备上加载的操作系统加载程序、UEFI 应用程序和 UEFI 驱动程序的签名者或图像哈希</span><span class="sxs-lookup"><span data-stu-id="d47ee-130">**Signature Database (db):** This lists the signers or image hashes of operating system loaders, UEFI applications, and UEFI drivers that are allowed to be loaded on the device</span></span>

* <span data-ttu-id="d47ee-131">已**吊销 (.dbx) 的签名数据库：** 这列出了不再受信任且*不*允许在设备上加载的操作系统加载程序、uefi 应用程序和 uefi 驱动程序的签名者或图像哈希</span><span class="sxs-lookup"><span data-stu-id="d47ee-131">**Revoked Signature Database (dbx):** This lists the signers or image hashes of operating system loaders, UEFI applications and UEFI drivers that are no longer trusted, and are *NOT* allowed to be loaded on the device</span></span>

* <span data-ttu-id="d47ee-132">**密钥注册密钥数据库 (KEK) ：** 包含一个签名密钥列表，可用于更新签名和吊销的签名数据库。</span><span class="sxs-lookup"><span data-stu-id="d47ee-132">**Key Enrollment Key database (KEK):** Contains a list of signing keys that can be used to update the signature and revoked signature databases.</span></span>

<span data-ttu-id="d47ee-133">创建这些数据库并将其添加到设备后，OEM 会锁定固件以进行编辑，并 (PK) 生成平台签名密钥。</span><span class="sxs-lookup"><span data-stu-id="d47ee-133">Once these databases are created and added to the device, the OEM locks the firmware from editing, and generates a platform signing key (PK).</span></span> <span data-ttu-id="d47ee-134">此密钥可用于对 KEK 的更新进行签名或禁用 UEFI 安全启动。</span><span class="sxs-lookup"><span data-stu-id="d47ee-134">This key can be used to sign updates to the KEK or to disable UEFI Secure Boot.</span></span>

<span data-ttu-id="d47ee-135">下面是 UEFI 安全启动所执行的步骤：</span><span class="sxs-lookup"><span data-stu-id="d47ee-135">Here are the steps taken by UEFI Secure Boot:</span></span>

1. <span data-ttu-id="d47ee-136">打开设备后，会根据平台签名密钥检查每个签名数据库 (PK) 。</span><span class="sxs-lookup"><span data-stu-id="d47ee-136">After the device is powered on, the signature databases are each checked against the platform signing key (PK).</span></span>
2. <span data-ttu-id="d47ee-137">如果固件不受信任，则 UEFI 固件启动 OEM 特定的恢复以还原受信任的固件。</span><span class="sxs-lookup"><span data-stu-id="d47ee-137">If the firmware isn't trusted, UEFI firmware initiates OEM-specific recovery to restore trusted firmware.</span></span>
3. <span data-ttu-id="d47ee-138">如果无法加载 Windows 启动管理器，固件将尝试启动 Windows 启动管理器的备份副本。</span><span class="sxs-lookup"><span data-stu-id="d47ee-138">If Windows Boot Manager cannot be loaded, the firmware will attempt to boot a backup copy of Windows Boot Manager.</span></span> <span data-ttu-id="d47ee-139">如果此操作失败，则 UEFI 固件会启动 OEM 特定的修正。</span><span class="sxs-lookup"><span data-stu-id="d47ee-139">If this also fails, the UEFI firmware initiates OEM-specific remediation.</span></span>
4. <span data-ttu-id="d47ee-140">Windows 启动管理器运行并验证 Windows 内核的数字签名。</span><span class="sxs-lookup"><span data-stu-id="d47ee-140">Windows Boot Manager runs and verifies the digital signature of the Windows Kernel.</span></span> <span data-ttu-id="d47ee-141">如果受信任，Windows 启动管理器会将控制权传递给 Windows 内核。</span><span class="sxs-lookup"><span data-stu-id="d47ee-141">If trusted, Windows Boot Manager passes control to the Windows Kernel.</span></span>

<span data-ttu-id="d47ee-142">[此处](https://technet.microsoft.com/library/dn747883.aspx)提供有关安全引导的其他详细信息，以及密钥创建和管理指南。</span><span class="sxs-lookup"><span data-stu-id="d47ee-142">Additional details on Secure Boot, along with key creation and management guidance, is available [here](https://technet.microsoft.com/library/dn747883.aspx).</span></span>

### <a name="windows-code-integrity"></a><span data-ttu-id="d47ee-143">Windows 代码完整性</span><span class="sxs-lookup"><span data-stu-id="d47ee-143">Windows Code Integrity</span></span>

<span data-ttu-id="d47ee-144">Windows 代码完整性 (WCI) 通过在每次将驱动程序或应用程序加载到内存时验证其完整性来提高操作系统的安全性。</span><span class="sxs-lookup"><span data-stu-id="d47ee-144">Windows Code Integrity (WCI) improves the security of the operating system by validating the integrity of a driver or application each time it is loaded into memory.</span></span> <span data-ttu-id="d47ee-145">CI 包含两个主要组件：内核模式代码完整性 (KMCI) 和用户模式代码完整性 (UMCI) 。</span><span class="sxs-lookup"><span data-stu-id="d47ee-145">CI contains two main components - Kernel Mode Code Integrity (KMCI) and User Mode Code Integrity (UMCI).</span></span>

<span data-ttu-id="d47ee-146">可配置代码完整性 (CCI) 是 Windows 10 中的一项功能，它允许设备构建者锁定设备，并只允许其运行和执行签名和信任的代码。</span><span class="sxs-lookup"><span data-stu-id="d47ee-146">Configurable Code Integrity (CCI) is a feature in Windows 10 that allows device builders to lockdown a device and only allow it to run and execute code that is signed and trusted.</span></span>  <span data-ttu-id="d47ee-147">为此，设备构建者可以在 "黄金" 设备上创建代码完整性策略 (最终版本的硬件和软件) ，然后在工厂地面上的所有设备上保护并应用此策略。</span><span class="sxs-lookup"><span data-stu-id="d47ee-147">To do so, device builders can create a code integrity policy on a 'golden' device (final release version of hardware and software) and then secure and apply this policy on all devices on the factory floor.</span></span>

<span data-ttu-id="d47ee-148">若要了解有关部署代码完整性策略、审核和强制的详细信息，请查看 [此处](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps)的最新 technet 文档。</span><span class="sxs-lookup"><span data-stu-id="d47ee-148">To learn more about deploying code integrity policies, auditing and enforcement, check out the latest technet documentation [here](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps).</span></span>

<span data-ttu-id="d47ee-149">下面是 Windows 代码完整性执行的步骤：</span><span class="sxs-lookup"><span data-stu-id="d47ee-149">Here are the steps taken by Windows Code Integrity:</span></span>

1. <span data-ttu-id="d47ee-150">在加载之前，Windows 内核将对照签名数据库验证所有其他组件。</span><span class="sxs-lookup"><span data-stu-id="d47ee-150">Windows Kernel will verify all other components against the signature database before loading.</span></span> <span data-ttu-id="d47ee-151">这包括驱动程序、启动文件和 ELAM (提前启动反恶意软件) 。</span><span class="sxs-lookup"><span data-stu-id="d47ee-151">This includes drivers, startup files, and ELAM (Early Launch Anti-Malware).</span></span>
2. <span data-ttu-id="d47ee-152">Windows 内核将在启动过程中加载受信任的组件，并禁止加载不受信任的组件。</span><span class="sxs-lookup"><span data-stu-id="d47ee-152">Windows Kernel will load the trusted components in the startup process, and prohibit loading of the untrusted components.</span></span>
3. <span data-ttu-id="d47ee-153">Windows 10 IoT Core 操作系统加载和任何已安装的应用程序。</span><span class="sxs-lookup"><span data-stu-id="d47ee-153">Windows 10 IoT Core operating system loads, along with any installed applications.</span></span>

### <a name="bitlocker-device-encryption"></a><span data-ttu-id="d47ee-154">BitLocker 设备加密</span><span class="sxs-lookup"><span data-stu-id="d47ee-154">BitLocker Device Encryption</span></span>

<span data-ttu-id="d47ee-155">Windows 10 IoT Core 还实现了 BitLocker 设备加密的轻型版，保护 IoT 设备免受离线攻击。</span><span class="sxs-lookup"><span data-stu-id="d47ee-155">Windows 10 IoT Core also implements a lightweight version of BitLocker Device Encryption, protecting IoT devices against offline attacks.</span></span> <span data-ttu-id="d47ee-156">此功能与平台上的 TPM 的存在很强，其中包括在 UEFI 中执行必要度量的必需的操作系统协议。</span><span class="sxs-lookup"><span data-stu-id="d47ee-156">This capability has a strong dependency on the presence of a TPM on the platform, including the necessary pre-OS protocol in UEFI that conducts the necessary measurements.</span></span> <span data-ttu-id="d47ee-157">这些预操作系统度量值可确保 OS 更高版本具有操作系统启动方式的明确记录;但是，它不强制执行任何执行限制。</span><span class="sxs-lookup"><span data-stu-id="d47ee-157">These pre-OS measurements ensure that the OS later has a definitive record of how the OS was launched; however, it does not enforce any execution restrictions.</span></span>

> [!TIP]
> <span data-ttu-id="d47ee-158">Windows 10 IoT Core 上的 BitLocker 功能允许对基于 NTFS 的 OS 卷进行自动加密，同时将所有可用的 NTFS 数据卷绑定到该卷。</span><span class="sxs-lookup"><span data-stu-id="d47ee-158">BitLocker functionality on Windows 10 IoT Core allows for automatic encryption of NTFS-based OS volume while binding all available NTFS data volumes to it.</span></span> <span data-ttu-id="d47ee-159">为此，必须确保 EFIESP 卷 GUID 设置为 _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_。</span><span class="sxs-lookup"><span data-stu-id="d47ee-159">For this, it’s necessary to ensure that the EFIESP volume GUID is set to _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_.</span></span>

### <a name="device-guard-on-windows-iot-core"></a><span data-ttu-id="d47ee-160">Windows IoT Core 上的 Device Guard</span><span class="sxs-lookup"><span data-stu-id="d47ee-160">Device Guard on Windows IoT Core</span></span>

<span data-ttu-id="d47ee-161">大多数 IoT 设备被构建为固定功能的设备。</span><span class="sxs-lookup"><span data-stu-id="d47ee-161">Most IoT devices are built as fixed-function devices.</span></span> <span data-ttu-id="d47ee-162">这意味着设备制造商确切知道哪些固件、操作系统、驱动程序和应用程序应在给定设备上运行。</span><span class="sxs-lookup"><span data-stu-id="d47ee-162">This implies that device builders know exactly which firmware, operating system, drivers, and applications should be running on a given device.</span></span> <span data-ttu-id="d47ee-163">反过来，此信息可用于通过只允许执行已知的和受信任的代码来完全锁定 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="d47ee-163">In turn, this information can be used to fully lockdown an IoT device by only allowing execution of known and trusted code.</span></span> <span data-ttu-id="d47ee-164">Windows 10 IoT Core 上的 Device Guard 可以通过确保无法在锁定的设备上运行未知或不受信任的可执行代码来帮助保护 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="d47ee-164">Device Guard on Windows 10 IoT Core can help protect IoT devices by ensuring that unknown or untrusted executable code cannot be run on locked-down devices.</span></span>


## <a name="turnkey-security-on-iot-core"></a><span data-ttu-id="d47ee-165">IoT 核心安全</span><span class="sxs-lookup"><span data-stu-id="d47ee-165">Turnkey Security on IoT Core</span></span>

<span data-ttu-id="d47ee-166">为了便于在 IoT Core 设备上轻松启用密钥安全功能，Microsoft 提供了一个允许设备构建商构建完全锁定的 IoT 设备的 [全包式安全包]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 。</span><span class="sxs-lookup"><span data-stu-id="d47ee-166">To facilitate easy enablement of key security features on IoT Core devices, Microsoft is providing a [Turnkey Security Package]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity) that allows device builders to build fully locked down IoT devices.</span></span> <span data-ttu-id="d47ee-167">此包将帮助你：</span><span class="sxs-lookup"><span data-stu-id="d47ee-167">This package will help with:</span></span>

* <span data-ttu-id="d47ee-168">设置安全启动密钥并在支持的 IoT 平台上启用该功能</span><span class="sxs-lookup"><span data-stu-id="d47ee-168">Provisioning Secure Boot keys and enabling the feature on supported IoT platforms</span></span>
* <span data-ttu-id="d47ee-169">使用 BitLocker 设置和配置设备加密</span><span class="sxs-lookup"><span data-stu-id="d47ee-169">Setup and configuration of device encryption using BitLocker</span></span>
* <span data-ttu-id="d47ee-170">启动设备锁定以仅允许执行已签名的应用程序和驱动程序</span><span class="sxs-lookup"><span data-stu-id="d47ee-170">Initiating device lockdown to only allow execution of signed applications and drivers</span></span>

<span data-ttu-id="d47ee-171">以下步骤将引导完成使用[交钥匙安全包]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity)创建锁定映像的过程</span><span class="sxs-lookup"><span data-stu-id="d47ee-171">The following steps will lead through the process to create a lockdown image using the [Turnkey Security Package]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity)</span></span>

![创建锁定映像](../media/SecurityFlowAndCertificates/ImageLockDown.png)

### <a name="prerequisites"></a><span data-ttu-id="d47ee-173">必备条件</span><span class="sxs-lookup"><span data-stu-id="d47ee-173">Prerequisites</span></span>

* <span data-ttu-id="d47ee-174">提供的脚本 **不** 支持运行 Windows 10 企业版 (其他 windows 版本的电脑) </span><span class="sxs-lookup"><span data-stu-id="d47ee-174">A PC running Windows 10 Enterprise (other Windows versions are **not** supported by the provided scripts)</span></span>
* <span data-ttu-id="d47ee-175">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) -证书生成必需</span><span class="sxs-lookup"><span data-stu-id="d47ee-175">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) - Required for Certificate Generation</span></span>
* <span data-ttu-id="d47ee-176">[Windows 10 ADK](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit) -CAB 生成必需的</span><span class="sxs-lookup"><span data-stu-id="d47ee-176">[Windows 10 ADK](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit) - Required for CAB generation</span></span>
* <span data-ttu-id="d47ee-177">引用平台-需要随附固件、OS、驱动程序和应用程序的版本硬件才能进行最终锁定</span><span class="sxs-lookup"><span data-stu-id="d47ee-177">Reference platform - release hardware with shipping firmware, OS, drivers, and applications will be required for final lockdown</span></span>

### <a name="development-iot-devices"></a><span data-ttu-id="d47ee-178">开发 IoT 设备</span><span class="sxs-lookup"><span data-stu-id="d47ee-178">Development IoT Devices</span></span>

<span data-ttu-id="d47ee-179">Windows 10 IoT Core 适用于数百个设备中使用的各种 silicons。</span><span class="sxs-lookup"><span data-stu-id="d47ee-179">Windows 10 IoT Core works with various silicons that are utilized in hundreds of devices.</span></span> <span data-ttu-id="d47ee-180">在 [建议的 IoT 开发设备](../learn-about-hardware/SoCsAndCustomBoards.md)中，以下提供了现成的固件 TPM 功能，以及安全启动、标准启动、BitLocker 和设备防护功能：</span><span class="sxs-lookup"><span data-stu-id="d47ee-180">Of the [suggested IoT development devices](../learn-about-hardware/SoCsAndCustomBoards.md), the following provide firmware TPM functionality out of the box, along with Secure Boot, Measured Boot, BitLocker, and Device Guard capabilities:</span></span>

* <span data-ttu-id="d47ee-181">Qualcomm DragonBoard 410c</span><span class="sxs-lookup"><span data-stu-id="d47ee-181">Qualcomm DragonBoard 410c</span></span>

    <span data-ttu-id="d47ee-182">若要启用安全启动，可能需要预配 RPMB。</span><span class="sxs-lookup"><span data-stu-id="d47ee-182">In order to enable Secure Boot, it may be necessary to provision RPMB.</span></span> <span data-ttu-id="d47ee-183">按照 [此处](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c)的说明将 EMMC 与 Windows 10 IoT Core (闪存后，请在启动时在设备上同时按 [Power] + [Vol +] + [vol] + [vol]，并从 BDS 菜单中选择 "预配 RPMB"。</span><span class="sxs-lookup"><span data-stu-id="d47ee-183">Once the eMMC has been flashed with Windows 10 IoT Core (as per instructions [here](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), press [Power] + [Vol+] + [Vol-] simultaneously on the device when powering up and select "Provision RPMB" from the BDS menu.</span></span> <span data-ttu-id="d47ee-184">*请注意，这是一个不可逆的步骤。*</span><span class="sxs-lookup"><span data-stu-id="d47ee-184">*Please note that this is an irreversible step.*</span></span>

* <span data-ttu-id="d47ee-185">Intel MinnowBoardMax</span><span class="sxs-lookup"><span data-stu-id="d47ee-185">Intel MinnowBoardMax</span></span>

    <span data-ttu-id="d47ee-186">对于 Intel 的 MinnowBoard Max，固件版本必须为0.82 或更高版本 (获取 [最新固件](https://firmware.intel.com/projects/minnowboard-max)) 。</span><span class="sxs-lookup"><span data-stu-id="d47ee-186">For Intel's MinnowBoard Max, firmware version must be 0.82 or higher (get the [latest firmware](https://firmware.intel.com/projects/minnowboard-max)).</span></span> <span data-ttu-id="d47ee-187">若要启用 TPM 功能，请使用键盘 & 显示连接，然后按 F2 进入 UEFI 设置。</span><span class="sxs-lookup"><span data-stu-id="d47ee-187">To enable TPM capabilities, power up board with a keyboard & display attached and press F2 to enter UEFI setup.</span></span> <span data-ttu-id="d47ee-188">请参阅_设备管理器-> 系统设置-> 安全配置-> PTT_并将其设置为 " _ &lt; 启用 &gt; _"。</span><span class="sxs-lookup"><span data-stu-id="d47ee-188">Go to _Device Manager -> System Setup -> Security Configuration -> PTT_ and set it to _&lt;Enable&gt;_.</span></span> <span data-ttu-id="d47ee-189">按 F10 保存更改并继续重新启动平台。</span><span class="sxs-lookup"><span data-stu-id="d47ee-189">Press F10 to save changes and proceed with a reboot of the platform.</span></span>

> [!NOTE]
> <span data-ttu-id="d47ee-190">Raspberry Pi 2 或3不支持 TPM，因此我们无法配置锁定方案。</span><span class="sxs-lookup"><span data-stu-id="d47ee-190">Raspberry Pi 2 nor 3 do not support TPM and so we cannot configure Lockdown scenarios.</span></span>

### <a name="generate-lockdown-packages"></a><span data-ttu-id="d47ee-191">生成锁定包</span><span class="sxs-lookup"><span data-stu-id="d47ee-191">Generate Lockdown Packages</span></span>

1. <span data-ttu-id="d47ee-192">下载 [DeviceLockDown 脚本](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 包，其中包含配置和锁定设备所需的所有其他工具和脚本</span><span class="sxs-lookup"><span data-stu-id="d47ee-192">Download the [DeviceLockDown Script](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) package, which contains all of the additional tools and scripts required for configuring and locking down devices</span></span>
2. <span data-ttu-id="d47ee-193">在 Windows 10 电脑上启动管理 PowerShell (PS) 控制台，并导航到下载的脚本的位置。</span><span class="sxs-lookup"><span data-stu-id="d47ee-193">Start an Administrative PowerShell (PS) console on your Windows 10 PC and navigate to the location of the downloaded script.</span></span>
3. <span data-ttu-id="d47ee-194">通过网络共享将你的参考硬件平台 (运行未锁定的映像) 到你的电脑上，使用</span><span class="sxs-lookup"><span data-stu-id="d47ee-194">Mount your reference hardware platform (running the unlocked image) to your PC via network share using</span></span>

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. <span data-ttu-id="d47ee-195">使用生成设备的密钥</span><span class="sxs-lookup"><span data-stu-id="d47ee-195">Generate keys for your device using</span></span>

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * <span data-ttu-id="d47ee-196">在指定的输出文件夹中生成具有相应后缀的密钥和证书。</span><span class="sxs-lookup"><span data-stu-id="d47ee-196">The keys and certificates are generated in the specified output folder with appropriate suffix.</span></span>
    * <span data-ttu-id="d47ee-197">**保护生成的密钥** ，因为设备将信任仅在锁定后通过这些密钥进行签名的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="d47ee-197">**Secure your generated keys** as the device will trust binaries signed with these keys only after lockdown.</span></span>
    * <span data-ttu-id="d47ee-198">你可以跳过此步骤，并使用预先生成的密钥仅用于测试</span><span class="sxs-lookup"><span data-stu-id="d47ee-198">You may skip this step and use the pre-generated keys for testing only</span></span>

5. <span data-ttu-id="d47ee-199">配置 _settings.xml_</span><span class="sxs-lookup"><span data-stu-id="d47ee-199">Configure _settings.xml_</span></span>

    * <span data-ttu-id="d47ee-200">常规部分：指定包目录</span><span class="sxs-lookup"><span data-stu-id="d47ee-200">General section : Specify the package directories</span></span>
    * <span data-ttu-id="d47ee-201">工具部分：设置工具的路径</span><span class="sxs-lookup"><span data-stu-id="d47ee-201">Tools section : Set the path for the tools</span></span>
        * <span data-ttu-id="d47ee-202">Windows10KitsRoot `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`</span><span class="sxs-lookup"><span data-stu-id="d47ee-202">Windows10KitsRoot `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`</span></span>
        * <span data-ttu-id="d47ee-203">WindowsSDKVersion `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`</span><span class="sxs-lookup"><span data-stu-id="d47ee-203">WindowsSDKVersion `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`</span></span>
            * <span data-ttu-id="d47ee-204">计算机上安装的 SDK 版本低于 `C:\Program Files (x86)\Windows Kits\10\`</span><span class="sxs-lookup"><span data-stu-id="d47ee-204">SDK version installed on your machine is under `C:\Program Files (x86)\Windows Kits\10\`</span></span>
    * <span data-ttu-id="d47ee-205">SecureBoot 节：指定用于安全启动 (PK 和 SB 键的密钥) </span><span class="sxs-lookup"><span data-stu-id="d47ee-205">SecureBoot section : Specify which keys to use for secure boot (PK and SB keys)</span></span>
    * <span data-ttu-id="d47ee-206">BitLocker 部分：为 BitLocker 数据恢复 (DRA 密钥指定证书) </span><span class="sxs-lookup"><span data-stu-id="d47ee-206">BitLocker section : Specify a certificate for BitLocker data recovery (DRA key)</span></span>
    * <span data-ttu-id="d47ee-207">SIPolicy 节：指定应信任的证书</span><span class="sxs-lookup"><span data-stu-id="d47ee-207">SIPolicy section : Specify certs that should be trusted</span></span>
        * <span data-ttu-id="d47ee-208">ScanPath：用于扫描二进制文件的设备的路径。 `\\a.b.c.d\C$`</span><span class="sxs-lookup"><span data-stu-id="d47ee-208">ScanPath : Path of the device for scanning binaries , `\\a.b.c.d\C$`</span></span>
        * <span data-ttu-id="d47ee-209">更新： SIPolicy (PAUTH 键的签名者) </span><span class="sxs-lookup"><span data-stu-id="d47ee-209">Update   : Signer of the SIPolicy (PAUTH keys)</span></span>
        * <span data-ttu-id="d47ee-210">用户模式证书 (UMCI 密钥) </span><span class="sxs-lookup"><span data-stu-id="d47ee-210">User     : User mode certificates (UMCI keys)</span></span>
        * <span data-ttu-id="d47ee-211">内核：内核模式证书 (KMCI 密钥) </span><span class="sxs-lookup"><span data-stu-id="d47ee-211">Kernel   : Kernel mode certificates (KMCI keys)</span></span>
    * <span data-ttu-id="d47ee-212">打包：指定包生成的设置</span><span class="sxs-lookup"><span data-stu-id="d47ee-212">Packaging : Specify the settings for the package generation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d47ee-213">为了在初始开发周期中协助测试，Microsoft 在适当的位置提供了预生成的密钥和证书。</span><span class="sxs-lookup"><span data-stu-id="d47ee-213">In order to assist with testing during the initial development cycle, Microsoft has provided pre-generated keys and certificates where appropriate.</span></span>  <span data-ttu-id="d47ee-214">这意味着 Microsoft 测试、开发和预发布二进制文件被视为受信任。</span><span class="sxs-lookup"><span data-stu-id="d47ee-214">This implies that Microsoft Test, Development and Pre-Release binaries are considered trusted.</span></span>  <span data-ttu-id="d47ee-215">在最终产品创建和映像生成过程中，请确保删除这些证书并使用你自己的密钥，以确保完全锁定的设备。</span><span class="sxs-lookup"><span data-stu-id="d47ee-215">During final product creation and image generation, be sure to remove these certifcates and use your own keys to ensure a fully locked down device.</span></span>

6. <span data-ttu-id="d47ee-216">执行以下命令以生成所需的包：</span><span class="sxs-lookup"><span data-stu-id="d47ee-216">Execute the following commands to generate required packages:</span></span>
```
    powershell

    Import-Module .\IoTTurnkeySecurity.psm1

    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml

    (or)

    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
```

### <a name="test-lockdown-packages"></a><span data-ttu-id="d47ee-217">测试锁定包</span><span class="sxs-lookup"><span data-stu-id="d47ee-217">Test Lockdown packages</span></span>
<span data-ttu-id="d47ee-218">你可以通过以下步骤在解锁的设备上手动安装生成的包，以对其进行测试</span><span class="sxs-lookup"><span data-stu-id="d47ee-218">You can test the generated packages by manually installing them on a unlocked device by the following steps</span></span>

1. <span data-ttu-id="d47ee-219">使用解锁的映像刷新设备， (用于在先前步骤中扫描的映像) 。</span><span class="sxs-lookup"><span data-stu-id="d47ee-219">Flash the device with the unlocked image (image used for scanning in earlier step).</span></span>
2. <span data-ttu-id="d47ee-220">[使用 SSH](../connect-your-device/SSH.md)或[PowerShell](../connect-your-device/PowerShell.md)连接到设备 () </span><span class="sxs-lookup"><span data-stu-id="d47ee-220">Connect to the device ([using SSH](../connect-your-device/SSH.md) or using [PowerShell](../connect-your-device/PowerShell.md))</span></span>
3. <span data-ttu-id="d47ee-221">将以下 .cab 文件复制到目录下的设备，例如 `c:\OemInstall`</span><span class="sxs-lookup"><span data-stu-id="d47ee-221">Copy the following .cab files to the device under a directory e.g. `c:\OemInstall`</span></span>
    * <span data-ttu-id="d47ee-222">OEM.Custom.Cmd.cab</span><span class="sxs-lookup"><span data-stu-id="d47ee-222">OEM.Custom.Cmd.cab</span></span>
    * <span data-ttu-id="d47ee-223">OEM.Security.BitLocker.cab</span><span class="sxs-lookup"><span data-stu-id="d47ee-223">OEM.Security.BitLocker.cab</span></span>
    * <span data-ttu-id="d47ee-224">OEM.Security.SecureBoot.cab</span><span class="sxs-lookup"><span data-stu-id="d47ee-224">OEM.Security.SecureBoot.cab</span></span>
    * <span data-ttu-id="d47ee-225">OEM.Security.DeviceGuard.cab</span><span class="sxs-lookup"><span data-stu-id="d47ee-225">OEM.Security.DeviceGuard.cab</span></span>
4. <span data-ttu-id="d47ee-226">发出以下命令启动生成的包的暂存</span><span class="sxs-lookup"><span data-stu-id="d47ee-226">Initiate staging of the generated packages by issuing the following commands</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    <span data-ttu-id="d47ee-227">如果使用的是自定义映像，则必须*跳过*此文件，并 `c:\windows\system32\oemcustomization.cmd` 使用文件中可用的内容手动编辑 `Output\OEMCustomization\OEMCustomization.cmd`</span><span class="sxs-lookup"><span data-stu-id="d47ee-227">If you are using custom image, then you will have to *skip* this file and manually edit the `c:\windows\system32\oemcustomization.cmd` with the contents available in `Output\OEMCustomization\OEMCustomization.cmd` file</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. <span data-ttu-id="d47ee-228">设备将重新启动以更新 OS (显示齿轮) 来安装包，并再次重新启动到主操作系统。</span><span class="sxs-lookup"><span data-stu-id="d47ee-228">The device will reboot into update OS (showing gears) to install the packages and will reboot again to main OS.</span></span>  <span data-ttu-id="d47ee-229">设备重新启动到 MainOS 后，将启用安全启动并应进行 SIPolicy。</span><span class="sxs-lookup"><span data-stu-id="d47ee-229">Once the device reboots back into MainOS, Secure Boot will be enabled and SIPolicy should be engaged.</span></span>
7. <span data-ttu-id="d47ee-230">再次重新启动设备以激活 BitLocker 加密。</span><span class="sxs-lookup"><span data-stu-id="d47ee-230">Reboot the device again to activate the BitLocker encryption.</span></span>
8. <span data-ttu-id="d47ee-231">测试安全功能</span><span class="sxs-lookup"><span data-stu-id="d47ee-231">Test the security features</span></span>
    * <span data-ttu-id="d47ee-232">SecureBoot：尝试 `bcdedit /debug on` ，会收到一条错误消息，指出值受安全启动策略的保护</span><span class="sxs-lookup"><span data-stu-id="d47ee-232">SecureBoot: try `bcdedit /debug on` , you will get an error stating that the value is protected by secure boot policy</span></span>
    * <span data-ttu-id="d47ee-233">BitLocker：运行 `start /wait sectask.exe -waitencryptcomplete:1` ，如果 ERRORLEVEL `-2147023436` () ERROR_TIMEOUT，则加密不完整。</span><span class="sxs-lookup"><span data-stu-id="d47ee-233">BitLocker: Run `start /wait sectask.exe -waitencryptcomplete:1`, if ERRORLEVEL is `-2147023436` (ERROR_TIMEOUT) then encryption is not complete.</span></span> <span data-ttu-id="d47ee-234">从 .cmd 文件运行 sectask.exe 时省略 `start /wait` 。</span><span class="sxs-lookup"><span data-stu-id="d47ee-234">When running sectask.exe from a .cmd file omit the `start /wait`.</span></span>
    * <span data-ttu-id="d47ee-235">DeviceGuard：运行任何未签名的二进制文件或使用不在 SIPolicy 列表中的证书签名的二进制文件，并确认它无法运行。</span><span class="sxs-lookup"><span data-stu-id="d47ee-235">DeviceGuard : Run any unsigned binary or a binary signed with certificate not in the SIPolicy list and confirm that it fails to run.</span></span>

### <a name="generate-lockdown-image"></a><span data-ttu-id="d47ee-236">生成锁定映像</span><span class="sxs-lookup"><span data-stu-id="d47ee-236">Generate Lockdown image</span></span>

<span data-ttu-id="d47ee-237">按照前面定义的设置验证锁定包是否正常工作后，可以按照以下给定步骤将这些包包含到映像中。</span><span class="sxs-lookup"><span data-stu-id="d47ee-237">After validating that the lockdown packages are working as per the settings defined earlier, you can then include these packages into the image by following the below given steps.</span></span> <span data-ttu-id="d47ee-238">阅读 [IoT 制造指南](https://aka.ms/iotcoreguide) 了解自定义映像创建说明。</span><span class="sxs-lookup"><span data-stu-id="d47ee-238">Read the [IoT manufacturing guide](https://aka.ms/iotcoreguide) for custom image creation instructions.</span></span>

1. <span data-ttu-id="d47ee-239">在工作区目录中，从上面生成的输出目录中更新以下文件</span><span class="sxs-lookup"><span data-stu-id="d47ee-239">In the workspace directory, update the following files from the generated output directory above</span></span>
    * <span data-ttu-id="d47ee-240">SecureBoot `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`</span><span class="sxs-lookup"><span data-stu-id="d47ee-240">SecureBoot : `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`</span></span>
      * <span data-ttu-id="d47ee-241">SetVariable_db bin</span><span class="sxs-lookup"><span data-stu-id="d47ee-241">SetVariable_db.bin</span></span>
      * <span data-ttu-id="d47ee-242">SetVariable_kek bin</span><span class="sxs-lookup"><span data-stu-id="d47ee-242">SetVariable_kek.bin</span></span>
      * <span data-ttu-id="d47ee-243">SetVariable_pk bin</span><span class="sxs-lookup"><span data-stu-id="d47ee-243">SetVariable_pk.bin</span></span>
    * <span data-ttu-id="d47ee-244">BitLocker `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`</span><span class="sxs-lookup"><span data-stu-id="d47ee-244">BitLocker : `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`</span></span>
      * <span data-ttu-id="d47ee-245">DETask.xml</span><span class="sxs-lookup"><span data-stu-id="d47ee-245">DETask.xml</span></span>
      * <span data-ttu-id="d47ee-246">Security.Bitlocker.wm.xml</span><span class="sxs-lookup"><span data-stu-id="d47ee-246">Security.Bitlocker.wm.xml</span></span>
      * <span data-ttu-id="d47ee-247">setup.exe</span><span class="sxs-lookup"><span data-stu-id="d47ee-247">setup.bitlocker.cmd</span></span>
    * <span data-ttu-id="d47ee-248">DeviceGuard : `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`</span><span class="sxs-lookup"><span data-stu-id="d47ee-248">DeviceGuard : `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`</span></span>
      * <span data-ttu-id="d47ee-249">SIPolicyOn</span><span class="sxs-lookup"><span data-stu-id="d47ee-249">SIPolicyOn.p7b</span></span>
      * <span data-ttu-id="d47ee-250">SIPolicyOff</span><span class="sxs-lookup"><span data-stu-id="d47ee-250">SIPolicyOff.p7b</span></span>

2. <span data-ttu-id="d47ee-251">在包含锁定包功能 ID 的 ProductName 目录下添加 RetailOEMInput.xml 和 TestOEMInput.xml</span><span class="sxs-lookup"><span data-stu-id="d47ee-251">Add RetailOEMInput.xml and TestOEMInput.xml under the ProductName directory with lockdown package feature ID</span></span>
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. <span data-ttu-id="d47ee-252">重新生成映像</span><span class="sxs-lookup"><span data-stu-id="d47ee-252">Re-generate Image</span></span>
    * <span data-ttu-id="d47ee-253">`buildpkg all` (基于以上策略文件生成新的锁定包) </span><span class="sxs-lookup"><span data-stu-id="d47ee-253">`buildpkg all` (this generates new lockdown packages based on above policy files)</span></span>
    * <span data-ttu-id="d47ee-254">`buildimage ProductName test(or)retail`  (生成新的 ffu) </span><span class="sxs-lookup"><span data-stu-id="d47ee-254">`buildimage ProductName test(or)retail`  (this generates new Flash.ffu)</span></span>
4. <span data-ttu-id="d47ee-255">用这个新的 ffu 闪存设备，并验证安全功能。</span><span class="sxs-lookup"><span data-stu-id="d47ee-255">Flash the device with this new Flash.ffu and validate the security features.</span></span>

<span data-ttu-id="d47ee-256">请参阅 [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) 作为锁定的龙板配置的示例。</span><span class="sxs-lookup"><span data-stu-id="d47ee-256">See [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) as an example of a lockdown dragon board configuration.</span></span>

<span data-ttu-id="d47ee-257">或者，你可以在 IoTCore Shell 本身中生成安全包，请参阅 [添加安全包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) 获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="d47ee-257">Alternatively, you can generate the security packages in the IoTCore Shell itself, see [adding security packages](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) for the details.</span></span>


### <a name="developing-with-codesigning-enforcement-enabled"></a><span data-ttu-id="d47ee-258">已启用代码签名强制开发</span><span class="sxs-lookup"><span data-stu-id="d47ee-258">Developing with CodeSigning Enforcement Enabled</span></span>

<span data-ttu-id="d47ee-259">生成包并激活锁定后，在开发过程中引入到映像中的所有二进制文件都需要进行相应的签名。</span><span class="sxs-lookup"><span data-stu-id="d47ee-259">Once the packages are generated and lockdown is activated, any binaries introduced into the image during development will need to be signed appropriately.</span></span> <span data-ttu-id="d47ee-260">确保用户模式的二进制文件已用密钥  _.\Keys\ \* \* \*-UMCI_进行签名。</span><span class="sxs-lookup"><span data-stu-id="d47ee-260">Ensure that your user-mode binaries are signed with the key  _.\Keys\ \*\*\*-UMCI.pfx_.</span></span> <span data-ttu-id="d47ee-261">对于内核模式签名（如驱动程序），需要指定自己的签名密钥并确保它们也包含在上述 SIPolicy 中。</span><span class="sxs-lookup"><span data-stu-id="d47ee-261">For kernel-mode signing, such as for drivers, you’ll need to specify your own signing keys and make sure that they are also included in the SIPolicy above.</span></span>

### <a name="unlocking-encrypted-drives"></a><span data-ttu-id="d47ee-262">解锁加密驱动器</span><span class="sxs-lookup"><span data-stu-id="d47ee-262">Unlocking Encrypted Drives</span></span>

<span data-ttu-id="d47ee-263">在开发和测试期间，如果尝试从脱机的已加密设备读取内容 (例如，通过 USB 大容量存储) 模式将 SD 卡用于 MinnowBoardMax 或 DragonBoard 的 eMMC，则可以使用 "diskpart" 将驱动器号分配给 MainOS 和数据卷， (假设 v：对于 MainOS 和 w：对于数据) 。</span><span class="sxs-lookup"><span data-stu-id="d47ee-263">During development and testing, when attempting to read contents from an encrypted device offline (e.g. SD card for MinnowBoardMax or DragonBoard's eMMC through USB mass storage mode), 'diskpart' may be used to assign a drive letter to MainOS and Data volume (let's assume v: for MainOS and w: for Data).</span></span>
<span data-ttu-id="d47ee-264">卷将被锁定，需要手动解锁。</span><span class="sxs-lookup"><span data-stu-id="d47ee-264">The volumes will appear locked and need to be manually unlocked.</span></span> <span data-ttu-id="d47ee-265">此操作可在安装了 OEM-DRA 证书的任何计算机上完成， (包含在 [DeviceLockDown 示例](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)) 中。</span><span class="sxs-lookup"><span data-stu-id="d47ee-265">This can be done on any machine that has the OEM-DRA.pfx certificate installed (included in the [DeviceLockDown sample](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)).</span></span> <span data-ttu-id="d47ee-266">安装 PFX，并从管理命令提示符运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d47ee-266">Install the PFX and then run the following commands from an administrative CMD prompt:</span></span>

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

<span data-ttu-id="d47ee-267">如果需要经常脱机访问内容，可以使用以下命令在初始解锁之后为卷设置 BitLocker autounlock：</span><span class="sxs-lookup"><span data-stu-id="d47ee-267">If the contents need to be frequently accessed offline, BitLocker autounlock can be set up for the volumes after the initial unlock using the following commands:</span></span>

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a><span data-ttu-id="d47ee-268">禁用 BitLocker</span><span class="sxs-lookup"><span data-stu-id="d47ee-268">Disabling BitLocker</span></span>

<span data-ttu-id="d47ee-269">如果需要临时禁用 BitLocker，请使用 IoT 设备启动远程 PowerShell 会话，并运行以下命令： `sectask.exe -disable` 。</span><span class="sxs-lookup"><span data-stu-id="d47ee-269">Should there arise a need to temporarily disable BitLocker, initate a remote PowerShell session with your IoT device and run the following command: `sectask.exe -disable`.</span></span>  

> [!NOTE]
> <span data-ttu-id="d47ee-270">除非已禁用计划的加密任务，否则将在随后的设备启动时重新启用设备加密。</span><span class="sxs-lookup"><span data-stu-id="d47ee-270">Device encryption will be re-enabled on subsequent device boot unless the scheduled encryption task is disabled.</span></span>
