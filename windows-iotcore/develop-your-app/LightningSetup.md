---
title: 闪电设置指南
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何在设备上将默认控制器驱动程序更改为闪电 DMAP 驱动程序。
keywords: windows iot，闪电，安装程序，闪电安装，Windows 设备门户
ms.openlocfilehash: 9bf44c8f1b12a29bac265b74fa7463c5ad77b365
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229023"
---
# <a name="lightning-setup-guide"></a>闪电设置指南

本指南将引导你完成将默认控制器驱动程序更改为 Windows IoT Core 设备上的 (DMAP) 驱动程序所需的步骤。 这将允许在该设备上使用启用了闪电的应用程序。

## <a name="change-the-default-controller-driver"></a>更改默认控制器驱动程序

我们需要打开 Windows 设备门户。

1. 使用 Windows 10 IoT 核心版仪表板应用程序，或将你的板挂钩到监视器，找到设备的 IP 地址。

2. 在本地计算机上，通过在 web 浏览器中输入此地址 http：//{BoardIPAddress}： 8080/来打开 "Windows 设备门户" 网页。
   ![Windows设备门户](../media/LightningSetup/dmap1.png)

3. "Windows 设备" 门户页应要求提供凭据。 默认用户名为， `Administrator` 密码为 `p@ssw0rd` 注意，输入用户名和密码后，门户会询问你是否需要更改密码。 更改此方法始终是一个好办法。
   ![Windows设备门户凭据](../media/LightningSetup/dmap2.png)

4. 单击导航菜单中的 "设备"，打开 "设备页面 ![ 设备" 页面](../media/LightningSetup/dmap3.png)

5. "设备" 页列出可用的控制器驱动程序。 默认情况下，收件箱驱动程序设置为 "当前"。

6. 从下拉菜单中选择 "直接内存映射驱动程序"，然后单击 "更新驱动程序" 按钮，切换到闪电驱动程序<br/>
   ![选择直接内存映射驱动程序](../media/LightningSetup/dmap4.png)

7. 请等待，直至页面通知您驱动程序安装完成的时间。
   ![驱动程序安装完成](../media/LightningSetup/dmap5.png)

8. 如果需要重新启动，则页面还会告诉你。 可以使用页面顶部的 "重新启动" 按钮重新启动。

9. 现在，你已准备好创建和使用应用程序，这些应用程序使用了闪电直接内存映射驱动程序。
