---
title: 开始使用 Mdn 响应程序示例源
author: saraclay
ms.author: saclayt
ms.date: 02/26/2019
ms.topic: article
description: 了解如何开始使用 Mdn 响应程序示例源。
keywords: Windows 10 IoT Core，Mdn 响应程序示例源
ms.openlocfilehash: eacd22bf4d8a93948706e214fd48262c61c59a08
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510613"
---
# <a name="getting-started-with-mdns-responder-sample-source"></a>开始使用 Mdn 响应程序示例源

## <a name="getting-started"></a>即刻体验

1.  将项目编译*mDNSResponder*到 get mDNSResponder.exe，是一项服务。 将.exe 复制到目标计算机，然后注册该服务并运行。
2. Run “mDNSResponder.exe /?” 若要打印使用情况
3.  将项目编译*dnssd*，则会生成 dnssd.dll
4.  将项目编译*mDNSUWP*。 它是可与 dnssd.dll 并将生成其自己的 dll 和 winmd UWP 代理
5.  将项目编译*mDNSTest*，这是一个示例使用 mDNSUWP 的 UWP 应用，最终到 mDNSResponder 服务通信。
6.  此 UWP 应用依赖于 dnssd.dll 和 UWP broker （没有配置为将所有内容复制到 UWP appx 文件夹的脚本）
7.  部署/启动 mDNSTest、 设置的 ID 并单击注册，则响应代码应为 0 （成功）
8.  如果在同一时间运行的任何 Bonjour 浏览器，应列出新的 （虚设） 设备。

![Mdn 的注册](media/mDNS/mDNS1.png)

## <a name="resources"></a>资源

* 下载 Bonjour 兼容 Mdn （示例源） 响应程序的 IoT Windows[此处](https://go.microsoft.com/fwlink/?linkid=2077676)。

