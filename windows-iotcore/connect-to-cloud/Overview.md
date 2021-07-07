---
title: 云上的 IoT 概述
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解使用云通过云进行的消息传送、安全和设备Azure IoT。
keywords: windows iot， 云， Azure， Azure IoT 中心， 消息传送， UWP， 通用 Windows 平台
ms.openlocfilehash: dbac576e77aa00e40ed5d53983f1761b543855b3
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230064"
---
# <a name="overview-of-iot-on-the-cloud"></a>云上的 IoT 概述

此物联网构建在云计算上。 与云通信以及从数据派生见解的能力是任何 IoT 项目的重要组成部分。

## <a name="messaging"></a>消息传递

通常，IoT 设备通过发送和接收消息与云通信或相互通信。 从设备发送到云的消息的有效负载可以小到传感器中的值，也可以与视频文件一样大。 云到设备消息通常是指示设备执行操作的命令。


消息传递通信模式的复杂性各不相同，从简单的单向消息传递到更复杂的协议（例如请求-响应或事务协议，如两阶段提交）。

## <a name="security"></a>安全性

安全性是 IoT 的基本部分。 对于每个消息，我们必须确保该消息来自受 (设备) ，并且未被篡改。 数据可以包含必须加密的信息。

## <a name="azure-iot-hub"></a>Azure IoT 中心

[Azure IoT中心](https://azure.microsoft.com/services/iot-hub/)是一项 Azure 云服务，它提供可靠且安全的设备到云和云到设备的消息传送，可扩展到数百万台设备。 它提供一个简化的编程模型，让你能够尽可能减少工作量，并随着解决方案需求的增长来扩展解决方案。

