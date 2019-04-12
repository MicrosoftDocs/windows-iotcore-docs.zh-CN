---
title: UEFI 要求
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 了解 Windows 10 IoT 核心版操作系统的 UEFI 要求。
keywords: windows iot、 创建映像、 映像自定义项、 UEFI 的 OEM 自定义
ms.openlocfilehash: efd8f104d61667b443d48e1722e26789a490196b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510615"
---
# <a name="uefi-requirements"></a><span data-ttu-id="ad952-104">UEFI 要求</span><span class="sxs-lookup"><span data-stu-id="ad952-104">UEFI Requirements</span></span>

<span data-ttu-id="ad952-105">IoT 核心版的 UEFI 要求都类似于桌面等其他 windows 版本。</span><span class="sxs-lookup"><span data-stu-id="ad952-105">The UEFI requirements for IoT Core are similar to other windows editions like desktop.</span></span> <span data-ttu-id="ad952-106">请参阅[Windows 中的 UEFI](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows)有关详细信息和具体而言，请参阅[SoC 平台上的 Windows 版本的 UEFI 要求](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms)。</span><span class="sxs-lookup"><span data-stu-id="ad952-106">See [UEFI in Windows](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) for details and specifically see [UEFI requirements for Windows editions on SoC platforms](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms).</span></span> 

## <a name="acpi-design"></a><span data-ttu-id="ad952-107">ACPI 设计</span><span class="sxs-lookup"><span data-stu-id="ad952-107">ACPI Design</span></span>

<span data-ttu-id="ad952-108">请参阅[SoC 平台的 Windows ACPI 设计指南](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms)有关 IoT 核心版的 ACPI 要求的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ad952-108">See [Windows ACPI design guide for SoC platforms](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) for the details on the ACPI requirements for IoT Core.</span></span>

## <a name="replacing-windows-boot-logo"></a><span data-ttu-id="ad952-109">替换为 Windows 启动徽标</span><span class="sxs-lookup"><span data-stu-id="ad952-109">Replacing Windows Boot Logo</span></span>

<span data-ttu-id="ad952-110">有多种方法来替换显示的 BIOS 或 UEFI 启动徽标：</span><span class="sxs-lookup"><span data-stu-id="ad952-110">There are multiple ways to replace the boot logo that is displayed by the BIOS or UEFI:</span></span>

* <span data-ttu-id="ad952-111">一种方法是许可证 UEFI，或支付主板制造商供应商，以执行此操作，并直接对 UEFI 源代码进行更改。</span><span class="sxs-lookup"><span data-stu-id="ad952-111">One way is to license the UEFI, or pay a board manufacturer vendor to do so, and make changes directly to the UEFI source code.</span></span>
* <span data-ttu-id="ad952-112">或者，在其 UEFI 实现支持签名可加载的 UEFI 驱动程序的设备上提供了一个示例[此处](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples)，演示如何生成替换引导驱动程序并提供给 bootmgr BGRT 表，以便 Windows 启动过程保留你的徽标在位置而不是替换带有 Windows 徽标的启动过程。</span><span class="sxs-lookup"><span data-stu-id="ad952-112">Alternatively, on devices whose UEFI implementation supports signed loadable UEFI drivers there is a sample [here](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) that shows how to build a driver that replaces the boot logo and supply a BGRT table to bootmgr so that the Windows boot process leaves your logo in place during boot instead of replacing it with the Windows logo.</span></span>

## <a name="smbios-settings"></a><span data-ttu-id="ad952-113">SMBIOS 设置</span><span class="sxs-lookup"><span data-stu-id="ad952-113">SMBIOS settings</span></span>

<span data-ttu-id="ad952-114">SMBIOS 设置进行了介绍所需的最低[OEM 许可要求](OEMLicenseRequirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad952-114">Minimum required SMBIOS settings are described in [OEM License Requirements](OEMLicenseRequirements.md).</span></span>

## <a name="io-bus-access"></a><span data-ttu-id="ad952-115">I/O 总线的访问</span><span class="sxs-lookup"><span data-stu-id="ad952-115">I/O Bus Access</span></span>

<span data-ttu-id="ad952-116">Windows IoT Core 和 IoT 企业版允许用户与系统 I/O pin 进行交互的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ad952-116">Windows IoT Core and IoT Enterprise allow for user applications to interface with system I/O pins.</span></span> <span data-ttu-id="ad952-117">若要启用此功能，ASL 表中需要特定的配置。</span><span class="sxs-lookup"><span data-stu-id="ad952-117">To enable this, specific configuration is required in the ASL table.</span></span> <span data-ttu-id="ad952-118">读取[启用 Windows 10 IoT Core 上的用户模式访问](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access)有关详细信息。</span><span class="sxs-lookup"><span data-stu-id="ad952-118">Read [Enable user mode access on Windows 10 IoT Core](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) for more information.</span></span>

## <a name="recovery-trigger"></a><span data-ttu-id="ad952-119">恢复触发器</span><span class="sxs-lookup"><span data-stu-id="ad952-119">Recovery Trigger</span></span>

<span data-ttu-id="ad952-120">审阅[Windows 10 IoT Core 恢复选项](Recovery.md)，如果需要硬件触发器进入恢复模式下，可能需要能够 UEFI 应用程序中实现这一点并设置 windows 启动之前所需的 bootsequence 调用恢复.</span><span class="sxs-lookup"><span data-stu-id="ad952-120">Review [Windows 10 IoT Core Recovery Options](Recovery.md) and if you require hardware trigger to get into recovery mode, you may require to implement this in the UEFI apps and invoke recovery by setting the required bootsequence before windows boots.</span></span>

<span data-ttu-id="ad952-121">下面提供了所需启动到恢复 OS bootsequence</span><span class="sxs-lookup"><span data-stu-id="ad952-121">The bootsequence required to boot into the recovery OS is given below</span></span>

```
bcdedit /set {bootmgr} bootsequence {a5935ff2-32ba-4617-bf36-5ac314b3f9bf}
```
