---
title: 在云上 IoT 的概述
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 与使用 Azure IoT 云了解有关消息传送、 安全性和设备管理。
keywords: windows iot，云，Azure，Azure IoT 中心，消息传送，UWP，通用 Windows 平台
ms.openlocfilehash: 4f38a45836e7c474655819988e447137249c2a7f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510934"
---
# <a name="overview-of-iot-on-the-cloud"></a><span data-ttu-id="b8129-104">在云上 IoT 的概述</span><span class="sxs-lookup"><span data-stu-id="b8129-104">Overview of IoT on the Cloud</span></span>

<span data-ttu-id="b8129-105">物联网基于云计算。</span><span class="sxs-lookup"><span data-stu-id="b8129-105">The Internet of Things is built on cloud computing.</span></span> <span data-ttu-id="b8129-106">与云通信和从数据获取见解的能力是必不可少的组成部分任何 IoT 项目。</span><span class="sxs-lookup"><span data-stu-id="b8129-106">The ability to communicate with the cloud and derive insight from the data is an essential part of any IoT project.</span></span>

## <a name="messaging"></a><span data-ttu-id="b8129-107">消息</span><span class="sxs-lookup"><span data-stu-id="b8129-107">Messaging</span></span>

<span data-ttu-id="b8129-108">通常情况下，IoT 设备与云或相互通信的发送和接收消息。</span><span class="sxs-lookup"><span data-stu-id="b8129-108">Usually, IoT devices communicate with the cloud or each other by sending and receiving messages.</span></span> <span data-ttu-id="b8129-109">从设备发送到云的消息的负载可以为最小可为从传感器和视频文件一样大的值。</span><span class="sxs-lookup"><span data-stu-id="b8129-109">The payload of a message sent from the device to cloud can be as small as a value from a sensor and as big as a video file.</span></span> <span data-ttu-id="b8129-110">云到设备的消息通常是一个命令，指示设备执行操作。</span><span class="sxs-lookup"><span data-stu-id="b8129-110">A cloud to device message is typically a command instructing the device to perform an action.</span></span>


<span data-ttu-id="b8129-111">在复杂性范围从简单的单向消息传送到更复杂的协议，如请求-响应或如两阶段提交的事务协议不同消息传递通信模式。</span><span class="sxs-lookup"><span data-stu-id="b8129-111">Message-passing communication patterns vary in complexity ranging from simple one-way messaging to more complex protocols such as request-response or transactional protocols such as the two-phase commit.</span></span>

## <a name="security"></a><span data-ttu-id="b8129-112">安全性</span><span class="sxs-lookup"><span data-stu-id="b8129-112">Security</span></span>

<span data-ttu-id="b8129-113">安全性是必不可少的组成部分 IoT。</span><span class="sxs-lookup"><span data-stu-id="b8129-113">Security is an essential part of IoT.</span></span> <span data-ttu-id="b8129-114">对于每个消息中，我们必须确保它来自 （或接收的） 受信任的设备以及未篡改。</span><span class="sxs-lookup"><span data-stu-id="b8129-114">For each message, we must ensure that it comes from (or is received by) a trusted device and is not tampered with.</span></span> <span data-ttu-id="b8129-115">数据可能包含必须加密的信息。</span><span class="sxs-lookup"><span data-stu-id="b8129-115">The data can contain information that must be encrypted.</span></span>

## <a name="azure-iot-hub"></a><span data-ttu-id="b8129-116">Azure IoT 中心</span><span class="sxs-lookup"><span data-stu-id="b8129-116">Azure IoT Hub</span></span>

<span data-ttu-id="b8129-117">[Azure IoT 中心](https://azure.microsoft.com/services/iot-hub/)是 Azure 云服务的产品/服务可靠且安全设备到云和云到设备消息传送，可扩展到数百万台设备。</span><span class="sxs-lookup"><span data-stu-id="b8129-117">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/) is an Azure cloud service that offers reliable and secure device-to-cloud and cloud-to-device messaging that scales to millions of devices.</span></span> <span data-ttu-id="b8129-118">它提供可让你开始使用极少的工作量并根据其需求的增长进行扩展构成解决方案的简化编程模型。</span><span class="sxs-lookup"><span data-stu-id="b8129-118">It offers a streamlined programming model that lets you get started with minimum effort and scale up your solution as its needs grow.</span></span>

