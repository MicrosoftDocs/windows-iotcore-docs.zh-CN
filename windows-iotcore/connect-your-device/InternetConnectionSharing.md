---
title: Internet 连接共享
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何启用和配置 Windows IoT Core 上的 internet 连接共享。
keywords: windows iot，Internet 连接共享，ICS，设备门户
ms.openlocfilehash: c80a87e4699e9198ac3e45506a7095ba2b351eb9
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656733"
---
# <a name="internet-connection-sharing"></a><span data-ttu-id="29280-104">Internet 连接共享</span><span class="sxs-lookup"><span data-stu-id="29280-104">Internet connection sharing</span></span>

<span data-ttu-id="29280-105">本文档介绍如何在 Windows IoT Core 上启用 (ICS) 的 internet 连接共享。</span><span class="sxs-lookup"><span data-stu-id="29280-105">This document describes how internet connection sharing (ICS) can be enabled on Windows IoT Core.</span></span> <span data-ttu-id="29280-106">开发人员可以使用 NetworkTetheringManager API 以编程方式配置 ICS。</span><span class="sxs-lookup"><span data-stu-id="29280-106">Developers can use the NetworkTetheringManager API to configure ICS programmatically.</span></span> <span data-ttu-id="29280-107">此 API 在 [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) 类中介绍。</span><span class="sxs-lookup"><span data-stu-id="29280-107">The API is described in the [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) class.</span></span>
<span data-ttu-id="29280-108">使用 [Windows 10 IoT Core 版本映像](https://developer.microsoft.com/en-us/windows/iot/downloads) 时，ICS 还可以使用设备门户进行配置。</span><span class="sxs-lookup"><span data-stu-id="29280-108">When using one of the [Windows 10 IoT Core Release Image](https://developer.microsoft.com/en-us/windows/iot/downloads) ICS can also be configured using the device portal.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29280-109">必须先创建 WiFi 配置文件，并将以下内容添加到清单中： `<DeviceCapability Name="wiFiControl" />`</span><span class="sxs-lookup"><span data-stu-id="29280-109">A WiFi profile must be created first and the following will need to be added to the manifest: `<DeviceCapability Name="wiFiControl" />`</span></span>

<span data-ttu-id="29280-110">有关共享教程，请查看 [Windows IoT Core 11 月2015版](InternetConnectionSharingNov2015.md) 文档。</span><span class="sxs-lookup"><span data-stu-id="29280-110">For the Sharing Tutorial, please view the [Windows IoT Core November 2015 Release](InternetConnectionSharingNov2015.md) document.</span></span>

## <a name="configuring-ics-using-the-device-portal"></a><span data-ttu-id="29280-111">使用设备门户配置 ICS</span><span class="sxs-lookup"><span data-stu-id="29280-111">Configuring ICS using the device portal</span></span>
<span data-ttu-id="29280-112">请参阅 [Windows 设备门户](../manage-your-device/deviceportal.md) (WDP) 上的文档。</span><span class="sxs-lookup"><span data-stu-id="29280-112">See documentation on [Windows Device Portal](../manage-your-device/deviceportal.md) (WDP).</span></span>

## <a name="ics-code-sample"></a><span data-ttu-id="29280-113">ICS 代码示例</span><span class="sxs-lookup"><span data-stu-id="29280-113">ICS code sample</span></span>
<span data-ttu-id="29280-114">下面的代码示例演示了如何使用 [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) API 通过 wi-fi 开始共享以太网连接。</span><span class="sxs-lookup"><span data-stu-id="29280-114">The code sample below demonstrates how the [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) API is used to start sharing an Ethernet connection over Wi-Fi.</span></span> <span data-ttu-id="29280-115">CreateFromConnectionProfile 方法接受指定公共和专用接口的参数。</span><span class="sxs-lookup"><span data-stu-id="29280-115">The CreateFromConnectionProfile method accepts arguments that specifies the public and private interface.</span></span> <span data-ttu-id="29280-116">在任何配置错误的情况下（例如 Wi-fi 无线电已关闭，或者以太网的连接受限），尝试启动 internet 共享会传达与此方案相关的相应错误代码。</span><span class="sxs-lookup"><span data-stu-id="29280-116">In any cases of misconfiguration, such as the Wi-Fi radio is turned off, or Ethernet has limited connectivity, then the attempt to start internet sharing conveys an appropriate error code pertaining to this scenario.</span></span>

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
