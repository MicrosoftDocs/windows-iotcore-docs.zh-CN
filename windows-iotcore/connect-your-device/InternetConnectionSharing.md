---
title: Internet 连接共享
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何启用和配置 Windows IoT Core 上共享 internet 连接。
keywords: windows iot，Internet 连接共享，ICS，设备门户
ms.openlocfilehash: dcf51d98bc618c1a843c43b2d33fc8f832ef73d4
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510786"
---
# <a name="internet-connection-sharing"></a>Internet 连接共享

本文档介绍如何在 Windows IoT Core 上启用 internet 连接共享 (ICS)。 开发人员可以使用 NetworkTetheringManager API 以编程方式配置 ICS。 在 API 中所述[NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx)类。
使用之一时[Windows 10 IoT Core 版本映像](https://developer.microsoft.com/en-us/windows/iot/downloads)还可以使用设备门户配置 ICS。

> [!IMPORTANT]
> 必须先创建 WiFi 配置文件和以下将需要添加到清单：
`<DeviceCapability Name="wiFiControl" />`

在共享教程中，请查看[Windows IoT Core 2015 年 11 月发布](InternetConnectionSharingNov2015.md)文档。

## <a name="configuring-ics-using-the-device-portal"></a>配置使用设备门户 ICS
请参阅文档[Windows Device Portal](../manage-your-device/deviceportal.md) (WDP)。

## <a name="ics-code-sample"></a>ICS 的代码示例
下面的代码示例演示如何[NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) API 用于开始通过 Wi-fi 共享以太网连接。 CreateFromConnectionProfile 方法接受指定公用和专用接口的参数。 在任何情况下配置不正确的如 Wi-fi 无线电处于关闭状态，或以太网具有有限的连接，在尝试启动 internet 共享传达有关此方案中的相应的错误代码。

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
