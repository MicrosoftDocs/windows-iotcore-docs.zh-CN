---
title: 移动宽带连接
ms.date: 06/12/2018
ms.topic: article
description: 使用适用于 Windows 10 IoT Core 的 Mobile 宽带连接。 使用 MBBConnect 工具帮助在 IoT Core 中设置移动宽带连接的配置。
keywords: windows iot，MBB，mobile 宽带连接
ms.openlocfilehash: c10e56bc42bf2c77eb74d0e7cd8170cceaa72b75
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782589"
---
# <a name="mobile-broadband-connection"></a><span data-ttu-id="e4701-105">移动宽带连接</span><span class="sxs-lookup"><span data-stu-id="e4701-105">Mobile Broadband Connection</span></span>

<span data-ttu-id="e4701-106">[Windows 10 IoT Core](http://windowsondevices.com)支持移动宽带连接。</span><span class="sxs-lookup"><span data-stu-id="e4701-106">Mobile Broadband Connection is supported on [Windows 10 IoT Core](http://windowsondevices.com).</span></span> <span data-ttu-id="e4701-107">如果 IoT 网关支持移动宽带调制解调器模块，则可以使用该 `MBBConnect` 工具来帮助在 IoT Core 中设置移动宽带连接的配置。</span><span class="sxs-lookup"><span data-stu-id="e4701-107">If your IoT gateway supports the mobile broadband modem module, you can use the `MBBConnect` tool to help set up configurations for mobile broadband connection in IoT Core.</span></span>

<span data-ttu-id="e4701-108">`MBBConnect` 检索连接的相关信息，例如订户 ID、SIM ICC ID、接口名称和 home 提供商名称等。然后，它会创建连接配置文件。</span><span class="sxs-lookup"><span data-stu-id="e4701-108">`MBBConnect` retrieves the relevant information for connect, such as subscriber ID, SIM ICC ID, interface name, and home provider name, etc. Then, it creates the connection profile.</span></span> <span data-ttu-id="e4701-109">你需要执行的唯一操作是提供 APN，并会自动设置连接。</span><span class="sxs-lookup"><span data-stu-id="e4701-109">The only thing you’ll need to do is to provide APN, and it will set up connection automatically.</span></span>

<span data-ttu-id="e4701-110">`MBBConnect` 基于 MinnowBoard 的基于最大的 IoT 网关，运行 IoT Core 版本16299和 mobile 宽带调制解调器模块，并通过台湾的主要电信提供商提供 SIM 卡。</span><span class="sxs-lookup"><span data-stu-id="e4701-110">`MBBConnect` is developed and tested with MinnowBoard Max based IoT gateway running IoT Core version 16299 and the mobile broadband modem module with the SIM card from major telecom provider in Taiwan.</span></span>

### <a name="usage"></a><span data-ttu-id="e4701-111">使用情况</span><span class="sxs-lookup"><span data-stu-id="e4701-111">Usage</span></span>

1. <span data-ttu-id="e4701-112">复制 `MBBConnect.exe` 到 IoT 网关。</span><span class="sxs-lookup"><span data-stu-id="e4701-112">Copy `MBBConnect.exe` to IoT gateway.</span></span>

   * [<span data-ttu-id="e4701-113">FTP</span><span class="sxs-lookup"><span data-stu-id="e4701-113">FTP</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. <span data-ttu-id="e4701-114">通过 PowerShell 或 SSH 连接网关。</span><span class="sxs-lookup"><span data-stu-id="e4701-114">Connect gateway by PowerShell or SSH.</span></span>

   * [<span data-ttu-id="e4701-115">PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4701-115">PowerShell</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [<span data-ttu-id="e4701-116">SSH</span><span class="sxs-lookup"><span data-stu-id="e4701-116">SSH</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. <span data-ttu-id="e4701-117">切换到所在的文件夹 `MBBConnect.exe` 。</span><span class="sxs-lookup"><span data-stu-id="e4701-117">Switch to the folder where `MBBConnect.exe` is located.</span></span> 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a><span data-ttu-id="e4701-118">示例</span><span class="sxs-lookup"><span data-stu-id="e4701-118">Example</span></span>
<span data-ttu-id="e4701-119">下面的示例在 PowerShell 中使用 MBBConnect.exe。</span><span class="sxs-lookup"><span data-stu-id="e4701-119">The example below uses MBBConnect.exe in PowerShell.</span></span> <span data-ttu-id="e4701-120">例如，如果 SIM 卡的 APN 是 "Internet"，请使用 `MBBConnect.exe Internet` 进行连接。</span><span class="sxs-lookup"><span data-stu-id="e4701-120">For example, if the APN of the SIM card is “Internet”, use `MBBConnect.exe Internet` to connect.</span></span>
 
<span data-ttu-id="e4701-121">输出消息将显示流：</span><span class="sxs-lookup"><span data-stu-id="e4701-121">The output message will show the flow:</span></span>

* <span data-ttu-id="e4701-122">状态从 "未连接" 更改为 "已连接"。</span><span class="sxs-lookup"><span data-stu-id="e4701-122">The state is changed from Not Connected to Connected.</span></span> 

* <span data-ttu-id="e4701-123">已成功配置 WWAN 网络。</span><span class="sxs-lookup"><span data-stu-id="e4701-123">WWAN network is configured successfully.</span></span>

<span data-ttu-id="e4701-124">[在此处](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect)试用移动宽带连接的示例。</span><span class="sxs-lookup"><span data-stu-id="e4701-124">Try the sample for Mobile Broadband Connection [here](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect).</span></span>
