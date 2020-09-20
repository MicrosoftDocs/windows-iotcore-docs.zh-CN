---
title: 安装 USB 外设驱动程序
ms.date: 08/28/2017
ms.topic: article
description: 了解如何创建驱动程序包，以及如何在设备上安装第三方驱动程序。
keywords: windows iot，USB 驱动程序，外围设备，USB
ms.openlocfilehash: ba7bc025bfd9f2a375d501d46aed160ede4e1997
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782639"
---
# <a name="install-usb-peripheral-drivers"></a>安装 USB 外设驱动程序
按照以下步骤为外围设备（如 USB 移动宽带调制解调器、打印机、扫描仪等）添加 (USB) 的第三方驱动程序。 

## <a name="step-1-get-drivers-from-pc"></a>步骤1：从电脑获取驱动程序
___
步骤是从 PC 获取驱动程序的 x86 版本。 对于 ARM，请联系外围设备的供应商以获取 sys/inf 文件。


1. 将设备连接到 windows 电脑

2. 在电脑上安装设备驱动程序

3. 请参阅设备管理器，选择 "通用串行总线控制器" 下列出的此设备 () ，然后右键单击并选择 "属性"。

4. 在属性窗口中转到 "驱动程序" 选项卡，然后单击 "驱动程序详细信息"。 请注意列出的 sys 文件。

5. 从复制 sys 文件 `C:\Windows\system32` ，并从中复制相关的 inf 文件 `C:\Windows\Inf` 。 可以通过在文件中搜索 sys 文件引用来查找 inf 文件 `.inf` 。 你可能需要复制 Inf 中列出的其他文件，这些文件将在  `inf2pkg.cmd` 下一步中使用时创建的 inf_filelist.txt 文件中列出。


## <a name="step-2-create-a-driver-package"></a>步骤2：创建驱动程序包
___

驱动程序包包含 (InfSource) 到驱动程序的 Inf 文件的引用，还列出了 Inf 文件中引用的所有文件。 您可以使用 [IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md)创作驱动程序 .wm.xml。

[IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) 创建包 xml 文件，还直接生成 cab 文件。

> [!NOTE]
> Windows IoT Core 仅支持 [通用 INF 和通用驱动程序](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)。


另请参阅： [示例驱动程序包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO) 

## <a name="step-3-install-on-device"></a>步骤3：在设备上安装
___

* [使用 SSH](../connect-your-device/ssh.md)或[PowerShell](../connect-your-device/powershell.md)连接到设备 () 
* 将 <filename> .cab 文件复制到该目录中，如 C:\OemInstall
* 使用启动包的临时 `applyupdate -stage C:\OemInstall\<filename>.cab` 。 请注意，当你有多个要安装的包时，将对每个包重复此步骤。
* 使用提交包 `applyupdate -commit` 。

设备将重新启动到更新 OS (显示齿轮) 来安装包，并再次重新启动到主操作系统。 此过程会花费几分钟时间。

## <a name="step-4-check-status-of-driver"></a>步骤4：检查驱动程序的状态
___

* 启动 [PowerShell](../connect-your-device/PowerShell.md)
* 可以使用以下 PowerShell commandlet 获取已安装驱动程序的状态

    * [Pnp 设备](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdevice?view=win10-ps)
    * [PnpDeviceProperty](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdeviceproperty?view=win10-ps)
    
