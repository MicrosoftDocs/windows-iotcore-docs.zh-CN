---
title: mDNS 响应程序示例源代码入门
ms.date: 02/26/2019
ms.topic: article
description: 了解如何开始使用面向 Windows IoT 的 mDNS 响应程序。 需要下载与 Bonjour 兼容的示例源。
keywords: Windows 10 IoT 核心版, mDNS 响应程序示例源代码
ms.openlocfilehash: ea6be19041b82ab4b496728d0ffb4a169c262eb9
ms.sourcegitcommit: 05278f1a522ed498900ce15b98bdd4389b5dde55
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88081352"
---
# <a name="getting-started-with-mdns-responder-sample-source"></a>mDNS 响应程序示例源代码入门

## <a name="getting-started"></a>入门

1.  编译项目 *mDNSResponder* 以获取 mDNSResponder.exe，这是一项服务。 将 .exe 复制到目标计算机，然后注册并运行该服务。
2. 运行“mDNSResponder.exe /?” 以列显用法
3.  编译项目 *dnssd*，用于生成 dnssd.dll
4.  编译项目 *mDNSUWP*。 这是一个 UWP 代理，它可以与 dnssd.dll 通信并生成自己的 dll 和 winmd
5.  编译项目 *mDNSTest*，这是一个示例 UWP 应用，可以使用 mDNSUWP 并最终与 mDNSResponder 服务通信。
6.  此 UWP 应用依赖于 dnssd.dll 和 UWP 代理（已配置可将所有内容复制到 UWP 的 appx 文件夹中的脚本）
7.  部署/启动 mDNSTest，设置一个 ID 并单击“注册”，响应代码应该为“0 (成功)”
8.  如果同时运行任何 Bonjour 浏览器，则会列出新的（虚设）设备。

![针对 mDNS 的注册](media/mDNS/mDNS1.png)

## <a name="resources"></a>资源

* 在[此处](https://go.microsoft.com/fwlink/?linkid=2077676)下载适用于 Windows IoT 且兼容 Bonjour 的 mDNS 响应程序（示例源代码）。

