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
# <a name="overview-of-iot-on-the-cloud"></a>在云上 IoT 的概述

物联网基于云计算。 与云通信和从数据获取见解的能力是必不可少的组成部分任何 IoT 项目。

## <a name="messaging"></a>消息

通常情况下，IoT 设备与云或相互通信的发送和接收消息。 从设备发送到云的消息的负载可以为最小可为从传感器和视频文件一样大的值。 云到设备的消息通常是一个命令，指示设备执行操作。


在复杂性范围从简单的单向消息传送到更复杂的协议，如请求-响应或如两阶段提交的事务协议不同消息传递通信模式。

## <a name="security"></a>安全性

安全性是必不可少的组成部分 IoT。 对于每个消息中，我们必须确保它来自 （或接收的） 受信任的设备以及未篡改。 数据可能包含必须加密的信息。

## <a name="azure-iot-hub"></a>Azure IoT 中心

[Azure IoT 中心](https://azure.microsoft.com/services/iot-hub/)是 Azure 云服务的产品/服务可靠且安全设备到云和云到设备消息传送，可扩展到数百万台设备。 它提供可让你开始使用极少的工作量并根据其需求的增长进行扩展构成解决方案的简化编程模型。

