---
title: Internet 连接共享
ms.date: 08/28/2017
ms.topic: article
description: 了解如何启用和配置 Windows IoT Core 上的 internet 连接共享。
keywords: windows iot，Internet 连接共享，ICS，设备门户
ms.openlocfilehash: 6392ef8b6216b9e622e308f8e1988655ebebee53
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918576"
---
# <a name="internet-connection-sharing"></a>Internet 连接共享

本文档介绍如何在 Windows IoT Core 上启用 internet 连接共享（ICS）。 开发人员可以使用 NetworkTetheringManager API 以编程方式配置 ICS。 此 API 在[NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx)类中介绍。
使用[Windows 10 IoT Core 版本映像](https://developer.microsoft.com/en-us/windows/iot/downloads)时，ICS 还可以使用设备门户进行配置。

> [!IMPORTANT]
> 必须首先创建 WiFi 配置文件，需要将以下内容添加到清单中： `<DeviceCapability Name="wiFiControl" />`

有关共享教程，请查看[Windows IoT Core 11 月2015版](InternetConnectionSharingNov2015.md)文档。

## <a name="configuring-ics-using-the-device-portal"></a>使用设备门户配置 ICS
请参阅[Windows 设备门户](../manage-your-device/deviceportal.md)上的文档（WDP）。

## <a name="ics-code-sample"></a>ICS 代码示例
下面的代码示例演示了如何使用[NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) API 通过 wi-fi 开始共享以太网连接。 CreateFromConnectionProfile 方法接受指定公共和专用接口的参数。 在任何配置错误的情况下（例如 Wi-fi 无线电已关闭，或者以太网的连接受限），尝试启动 internet 共享会传达与此方案相关的相应错误代码。

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
