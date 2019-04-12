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
# <a name="lightning-setup-guide"></a>Lightning 设置指南

本指南将引导你完成将默认控制器驱动程序更改为 Windows IoT Core 设备上的闪电形直接内存访问映射 (DMAP) 驱动程序所需的步骤。 此操作将允许在该设备上使用支持 Lightning 的应用程序。

## <a name="change-the-default-controller-driver"></a>更改默认控制器驱动程序

我们想要打开 Windows Device Portal。

1. 通过使用 Windows 10 IoT 核心版仪表板应用程序或将开发板接入监视器来查找设备的 IP 地址。

2. 在本地计算机上，打开 web 浏览器中输入此地址 http://{BoardIPAddress}:8080/ Windows 设备门户网页。
   ![Windows Devices Portal](../media/LightningSetup/dmap1.png)

3. Windows Devices Portal 页面应该会要求你提供凭据。 默认的用户名是 `Administrator`，密码是 `p@ssw0rd`。请注意，输入用户名和密码后，该门户将询问你是否需要更改密码。 它始终是一个好办法对其进行更改。
   ![Windows Devices Portal 凭据](../media/LightningSetup/dmap2.png)

4. 单击以打开设备页的导航菜单中的设备![设备页](../media/LightningSetup/dmap3.png)

5. “设备”页面列出了可用的控制器驱动程序。 默认情况下，收件箱驱动程序会设置为当前驱动程序。

6. 从下拉列表菜单中选择直接内存映射驱动程序切换到闪电驱动程序，然后单击更新驱动程序按钮<br/>
   ![选择直接内存映射的驱动程序](../media/LightningSetup/dmap4.png)

7. 请页告知你驱动程序安装完成后，等待。
   ![驱动程序安装完成](../media/LightningSetup/dmap5.png)

8. 如果需要重新启动，该页面也将通知你。 你可以通过使用页面顶部的“重新启动”按钮来重新启动。

9. 现在你可以随时创建和使用可利用 Lightning 直接内存映射的驱动程序的应用程序。
