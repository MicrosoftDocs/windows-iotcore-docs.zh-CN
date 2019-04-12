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
# <a name="internet-connection-sharing"></a><span data-ttu-id="f5fab-104">Internet 连接共享</span><span class="sxs-lookup"><span data-stu-id="f5fab-104">Internet connection sharing</span></span>

<span data-ttu-id="f5fab-105">本文档介绍如何在 Windows IoT Core 上启用 internet 连接共享 (ICS)。</span><span class="sxs-lookup"><span data-stu-id="f5fab-105">This document describes how internet connection sharing (ICS) can be enabled on Windows IoT Core.</span></span> <span data-ttu-id="f5fab-106">开发人员可以使用 NetworkTetheringManager API 以编程方式配置 ICS。</span><span class="sxs-lookup"><span data-stu-id="f5fab-106">Developers can use the NetworkTetheringManager API to configure ICS programmatically.</span></span> <span data-ttu-id="f5fab-107">在 API 中所述[NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx)类。</span><span class="sxs-lookup"><span data-stu-id="f5fab-107">The API is described in the [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) class.</span></span>
<span data-ttu-id="f5fab-108">使用之一时[Windows 10 IoT Core 版本映像](https://developer.microsoft.com/en-us/windows/iot/downloads)还可以使用设备门户配置 ICS。</span><span class="sxs-lookup"><span data-stu-id="f5fab-108">When using one of the [Windows 10 IoT Core Release Image](https://developer.microsoft.com/en-us/windows/iot/downloads) ICS can also be configured using the device portal.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5fab-109">必须先创建 WiFi 配置文件和以下将需要添加到清单：</span><span class="sxs-lookup"><span data-stu-id="f5fab-109">A WiFi profile must be created first and the following will need to be added to the manifest:</span></span>
`<DeviceCapability Name="wiFiControl" />`

<span data-ttu-id="f5fab-110">在共享教程中，请查看[Windows IoT Core 2015 年 11 月发布](InternetConnectionSharingNov2015.md)文档。</span><span class="sxs-lookup"><span data-stu-id="f5fab-110">For the Sharing Tutorial, please view the [Windows IoT Core November 2015 Release](InternetConnectionSharingNov2015.md) document.</span></span>

## <a name="configuring-ics-using-the-device-portal"></a><span data-ttu-id="f5fab-111">配置使用设备门户 ICS</span><span class="sxs-lookup"><span data-stu-id="f5fab-111">Configuring ICS using the device portal</span></span>
<span data-ttu-id="f5fab-112">请参阅文档[Windows Device Portal](../manage-your-device/deviceportal.md) (WDP)。</span><span class="sxs-lookup"><span data-stu-id="f5fab-112">See documentation on [Windows Device Portal](../manage-your-device/deviceportal.md) (WDP).</span></span>

## <a name="ics-code-sample"></a><span data-ttu-id="f5fab-113">ICS 的代码示例</span><span class="sxs-lookup"><span data-stu-id="f5fab-113">ICS code sample</span></span>
<span data-ttu-id="f5fab-114">下面的代码示例演示如何[NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) API 用于开始通过 Wi-fi 共享以太网连接。</span><span class="sxs-lookup"><span data-stu-id="f5fab-114">The code sample below demonstrates how the [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) API is used to start sharing an Ethernet connection over Wi-Fi.</span></span> <span data-ttu-id="f5fab-115">CreateFromConnectionProfile 方法接受指定公用和专用接口的参数。</span><span class="sxs-lookup"><span data-stu-id="f5fab-115">The CreateFromConnectionProfile method accepts arguments that specifies the public and private interface.</span></span> <span data-ttu-id="f5fab-116">在任何情况下配置不正确的如 Wi-fi 无线电处于关闭状态，或以太网具有有限的连接，在尝试启动 internet 共享传达有关此方案中的相应的错误代码。</span><span class="sxs-lookup"><span data-stu-id="f5fab-116">In any cases of misconfiguration, such as the Wi-Fi radio is turned off, or Ethernet has limited connectivity, then the attempt to start internet sharing conveys an appropriate error code pertaining to this scenario.</span></span>

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
