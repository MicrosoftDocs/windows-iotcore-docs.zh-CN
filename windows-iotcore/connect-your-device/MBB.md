---
title: 移动宽带连接
author: saraclay
ms.author: saclayt
ms.date: 06/12/18
ms.topic: article
description: 了解如何使用适用于 Windows 10 IoT Core 的 Mobile 宽带连接。
keywords: windows iot, MBB, mobile 宽带连接
ms.openlocfilehash: 3afa48e049e38f7e26308434ba6f7349ac0be050
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168045"
---
## <a name="mobile-broadband-connection"></a><span data-ttu-id="0dff0-104">移动宽带连接</span><span class="sxs-lookup"><span data-stu-id="0dff0-104">Mobile Broadband Connection</span></span>

<span data-ttu-id="0dff0-105">[Windows 10 IoT Core](http://windowsondevices.com)支持移动宽带连接。</span><span class="sxs-lookup"><span data-stu-id="0dff0-105">Mobile Broadband Connection is supported on [Windows 10 IoT Core](http://windowsondevices.com).</span></span> <span data-ttu-id="0dff0-106">如果 iot 网关支持移动宽带调制解调器模块, 则可以使用该`MBBConnect`工具来帮助在 IoT Core 中设置移动宽带连接的配置。</span><span class="sxs-lookup"><span data-stu-id="0dff0-106">If your IoT gateway supports the mobile broadband modem module, you can use the `MBBConnect` tool to help setup configurations for mobile broadband connection in IoT Core.</span></span>

<span data-ttu-id="0dff0-107">`MBBConnect`检索连接的相关信息, 例如订户 ID、SIM ICC ID、接口名称和 home 提供商名称等。然后, 它会创建连接配置文件。</span><span class="sxs-lookup"><span data-stu-id="0dff0-107">`MBBConnect` retrieves the relevant information for connect, such as subscriber ID, SIM ICC ID, interface name, and home provider name, etc. Then, it creates the connection profile.</span></span> <span data-ttu-id="0dff0-108">您需要做的唯一事情是提供 APN, 并自动设置连接。</span><span class="sxs-lookup"><span data-stu-id="0dff0-108">The only thing you’ll need to do is to provide APN, and it’ll setup connection automatically.</span></span>

<span data-ttu-id="0dff0-109">`MBBConnect`基于 MinnowBoard 的基于最大的 IoT 网关, 运行 IoT Core 版本16299和 mobile 宽带调制解调器模块, 并通过台湾的主要电信提供商提供 SIM 卡。</span><span class="sxs-lookup"><span data-stu-id="0dff0-109">`MBBConnect` is developed and tested with MinnowBoard Max based IoT gateway running IoT Core version 16299 and the mobile broadband modem module with the SIM card from major telecom provider in Taiwan.</span></span>

### <a name="usage"></a><span data-ttu-id="0dff0-110">用法</span><span class="sxs-lookup"><span data-stu-id="0dff0-110">Usage</span></span>

1. <span data-ttu-id="0dff0-111">复制`MBBConnect.exe`到 IoT 网关。</span><span class="sxs-lookup"><span data-stu-id="0dff0-111">Copy `MBBConnect.exe` to IoT gateway.</span></span>

   * [<span data-ttu-id="0dff0-112">FTP</span><span class="sxs-lookup"><span data-stu-id="0dff0-112">FTP</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. <span data-ttu-id="0dff0-113">通过 Powershell 或 SSH 连接网关。</span><span class="sxs-lookup"><span data-stu-id="0dff0-113">Connect gateway by Powershell or SSH.</span></span>

   * [<span data-ttu-id="0dff0-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="0dff0-114">PowerShell</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [<span data-ttu-id="0dff0-115">SSH</span><span class="sxs-lookup"><span data-stu-id="0dff0-115">SSH</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. <span data-ttu-id="0dff0-116">切换到所在的文件夹`MBBConnect.exe` 。</span><span class="sxs-lookup"><span data-stu-id="0dff0-116">Switch to the folder where `MBBConnect.exe` is located.</span></span> 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a><span data-ttu-id="0dff0-117">示例</span><span class="sxs-lookup"><span data-stu-id="0dff0-117">Example</span></span>
<span data-ttu-id="0dff0-118">下面的示例在 PowerShell 中使用 MBBConnect。</span><span class="sxs-lookup"><span data-stu-id="0dff0-118">The example below uses MBBConnect.exe in PowerShell.</span></span> <span data-ttu-id="0dff0-119">例如, 如果 SIM 卡的 APN 是 "Internet", 请使用`MBBConnect.exe Internet`进行连接。</span><span class="sxs-lookup"><span data-stu-id="0dff0-119">For example, if the APN of the SIM card is “Internet”, use `MBBConnect.exe Internet` to connect.</span></span>
 
<span data-ttu-id="0dff0-120">输出消息将显示流:</span><span class="sxs-lookup"><span data-stu-id="0dff0-120">The output message will show the flow:</span></span>

* <span data-ttu-id="0dff0-121">状态从 "未连接" 更改为 "已连接"。</span><span class="sxs-lookup"><span data-stu-id="0dff0-121">The state is changed from Not Connected to Connected.</span></span> 

* <span data-ttu-id="0dff0-122">已成功配置 WWAN 网络。</span><span class="sxs-lookup"><span data-stu-id="0dff0-122">WWAN network is configured successfully.</span></span>

<span data-ttu-id="0dff0-123">[在此处](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect)试用移动宽带连接的示例。</span><span class="sxs-lookup"><span data-stu-id="0dff0-123">Try the sample for Mobile Broadband Connection [here](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect).</span></span>
