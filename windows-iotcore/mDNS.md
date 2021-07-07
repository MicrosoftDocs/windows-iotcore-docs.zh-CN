---
title: mDNS 响应程序示例源代码入门
ms.date: 02/26/2019
ms.topic: article
description: 了解如何开始使用面向 Windows IoT 的 mDNS 响应程序。 需要下载与 Bonjour 兼容的示例源。
keywords: Windows 10 IoT 核心版, mDNS 响应程序示例源代码
ms.openlocfilehash: 4b87a20f30de2fcce1ac3bb4038ed4ec7360ea65
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228663"
---
# <a name="getting-started-with-mdns-responder-sample-source"></a><span data-ttu-id="62be7-105">mDNS 响应程序示例源代码入门</span><span class="sxs-lookup"><span data-stu-id="62be7-105">Getting Started with mDNS Responder Sample Source</span></span>

## <a name="getting-started"></a><span data-ttu-id="62be7-106">入门</span><span class="sxs-lookup"><span data-stu-id="62be7-106">Getting started</span></span>

1.  <span data-ttu-id="62be7-107">编译项目 *mDNSResponder* 以获取 mDNSResponder.exe，这是一项服务。</span><span class="sxs-lookup"><span data-stu-id="62be7-107">Compile the project *mDNSResponder* to get mDNSResponder.exe, which is a service.</span></span> <span data-ttu-id="62be7-108">将 .exe 复制到目标计算机，然后注册并运行该服务。</span><span class="sxs-lookup"><span data-stu-id="62be7-108">Copy the .exe to the target machine then register the service and run.</span></span>
2. <span data-ttu-id="62be7-109">运行“mDNSResponder.exe /?”</span><span class="sxs-lookup"><span data-stu-id="62be7-109">Run “mDNSResponder.exe /?”</span></span> <span data-ttu-id="62be7-110">以列显用法</span><span class="sxs-lookup"><span data-stu-id="62be7-110">to print the usage</span></span>
3.  <span data-ttu-id="62be7-111">编译项目 *dnssd*，用于生成 dnssd.dll</span><span class="sxs-lookup"><span data-stu-id="62be7-111">Compile the project *dnssd*, it would generate dnssd.dll</span></span>
4.  <span data-ttu-id="62be7-112">编译项目 *mDNSUWP*。</span><span class="sxs-lookup"><span data-stu-id="62be7-112">Compile the project *mDNSUWP*.</span></span> <span data-ttu-id="62be7-113">这是一个 UWP 代理，它可以与 dnssd.dll 通信并生成自己的 dll 和 winmd</span><span class="sxs-lookup"><span data-stu-id="62be7-113">It’s a UWP broker that talks to dnssd.dll and will generate its own dll and winmd</span></span>
5.  <span data-ttu-id="62be7-114">编译项目 *mDNSTest*，这是一个示例 UWP 应用，可以使用 mDNSUWP 并最终与 mDNSResponder 服务通信。</span><span class="sxs-lookup"><span data-stu-id="62be7-114">Compile the project *mDNSTest*, which is a sample UWP app to consume mDNSUWP and eventually talks into mDNSResponder service.</span></span>
6.  <span data-ttu-id="62be7-115">此 UWP 应用依赖于 dnssd.dll 和 UWP 代理（已配置可将所有内容复制到 UWP 的 appx 文件夹中的脚本）</span><span class="sxs-lookup"><span data-stu-id="62be7-115">This UWP app depends on both dnssd.dll and the UWP broker (there is script configured to copy everything into the UWP appx folder)</span></span>
7.  <span data-ttu-id="62be7-116">部署/启动 mDNSTest，设置一个 ID 并单击“注册”，响应代码应该为“0 (成功)”</span><span class="sxs-lookup"><span data-stu-id="62be7-116">Deploy/launch mDNSTest, set an ID and click Register, the respond code should be 0 (SUCCESS)</span></span>
8.  <span data-ttu-id="62be7-117">如果同时运行任何 Bonjour 浏览器，则会列出新的（虚设）设备。</span><span class="sxs-lookup"><span data-stu-id="62be7-117">If you run any Bonjour Browser at the same time, the new (fake) device should be listed.</span></span>

![针对 mDNS 的注册](media/mDNS/mDNS1.png)

## <a name="resources"></a><span data-ttu-id="62be7-119">资源</span><span class="sxs-lookup"><span data-stu-id="62be7-119">Resources</span></span>

* <span data-ttu-id="62be7-120">在[此处](https://go.microsoft.com/fwlink/?linkid=2077676)下载适用于 Windows IoT 且兼容 Bonjour 的 mDNS 响应程序（示例源代码）。</span><span class="sxs-lookup"><span data-stu-id="62be7-120">Download the Bonjour-compatible mDNS Responder for Windows IoT (sample source) [here](https://go.microsoft.com/fwlink/?linkid=2077676).</span></span>

