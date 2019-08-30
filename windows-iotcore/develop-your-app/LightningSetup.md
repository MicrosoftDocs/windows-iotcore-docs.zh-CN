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
# <a name="lightning-setup-guide"></a>Lightning 设置指南

本指南将指导你完成将默认控制器驱动程序更改为 Windows IoT Core 设备上的闪电直内存访问映射 (DMAP) 驱动程序所需的步骤。 此操作将允许在该设备上使用支持 Lightning 的应用程序。

## <a name="change-the-default-controller-driver"></a>更改默认控制器驱动程序

我们需要打开 Windows 设备门户。

1. 通过使用 Windows 10 IoT 核心版仪表板应用程序或将开发板接入监视器来查找设备的 IP 地址。

2. 在本地计算机上, 通过在 web 浏览器中输入以下地址 http://{BoardIPAddress}: 8080/来打开 Windows 设备门户网页。
   ![Windows 设备门户](../media/LightningSetup/dmap1.png)

3. Windows Devices Portal 页面应该会要求你提供凭据。 默认的用户名是 `Administrator`，密码是 `p@ssw0rd`。请注意，输入用户名和密码后，该门户将询问你是否需要更改密码。 更改此方法始终是一个好办法。
   ![Windows 设备门户凭据](../media/LightningSetup/dmap2.png)

4. 单击导航菜单中的 "设备", 打开 "设备![页面设备" 页面](../media/LightningSetup/dmap3.png)

5. “设备”页面列出了可用的控制器驱动程序。 默认情况下，收件箱驱动程序会设置为当前驱动程序。

6. 从下拉菜单中选择 "直接内存映射驱动程序", 然后单击 "更新驱动程序" 按钮, 切换到闪电驱动程序<br/>
   ![选择直接内存映射驱动程序](../media/LightningSetup/dmap4.png)

7. 请等待, 直至页面通知您驱动程序安装完成的时间。
   ![驱动程序安装完成](../media/LightningSetup/dmap5.png)

8. 如果需要重新启动，该页面也将通知你。 你可以通过使用页面顶部的“重新启动”按钮来重新启动。

9. 现在你可以随时创建和使用可利用 Lightning 直接内存映射的驱动程序的应用程序。
