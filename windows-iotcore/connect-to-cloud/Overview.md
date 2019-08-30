---
title: 云上的 IoT 概述
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 使用 Azure IoT 了解如何通过云进行消息传送、安全和设备管理。
keywords: windows iot, cloud, Azure, Azure IoT 中心, 消息传送, UWP, 通用 Windows 平台
ms.openlocfilehash: 4f38a45836e7c474655819988e447137249c2a7f
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170055"
---
# <a name="overview-of-iot-on-the-cloud"></a><span data-ttu-id="5ee54-104">云上的 IoT 概述</span><span class="sxs-lookup"><span data-stu-id="5ee54-104">Overview of IoT on the Cloud</span></span>

<span data-ttu-id="5ee54-105">物联网基于云计算构建。</span><span class="sxs-lookup"><span data-stu-id="5ee54-105">The Internet of Things is built on cloud computing.</span></span> <span data-ttu-id="5ee54-106">与云进行通信并从数据中获取见解的功能是任何 IoT 项目的重要组成部分。</span><span class="sxs-lookup"><span data-stu-id="5ee54-106">The ability to communicate with the cloud and derive insight from the data is an essential part of any IoT project.</span></span>

## <a name="messaging"></a><span data-ttu-id="5ee54-107">消息</span><span class="sxs-lookup"><span data-stu-id="5ee54-107">Messaging</span></span>

<span data-ttu-id="5ee54-108">通常, IoT 设备通过发送和接收消息与云或彼此通信。</span><span class="sxs-lookup"><span data-stu-id="5ee54-108">Usually, IoT devices communicate with the cloud or each other by sending and receiving messages.</span></span> <span data-ttu-id="5ee54-109">从设备发送到云的消息的有效负载可以小到传感器的值, 也可以像视频文件一样小。</span><span class="sxs-lookup"><span data-stu-id="5ee54-109">The payload of a message sent from the device to cloud can be as small as a value from a sensor and as big as a video file.</span></span> <span data-ttu-id="5ee54-110">云到设备的消息通常是指示设备执行操作的命令。</span><span class="sxs-lookup"><span data-stu-id="5ee54-110">A cloud to device message is typically a command instructing the device to perform an action.</span></span>


<span data-ttu-id="5ee54-111">消息传递通信模式的复杂性不同于从简单单向消息传递到更复杂的协议, 如请求响应或事务协议 (如两阶段提交)。</span><span class="sxs-lookup"><span data-stu-id="5ee54-111">Message-passing communication patterns vary in complexity ranging from simple one-way messaging to more complex protocols such as request-response or transactional protocols such as the two-phase commit.</span></span>

## <a name="security"></a><span data-ttu-id="5ee54-112">安全性</span><span class="sxs-lookup"><span data-stu-id="5ee54-112">Security</span></span>

<span data-ttu-id="5ee54-113">安全是 IoT 的重要组成部分。</span><span class="sxs-lookup"><span data-stu-id="5ee54-113">Security is an essential part of IoT.</span></span> <span data-ttu-id="5ee54-114">对于每条消息, 我们必须确保它来自受信任的设备 (或接收), 并且不会被篡改。</span><span class="sxs-lookup"><span data-stu-id="5ee54-114">For each message, we must ensure that it comes from (or is received by) a trusted device and is not tampered with.</span></span> <span data-ttu-id="5ee54-115">数据可以包含必须加密的信息。</span><span class="sxs-lookup"><span data-stu-id="5ee54-115">The data can contain information that must be encrypted.</span></span>

## <a name="azure-iot-hub"></a><span data-ttu-id="5ee54-116">Azure IoT 中心</span><span class="sxs-lookup"><span data-stu-id="5ee54-116">Azure IoT Hub</span></span>

<span data-ttu-id="5ee54-117">[Azure IoT 中心](https://azure.microsoft.com/services/iot-hub/)是一项 azure 云服务, 可提供可靠且安全的设备到云和云到设备的消息传送功能, 可扩展到数百万台设备。</span><span class="sxs-lookup"><span data-stu-id="5ee54-117">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/) is an Azure cloud service that offers reliable and secure device-to-cloud and cloud-to-device messaging that scales to millions of devices.</span></span> <span data-ttu-id="5ee54-118">它提供了一种简化的编程模型, 可让你快速入门, 并随着需求的增加而扩展解决方案。</span><span class="sxs-lookup"><span data-stu-id="5ee54-118">It offers a streamlined programming model that lets you get started with minimum effort and scale up your solution as its needs grow.</span></span>

