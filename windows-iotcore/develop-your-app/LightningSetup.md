---
title: Lightning 设置指南
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解如何在设备上将默认控制器驱动程序更改为闪电 DMAP 驱动程序。
keywords: windows iot, 闪电, 安装, 闪电安装, Windows 设备门户
ms.openlocfilehash: 0997638b50f89fd42262df437623bd55380fbb5b
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167827"
---
# <a name="lightning-setup-guide"></a><span data-ttu-id="5d4b6-104">Lightning 设置指南</span><span class="sxs-lookup"><span data-stu-id="5d4b6-104">Lightning Setup Guide</span></span>

<span data-ttu-id="5d4b6-105">本指南将指导你完成将默认控制器驱动程序更改为 Windows IoT Core 设备上的闪电直内存访问映射 (DMAP) 驱动程序所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="5d4b6-105">This guide will walk you through the steps needed to change the default controller driver to the Lightning direct memory access mapped (DMAP) driver on a Windows IoT Core device.</span></span> <span data-ttu-id="5d4b6-106">此操作将允许在该设备上使用支持 Lightning 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="5d4b6-106">This will allow the use of Lightning-enabled applications on that device.</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="5d4b6-107">更改默认控制器驱动程序</span><span class="sxs-lookup"><span data-stu-id="5d4b6-107">Change the Default Controller Driver</span></span>

<span data-ttu-id="5d4b6-108">我们需要打开 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="5d4b6-108">We will want to open the Windows Device Portal.</span></span>

1. <span data-ttu-id="5d4b6-109">通过使用 Windows 10 IoT 核心版仪表板应用程序或将开发板接入监视器来查找设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="5d4b6-109">Locate the IP address of your device, either by using the Windows 10 IoT Core Dashboard application or hooking up your board to a monitor.</span></span>

2. <span data-ttu-id="5d4b6-110">在本地计算机上, 通过在 web 浏览器中输入以下地址 http://{BoardIPAddress}: 8080/来打开 Windows 设备门户网页。</span><span class="sxs-lookup"><span data-stu-id="5d4b6-110">From your local machine, open the Windows Devices Portal web page by entering this address http://{BoardIPAddress}:8080/ in your web browser.</span></span>
   <span data-ttu-id="5d4b6-111">![Windows 设备门户](../media/LightningSetup/dmap1.png)</span><span class="sxs-lookup"><span data-stu-id="5d4b6-111">![Windows Devices Portal](../media/LightningSetup/dmap1.png)</span></span>

3. <span data-ttu-id="5d4b6-112">Windows Devices Portal 页面应该会要求你提供凭据。</span><span class="sxs-lookup"><span data-stu-id="5d4b6-112">The Windows Devices Portal Page should ask you for your credentials.</span></span> <span data-ttu-id="5d4b6-113">默认的用户名是 `Administrator`，密码是 `p@ssw0rd`。请注意，输入用户名和密码后，该门户将询问你是否需要更改密码。</span><span class="sxs-lookup"><span data-stu-id="5d4b6-113">The default username is `Administrator` and password is `p@ssw0rd` Note, after entering the username and password, the Portal will ask you if you need to change the password.</span></span> <span data-ttu-id="5d4b6-114">更改此方法始终是一个好办法。</span><span class="sxs-lookup"><span data-stu-id="5d4b6-114">It's always a good practice to change it.</span></span>
   <span data-ttu-id="5d4b6-115">![Windows 设备门户凭据](../media/LightningSetup/dmap2.png)</span><span class="sxs-lookup"><span data-stu-id="5d4b6-115">![Windows Devices Portal Credentials](../media/LightningSetup/dmap2.png)</span></span>

4. <span data-ttu-id="5d4b6-116">单击导航菜单中的 "设备", 打开 "设备![页面设备" 页面](../media/LightningSetup/dmap3.png)</span><span class="sxs-lookup"><span data-stu-id="5d4b6-116">Click on Devices in the navigation menu to open the Devices page ![Devices Page](../media/LightningSetup/dmap3.png)</span></span>

5. <span data-ttu-id="5d4b6-117">“设备”页面列出了可用的控制器驱动程序。</span><span class="sxs-lookup"><span data-stu-id="5d4b6-117">The Devices page lists the available Controller drivers.</span></span> <span data-ttu-id="5d4b6-118">默认情况下，收件箱驱动程序会设置为当前驱动程序。</span><span class="sxs-lookup"><span data-stu-id="5d4b6-118">By default, the Inbox Driver is set to current.</span></span>

6. <span data-ttu-id="5d4b6-119">从下拉菜单中选择 "直接内存映射驱动程序", 然后单击 "更新驱动程序" 按钮, 切换到闪电驱动程序</span><span class="sxs-lookup"><span data-stu-id="5d4b6-119">Switch to the Lightning driver by choosing the Direct Memory Mapped Driver from the drop down menu and click the Update Driver Button</span></span><br/>
   <span data-ttu-id="5d4b6-120">![选择直接内存映射驱动程序](../media/LightningSetup/dmap4.png)</span><span class="sxs-lookup"><span data-stu-id="5d4b6-120">![Select Direct Memory Mapped Driver](../media/LightningSetup/dmap4.png)</span></span>

7. <span data-ttu-id="5d4b6-121">请等待, 直至页面通知您驱动程序安装完成的时间。</span><span class="sxs-lookup"><span data-stu-id="5d4b6-121">Please wait until the page lets you know when the driver installation is complete.</span></span>
   <span data-ttu-id="5d4b6-122">![驱动程序安装完成](../media/LightningSetup/dmap5.png)</span><span class="sxs-lookup"><span data-stu-id="5d4b6-122">![Driver Installation Complete](../media/LightningSetup/dmap5.png)</span></span>

8. <span data-ttu-id="5d4b6-123">如果需要重新启动，该页面也将通知你。</span><span class="sxs-lookup"><span data-stu-id="5d4b6-123">If a reboot is required, the page will let you know as well.</span></span> <span data-ttu-id="5d4b6-124">你可以通过使用页面顶部的“重新启动”按钮来重新启动。</span><span class="sxs-lookup"><span data-stu-id="5d4b6-124">You can reboot by using the Reboot button at the top of the page.</span></span>

9. <span data-ttu-id="5d4b6-125">现在你可以随时创建和使用可利用 Lightning 直接内存映射的驱动程序的应用程序。</span><span class="sxs-lookup"><span data-stu-id="5d4b6-125">Now you're ready to create and use applications that make use of the Lightning Direct Memory Mapped driver.</span></span>
