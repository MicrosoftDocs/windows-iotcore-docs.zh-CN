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
# <a name="overview-of-iot-on-the-cloud"></a>云上的 IoT 概述

物联网基于云计算构建。 与云进行通信并从数据中获取见解的功能是任何 IoT 项目的重要组成部分。

## <a name="messaging"></a>消息

通常, IoT 设备通过发送和接收消息与云或彼此通信。 从设备发送到云的消息的有效负载可以小到传感器的值, 也可以像视频文件一样小。 云到设备的消息通常是指示设备执行操作的命令。


消息传递通信模式的复杂性不同于从简单单向消息传递到更复杂的协议, 如请求响应或事务协议 (如两阶段提交)。

## <a name="security"></a>安全性

安全是 IoT 的重要组成部分。 对于每条消息, 我们必须确保它来自受信任的设备 (或接收), 并且不会被篡改。 数据可以包含必须加密的信息。

## <a name="azure-iot-hub"></a>Azure IoT 中心

[Azure IoT 中心](https://azure.microsoft.com/services/iot-hub/)是一项 azure 云服务, 可提供可靠且安全的设备到云和云到设备的消息传送功能, 可扩展到数百万台设备。 它提供了一种简化的编程模型, 可让你快速入门, 并随着需求的增加而扩展解决方案。

