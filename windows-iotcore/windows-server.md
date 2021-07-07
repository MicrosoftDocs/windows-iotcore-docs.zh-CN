---
title: Windows Server IoT 2019 概述
ms.date: 02/07/2019
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解 Windows Server IoT 2019 是什么，以及可以用它执行什么操作。
keywords: Windows Server IoT 2019, 企业可管理性, Windows 生态系统, IoT
ms.openlocfilehash: 1c3ba30093c93f77866146e747d0b6b053364c1b
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230744"
---
# <a name="an-overview-of-windows-server-iot-2019"></a><span data-ttu-id="b7f0b-104">Windows Server IoT 2019 概述</span><span class="sxs-lookup"><span data-stu-id="b7f0b-104">An overview of Windows Server IoT 2019</span></span>

> [!NOTE]
> <span data-ttu-id="b7f0b-105">Windows 容器受到支持，能够以商业方式部署在 Windows Server、Windows IoT Server、Windows IoT Enterprise 和 Windows IoT Core 上。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-105">Windows Containers are supported for commercial deployments on Windows Server, Windows IoT Server, Windows IoT Enterprise and Windows IoT Core.</span></span>  <span data-ttu-id="b7f0b-106">从 Windows 10 月更新 2018（版本 17763）开始，Windows 容器只能与 Windows 企业版和专业版配合使用，用于开发/测试目的。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-106">As of Windows October Update 2018 (Build 17763), Windows Containers can only be used with Windows Enterprise and Professional for dev/test purposes.</span></span>

## <a name="what-is-windows-server-iot-2019"></a><span data-ttu-id="b7f0b-107">什么是 Windows Server IoT 2019？</span><span class="sxs-lookup"><span data-stu-id="b7f0b-107">What is Windows Server IoT 2019?</span></span>
<span data-ttu-id="b7f0b-108">Windows Server IoT 2019 是完整版本的 Windows Server 2019，可以为 IoT 解决方案提供企业可管理性和安全性。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-108">Windows Server IoT 2019 is a full version of Windows Server 2019 that delivers enterprise manageability and security to IoT solutions.</span></span> <span data-ttu-id="b7f0b-109">Windows Server IoT 2019 享有全球 Windows 生态系统的所有权益。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-109">Windows Server IoT 2019 shares all the benefits of the world-wide Windows ecosystem.</span></span> <span data-ttu-id="b7f0b-110">它是 Windows Server 2019 的二进制等效文件，因此你可以使用类似的开发和管理工具，就像在常规用途服务器上使用一样。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-110">It is a binary equivalent to Windows Server 2019, so you can use the same familiar development and management tools that you use on your general-purpose servers.</span></span> <span data-ttu-id="b7f0b-111">但是，在许可和分发方面，常规用途版本和 IoT 版本存在差异。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-111">However, when it comes to licensing and distribution, the general-purpose version and IoT versions differ.</span></span>  <span data-ttu-id="b7f0b-112">Windows Server IoT 2019 只能通过 OEM 渠道获得许可，其用户享有特殊的专用权利。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-112">Windows Server IoT 2019 is only licensed through the OEM channel under special dedicated use rights.</span></span>

## <a name="fixed-purpose-devices"></a><span data-ttu-id="b7f0b-113">固定用途设备</span><span class="sxs-lookup"><span data-stu-id="b7f0b-113">Fixed purpose devices</span></span> 

> [!TIP]
> <span data-ttu-id="b7f0b-114">若要完全了解所有 Windows Server IoT 2019 使用方案，请查看许可协议。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-114">See your licensing agreement for complete guidance on all Windows Server IoT 2019 usage scenarios.</span></span> <span data-ttu-id="b7f0b-115">如果没有此许可协议，请要求你的 OEM 提供商业协议。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-115">If you do not have this licensing agreement, ask the OEM you work with for the commercial agreement.</span></span>

<span data-ttu-id="b7f0b-116">Windows Server 作为可供世界范围的小型企业使用的服务器操作系统享有盛誉。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-116">Windows Server is well known as the server operating system used by small businesses and enterprises world-wide.</span></span> <span data-ttu-id="b7f0b-117">其不太为人所知的是，多年来，Windows Server 还在零售、制造、医疗保健等领域为许多专用解决方案提供支持。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-117">What is less well known is that for years, Windows Server has also powered many dedicated solutions in retail, manufacturing, healthcare, and more.</span></span> <span data-ttu-id="b7f0b-118">Windows Server IoT 2019 允许你构建固定用途的解决方案，在许可协议中提供特定的许可和限制。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-118">Windows Server IoT 2019 allows you to build fixed purpose solutions with specific allowances and restrictions in the license agreement.</span></span>

## <a name="long-term-servicing-channel-ltsc"></a><span data-ttu-id="b7f0b-119">长期服务频道 (LTSC)</span><span class="sxs-lookup"><span data-stu-id="b7f0b-119">Long-term Servicing Channel (LTSC)</span></span>

<span data-ttu-id="b7f0b-120">这是你已熟悉的版本模型（以前称为“Long-Term Servicing Branch”），其中 Windows Server 的全新主要版本每两到三年发布一次。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-120">This is the release model you’re already familiar with, formerly called the “Long-Term Servicing Branch”, where a new major version of Windows Server is released every two to three years.</span></span> <span data-ttu-id="b7f0b-121">用户有权享受五年的主流支持和五年的延长支持。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-121">Users are entitled to five years of mainstream support and five years of extended support.</span></span> <span data-ttu-id="b7f0b-122">该频道适用于需要更长时间服务选项和功能稳定性的系统。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-122">This channel is appropriate for systems that require a longer servicing option and functional stability.</span></span> <span data-ttu-id="b7f0b-123">新的半年频道版本不会影响 Windows Server IoT 2019 和 Windows Server 早期版本的部署工作。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-123">Deployments of Windows Server IoT 2019 and earlier versions of Windows Server will not be affected by the new Semi-Annual Channel releases.</span></span> <span data-ttu-id="b7f0b-124">长期服务频道将持续接受安全和非安全更新，但不会接受新特性和新功能。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-124">The Long-Term Servicing Channel will continue to receive security and non-security updates, but it will not receive the new features and functionality.</span></span>

* [<span data-ttu-id="b7f0b-125">了解有关 LTSC 的详细信息</span><span class="sxs-lookup"><span data-stu-id="b7f0b-125">Learn more about LTSC</span></span>](https://docs.microsoft.com/windows-server/get-started-19/servicing-channels-19#long-term-servicing-channel-ltsc)

## <a name="helpful-resources"></a><span data-ttu-id="b7f0b-126">有用资源</span><span class="sxs-lookup"><span data-stu-id="b7f0b-126">Helpful resources</span></span>
> [!NOTE]
> <span data-ttu-id="b7f0b-127">分发商或 Microsoft 代表可能会提供其他资源。</span><span class="sxs-lookup"><span data-stu-id="b7f0b-127">Additional resources may be available from your distributor or Microsoft representative.</span></span>

* [<span data-ttu-id="b7f0b-128">Windows Server 2019 文档</span><span class="sxs-lookup"><span data-stu-id="b7f0b-128">Windows Server 2019 documentation</span></span>](https://docs.microsoft.com/windows-server/index)
