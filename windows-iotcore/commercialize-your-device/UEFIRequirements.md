---
title: UEFI 要求
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解 Windows 10 IoT 核心版 OS 的 UEFI 要求。 IoT Core 的 UEFI 要求类似于其他 Windows 版本，如 Windows 10 桌面。
keywords: windows iot，映像创建，映像自定义，OEM 自定义，UEFI
ms.openlocfilehash: 8ab0c81fc0bae5526ea6fdff2dbaa49e1cda9cce
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230184"
---
# <a name="uefi-requirements"></a>UEFI 要求

IoT Core 的 UEFI 要求类似于其他 windows 版本（如桌面）。 有关详细信息，请参阅[Windows 中的 uefi](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) ，并特别了解[SoC 平台上 Windows 版本的 uefi 要求](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms)。 

## <a name="acpi-design"></a>ACPI 设计

有关 IoT 核心 acpi 要求的详细信息，请参阅[针对 SoC 平台 Windows acpi 设计指南](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms)。

## <a name="replacing-windows-boot-logo"></a>替换 Windows 启动徽标

有多种方法可以替换 BIOS 或 UEFI 显示的启动徽标：

* 其中一种方法是授权 UEFI，或为板制造商供应商付款，并直接对 UEFI 源代码进行更改。
* 或者，在其 UEFI 实现支持签名的可加载 UEFI 驱动程序的设备上，[此处](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples)提供了一个示例，演示如何构建替换启动徽标的驱动程序，并向 bootmgr 提供 BGRT 表，以便 Windows 引导过程在启动过程中保留徽标，而不是将其替换为 Windows 徽标。

## <a name="smbios-settings"></a>SMBIOS 设置

[OEM 许可证要求](OEMLicenseRequirements.md)中描述了所需的最小 SMBIOS 设置。

## <a name="io-bus-access"></a>I/o 总线访问

Windowsiot Core 和 iot Enterprise 允许用户应用程序与系统 i/o 引脚交互。 若要启用此设置，需要在 ASL 表中进行特定配置。 有关详细信息，请参阅[Windows 10 IoT 核心版上的启用用户模式访问](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access)。

## <a name="recovery-trigger"></a>恢复触发器

查看[Windows 10 IoT 核心版恢复选项](Recovery.md)，如果你需要硬件触发器进入恢复模式，你可能需要在 UEFI 应用中实现此项，并通过在 Windows 启动之前设置所需的 bootsequence 来调用恢复。

以下提供了启动到恢复 OS 所需的 bootsequence

```
bcdedit /set {bootmgr} bootsequence {a5935ff2-32ba-4617-bf36-5ac314b3f9bf}
```
