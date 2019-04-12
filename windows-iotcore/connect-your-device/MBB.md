---
title: 移动宽带连接
author: saraclay
ms.author: saclayt
ms.date: 06/12/18
ms.topic: article
description: 了解如何使用移动宽带连接的 Windows 10 IoT Core。
keywords: windows iot，MBB，移动宽带连接
ms.openlocfilehash: 3afa48e049e38f7e26308434ba6f7349ac0be050
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510937"
---
## <a name="mobile-broadband-connection"></a><span data-ttu-id="cbf16-104">移动宽带连接</span><span class="sxs-lookup"><span data-stu-id="cbf16-104">Mobile Broadband Connection</span></span>

<span data-ttu-id="cbf16-105">支持的移动宽带连接[Windows 10 IoT Core](http://windowsondevices.com)。</span><span class="sxs-lookup"><span data-stu-id="cbf16-105">Mobile Broadband Connection is supported on [Windows 10 IoT Core](http://windowsondevices.com).</span></span> <span data-ttu-id="cbf16-106">如果你的 IoT 网关支持的移动宽带调制解调器模块，可以使用`MBBConnect`工具，可帮助 IoT Core 中的移动宽带连接的安装程序配置。</span><span class="sxs-lookup"><span data-stu-id="cbf16-106">If your IoT gateway supports the mobile broadband modem module, you can use the `MBBConnect` tool to help setup configurations for mobile broadband connection in IoT Core.</span></span>

`MBBConnect` <span data-ttu-id="cbf16-107">检索连接中，订阅者 ID、 SIM ICC ID、 接口名称和家庭提供程序名称等的相关信息。然后，创建连接配置文件。</span><span class="sxs-lookup"><span data-stu-id="cbf16-107">retrieves the relevant information for connect, such as subscriber ID, SIM ICC ID, interface name, and home provider name, etc. Then, it creates the connection profile.</span></span> <span data-ttu-id="cbf16-108">将需要执行操作的唯一是提供 APN，并且它将自动设置连接。</span><span class="sxs-lookup"><span data-stu-id="cbf16-108">The only thing you’ll need to do is to provide APN, and it’ll setup connection automatically.</span></span>

`MBBConnect` <span data-ttu-id="cbf16-109">是开发和测试使用 MinnowBoard 最大值基于运行 IoT Core 版本 16299 和移动宽带调制解调器模块的 SIM 卡从主要电信提供商在中国台湾地区的 IoT 网关。</span><span class="sxs-lookup"><span data-stu-id="cbf16-109">is developed and tested with MinnowBoard Max based IoT gateway running IoT Core version 16299 and the mobile broadband modem module with the SIM card from major telecom provider in Taiwan.</span></span>

### <a name="usage"></a><span data-ttu-id="cbf16-110">用法</span><span class="sxs-lookup"><span data-stu-id="cbf16-110">Usage</span></span>

1. <span data-ttu-id="cbf16-111">复制`MBBConnect.exe`到 IoT 网关。</span><span class="sxs-lookup"><span data-stu-id="cbf16-111">Copy `MBBConnect.exe` to IoT gateway.</span></span>

   * [<span data-ttu-id="cbf16-112">FTP</span><span class="sxs-lookup"><span data-stu-id="cbf16-112">FTP</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. <span data-ttu-id="cbf16-113">网关通过 Powershell 或 SSH 连接。</span><span class="sxs-lookup"><span data-stu-id="cbf16-113">Connect gateway by Powershell or SSH.</span></span>

   * [<span data-ttu-id="cbf16-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="cbf16-114">PowerShell</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [<span data-ttu-id="cbf16-115">SSH</span><span class="sxs-lookup"><span data-stu-id="cbf16-115">SSH</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. <span data-ttu-id="cbf16-116">切换到的文件夹位置`MBBConnect.exe`所在。</span><span class="sxs-lookup"><span data-stu-id="cbf16-116">Switch to the folder where `MBBConnect.exe` is located.</span></span> 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a><span data-ttu-id="cbf16-117">示例</span><span class="sxs-lookup"><span data-stu-id="cbf16-117">Example</span></span>
<span data-ttu-id="cbf16-118">下面的示例在 PowerShell 中使用 MBBConnect.exe。</span><span class="sxs-lookup"><span data-stu-id="cbf16-118">The example below uses MBBConnect.exe in PowerShell.</span></span> <span data-ttu-id="cbf16-119">例如，如果此 APN SIM 卡的"Internet"，请使用`MBBConnect.exe Internet`连接。</span><span class="sxs-lookup"><span data-stu-id="cbf16-119">For example, if the APN of the SIM card is “Internet”, use `MBBConnect.exe Internet` to connect.</span></span>
 
<span data-ttu-id="cbf16-120">输出消息会显示该流：</span><span class="sxs-lookup"><span data-stu-id="cbf16-120">The output message will show the flow:</span></span>

* <span data-ttu-id="cbf16-121">状态将变为未连接从已连接。</span><span class="sxs-lookup"><span data-stu-id="cbf16-121">The state is changed from Not Connected to Connected.</span></span> 

* <span data-ttu-id="cbf16-122">已成功配置 WWAN 网络。</span><span class="sxs-lookup"><span data-stu-id="cbf16-122">WWAN network is configured successfully.</span></span>

<span data-ttu-id="cbf16-123">移动宽带连接尝试示例[此处](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect)。</span><span class="sxs-lookup"><span data-stu-id="cbf16-123">Try the sample for Mobile Broadband Connection [here](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect).</span></span>
