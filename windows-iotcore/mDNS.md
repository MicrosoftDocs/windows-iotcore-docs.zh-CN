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
# <a name="getting-started-with-mdns-responder-sample-source"></a><span data-ttu-id="13894-104">开始使用 Mdn 响应程序示例源</span><span class="sxs-lookup"><span data-stu-id="13894-104">Getting Started with mDNS Responder Sample Source</span></span>

## <a name="getting-started"></a><span data-ttu-id="13894-105">即刻体验</span><span class="sxs-lookup"><span data-stu-id="13894-105">Getting started</span></span>

1.  <span data-ttu-id="13894-106">将项目编译*mDNSResponder*到 get mDNSResponder.exe，是一项服务。</span><span class="sxs-lookup"><span data-stu-id="13894-106">Compile the project *mDNSResponder* to get mDNSResponder.exe, which is a service.</span></span> <span data-ttu-id="13894-107">将.exe 复制到目标计算机，然后注册该服务并运行。</span><span class="sxs-lookup"><span data-stu-id="13894-107">Copy the .exe to the target machine then register the service and run.</span></span>
2. <span data-ttu-id="13894-108">Run “mDNSResponder.exe /?”</span><span class="sxs-lookup"><span data-stu-id="13894-108">Run “mDNSResponder.exe /?”</span></span> <span data-ttu-id="13894-109">若要打印使用情况</span><span class="sxs-lookup"><span data-stu-id="13894-109">to print the usage</span></span>
3.  <span data-ttu-id="13894-110">将项目编译*dnssd*，则会生成 dnssd.dll</span><span class="sxs-lookup"><span data-stu-id="13894-110">Compile the project *dnssd*, it would generate dnssd.dll</span></span>
4.  <span data-ttu-id="13894-111">将项目编译*mDNSUWP*。</span><span class="sxs-lookup"><span data-stu-id="13894-111">Compile the project *mDNSUWP*.</span></span> <span data-ttu-id="13894-112">它是可与 dnssd.dll 并将生成其自己的 dll 和 winmd UWP 代理</span><span class="sxs-lookup"><span data-stu-id="13894-112">It’s a UWP broker that talks to dnssd.dll and will generate its own dll and winmd</span></span>
5.  <span data-ttu-id="13894-113">将项目编译*mDNSTest*，这是一个示例使用 mDNSUWP 的 UWP 应用，最终到 mDNSResponder 服务通信。</span><span class="sxs-lookup"><span data-stu-id="13894-113">Compile the project *mDNSTest*, which is a sample UWP app to consume mDNSUWP and eventually talks into mDNSResponder service.</span></span>
6.  <span data-ttu-id="13894-114">此 UWP 应用依赖于 dnssd.dll 和 UWP broker （没有配置为将所有内容复制到 UWP appx 文件夹的脚本）</span><span class="sxs-lookup"><span data-stu-id="13894-114">This UWP app depends on both dnssd.dll and the UWP broker (there is script configured to copy everything into the UWP appx folder)</span></span>
7.  <span data-ttu-id="13894-115">部署/启动 mDNSTest、 设置的 ID 并单击注册，则响应代码应为 0 （成功）</span><span class="sxs-lookup"><span data-stu-id="13894-115">Deploy/launch mDNSTest, set an ID and click Register, the respond code should be 0 (SUCCESS)</span></span>
8.  <span data-ttu-id="13894-116">如果在同一时间运行的任何 Bonjour 浏览器，应列出新的 （虚设） 设备。</span><span class="sxs-lookup"><span data-stu-id="13894-116">If you run any Bonjour Browser at the same time, the new (fake) device should be listed.</span></span>

![Mdn 的注册](media/mDNS/mDNS1.png)

## <a name="resources"></a><span data-ttu-id="13894-118">资源</span><span class="sxs-lookup"><span data-stu-id="13894-118">Resources</span></span>

* <span data-ttu-id="13894-119">下载 Bonjour 兼容 Mdn （示例源） 响应程序的 IoT Windows[此处](https://go.microsoft.com/fwlink/?linkid=2077676)。</span><span class="sxs-lookup"><span data-stu-id="13894-119">Download the Bonjour-compatible mDNS Responder for Windows IoT (sample source) [here](https://go.microsoft.com/fwlink/?linkid=2077676).</span></span>

