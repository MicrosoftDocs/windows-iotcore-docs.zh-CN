---
title: 安装 USB 外围设备驱动程序
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何创建驱动程序包并在设备上安装第三方驱动程序。
keywords: windows iot、 USB 驱动程序、 USB 外围设备
ms.openlocfilehash: dd7eec9defc676bb84efe988d771794d9bb7c9ef
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510939"
---
# <a name="install-usb-peripheral-drivers"></a>安装 USB 外围设备驱动程序
请按照以下步骤来添加用于外围设备，例如 USB 移动宽带调制解调器、 打印机、 扫描仪等第三方驱动程序 (usb)。 

## <a name="step-1-get-drivers-from-pc"></a>第 1 步：从 PC 获得驱动程序
___
此步骤将获取 x86 版本的驱动程序从 PC。 对于 ARM，请联系外围设备的供应商来获取 sys/inf 文件。


1. 将设备连接到 windows PC

2. 在 PC 上安装设备驱动程序

3. 转到设备管理器中，选择此设备 （在通用串行总线控制器下所列） 和右键单击并选择属性。

4. 转到属性窗口中的驱动程序选项卡，然后单击驱动程序详细信息。 请注意那里列出的 sys 文件。

5. 中的 sys 文件复制`C:\Windows\system32`和 inf 文件从还相关的`C:\Windows\Inf`。 您可以查找的 inf 文件通过在 sys 中的文件引用`.inf`文件。 可能需要将 Inf 中列出的其他文件复制，并且将在创建时使用的 inf_filelist.txt 文件列出这些`inf2pkg.cmd`在下一步。


## <a name="step-2-create-a-driver-package"></a>步骤 2：创建驱动程序包
___

驱动程序包的驱动程序的 Inf 文件到包含引用 (InfSource)，并还列出了在 Inf 文件中引用的所有文件。 可以编写驱动程序。 使用 wm.xml[新建 IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md)。

[新 IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md)创建包 xml 文件，并还直接生成 cab 文件。

> [!NOTE]
> 仅支持 Windows IoT Core[通用 INF 和通用驱动程序](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers)。


另请参阅：[示例驱动程序包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO) 

## <a name="step-3-install-on-device"></a>步骤 3:在设备上安装
___

* 连接到设备 ([使用 SSH](../connect-your-device/ssh.md)或[使用 Powershell](../connect-your-device/powershell.md))
* 复制<filename>到目录的设备的.cab 文件说 C:\OemInstall
* 启动包使用的临时`applyupdate -stage C:\OemInstall\<filename>.cab`。 请注意，此步骤被重复的每个包，当有多个包安装时。
* 提交使用的包`applyupdate -commit`。

设备将重新启动进入更新 OS （显示齿轮） 来安装包，并将再次重新启动到主操作系统。 此过程可能需要几分钟。

## <a name="step-4-check-status-of-driver"></a>步骤 4：检查驱动程序的状态
___

* 启动[Powershell](../connect-your-device/PowerShell.md)
* 就可以使用以下 Powershell commandlet 安装驱动程序的状态

    * [Get-PnpDevice](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdevice?view=win10-ps)
    * [Get-PnpDeviceProperty](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdeviceproperty?view=win10-ps)
    
