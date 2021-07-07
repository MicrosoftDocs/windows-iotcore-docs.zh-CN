---
title: Internet 连接共享
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何在 IoT Core 上启用和Windows Internet 连接共享。
keywords: windows iot、Internet 连接共享、ICS、设备门户
ms.openlocfilehash: 69ee300ed003f3fd39a154780a07cd9de91a0e71
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230014"
---
# <a name="internet-connection-sharing"></a>Internet 连接共享

本文档介绍如何在 IoT 核心 (ICS) Internet Windows共享。 开发人员可以使用 NetworkTetheringManager API 以编程方式配置 ICS。 [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx)类中介绍了 API。
使用其中一个[Windows 10 IoT 核心版](https://developer.microsoft.com/en-us/windows/iot/downloads)也可使用设备门户配置发布映像 ICS。

> [!IMPORTANT]
> 必须先创建 WiFi 配置文件，并且需要将以下内容添加到清单中： `<DeviceCapability Name="wiFiControl" />`

有关共享教程，请查看 Windows [IoT Core 2015 年 11 月版本文档](InternetConnectionSharingNov2015.md)。

## <a name="configuring-ics-using-the-device-portal"></a>使用设备门户配置 ICS
请参阅有关[Windows 设备门户](../manage-your-device/deviceportal.md) (WDP) 的文档。

## <a name="ics-code-sample"></a>ICS 代码示例
下面的代码示例演示如何使用 [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) API 通过 Wi-Fi 开始共享以太网连接。 CreateFromConnectionProfile 方法接受指定公共和专用接口的参数。 在任何配置错误的情况下（例如 Wi-Fi 无线电已关闭或以太网连接受限）时，尝试启动 Internet 共享会传达与此方案相关的相应错误代码。

```
using Windows.Networking.NetworkOperators;
using Windows.Networking.Connectivity; 
 
// Find the Ethernet profile (IANA Type 6)
var connectionProfiles = NetworkInformation.GetConnectionProfiles(); 
var ethernetConnectionProfile = connectionProfiles.FirstOrDefault(x => x.NetworkAdapter.IanaInterfaceType == 6); 

// Find an 802.11 wireless network interface (IANA Type 71)
var wirelessConnectionProfile = connectionProfiles.FirstOrDefault(x => x.NetworkAdapter.IanaInterfaceType == 71);
var targetNetworkAdapter = wirelessConnectionProfile.NetworkAdapter;

if (ethernetConnectionProfile != null && targetNetworkAdapter != null)
{
    var tetheringManager = NetworkOperatorTetheringManager.CreateFromConnectionProfile(ethernetConnectionProfile, targetNetworkAdapter); 

    var result = await tetheringManager.StartTetheringAsync(); 
    if (result.Status == TetheringOperationStatus.Success)
    {
        UpdateUI();
    }
    else
    {
        ProcessTetheringError(result);
    }
}
```
