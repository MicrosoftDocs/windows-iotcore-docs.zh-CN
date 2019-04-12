---
title: Lightning 设置指南
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解如何将默认控制器驱动程序更改为设备上的闪电 DMAP 驱动程序。
keywords: windows iot、 快如闪电、 安装、 快如闪电安装过程中，Windows Device Portal
ms.openlocfilehash: 0997638b50f89fd42262df437623bd55380fbb5b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510843"
---
# <a name="lightning-setup-guide"></a><span data-ttu-id="f4c42-104">Lightning 设置指南</span><span class="sxs-lookup"><span data-stu-id="f4c42-104">Lightning Setup Guide</span></span>

<span data-ttu-id="f4c42-105">本指南将引导你完成将默认控制器驱动程序更改为 Windows IoT Core 设备上的闪电形直接内存访问映射 (DMAP) 驱动程序所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="f4c42-105">This guide will walk you through the steps needed to change the default controller driver to the Lightning direct memory access mapped (DMAP) driver on a Windows IoT Core device.</span></span> <span data-ttu-id="f4c42-106">此操作将允许在该设备上使用支持 Lightning 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="f4c42-106">This will allow the use of Lightning-enabled applications on that device.</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="f4c42-107">更改默认控制器驱动程序</span><span class="sxs-lookup"><span data-stu-id="f4c42-107">Change the Default Controller Driver</span></span>

<span data-ttu-id="f4c42-108">我们想要打开 Windows Device Portal。</span><span class="sxs-lookup"><span data-stu-id="f4c42-108">We will want to open the Windows Device Portal.</span></span>

1. <span data-ttu-id="f4c42-109">通过使用 Windows 10 IoT 核心版仪表板应用程序或将开发板接入监视器来查找设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="f4c42-109">Locate the IP address of your device, either by using the Windows 10 IoT Core Dashboard application or hooking up your board to a monitor.</span></span>

2. <span data-ttu-id="f4c42-110">在本地计算机上，打开 web 浏览器中输入此地址 http://{BoardIPAddress}:8080/ Windows 设备门户网页。</span><span class="sxs-lookup"><span data-stu-id="f4c42-110">From your local machine, open the Windows Devices Portal web page by entering this address http://{BoardIPAddress}:8080/ in your web browser.</span></span>
   ![Windows Devices Portal](../media/LightningSetup/dmap1.png)

3. <span data-ttu-id="f4c42-112">Windows Devices Portal 页面应该会要求你提供凭据。</span><span class="sxs-lookup"><span data-stu-id="f4c42-112">The Windows Devices Portal Page should ask you for your credentials.</span></span> <span data-ttu-id="f4c42-113">默认的用户名是 `Administrator`，密码是 `p@ssw0rd`。请注意，输入用户名和密码后，该门户将询问你是否需要更改密码。</span><span class="sxs-lookup"><span data-stu-id="f4c42-113">The default username is `Administrator` and password is `p@ssw0rd` Note, after entering the username and password, the Portal will ask you if you need to change the password.</span></span> <span data-ttu-id="f4c42-114">它始终是一个好办法对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="f4c42-114">It's always a good practice to change it.</span></span>
   ![Windows Devices Portal 凭据](../media/LightningSetup/dmap2.png)

4. <span data-ttu-id="f4c42-116">单击以打开设备页的导航菜单中的设备![设备页](../media/LightningSetup/dmap3.png)</span><span class="sxs-lookup"><span data-stu-id="f4c42-116">Click on Devices in the navigation menu to open the Devices page ![Devices Page](../media/LightningSetup/dmap3.png)</span></span>

5. <span data-ttu-id="f4c42-117">“设备”页面列出了可用的控制器驱动程序。</span><span class="sxs-lookup"><span data-stu-id="f4c42-117">The Devices page lists the available Controller drivers.</span></span> <span data-ttu-id="f4c42-118">默认情况下，收件箱驱动程序会设置为当前驱动程序。</span><span class="sxs-lookup"><span data-stu-id="f4c42-118">By default, the Inbox Driver is set to current.</span></span>

6. <span data-ttu-id="f4c42-119">从下拉列表菜单中选择直接内存映射驱动程序切换到闪电驱动程序，然后单击更新驱动程序按钮</span><span class="sxs-lookup"><span data-stu-id="f4c42-119">Switch to the Lightning driver by choosing the Direct Memory Mapped Driver from the drop down menu and click the Update Driver Button</span></span><br/>
   ![选择直接内存映射的驱动程序](../media/LightningSetup/dmap4.png)

7. <span data-ttu-id="f4c42-121">请页告知你驱动程序安装完成后，等待。</span><span class="sxs-lookup"><span data-stu-id="f4c42-121">Please wait until the page lets you know when the driver installation is complete.</span></span>
   ![驱动程序安装完成](../media/LightningSetup/dmap5.png)

8. <span data-ttu-id="f4c42-123">如果需要重新启动，该页面也将通知你。</span><span class="sxs-lookup"><span data-stu-id="f4c42-123">If a reboot is required, the page will let you know as well.</span></span> <span data-ttu-id="f4c42-124">你可以通过使用页面顶部的“重新启动”按钮来重新启动。</span><span class="sxs-lookup"><span data-stu-id="f4c42-124">You can reboot by using the Reboot button at the top of the page.</span></span>

9. <span data-ttu-id="f4c42-125">现在你可以随时创建和使用可利用 Lightning 直接内存映射的驱动程序的应用程序。</span><span class="sxs-lookup"><span data-stu-id="f4c42-125">Now you're ready to create and use applications that make use of the Lightning Direct Memory Mapped driver.</span></span>
