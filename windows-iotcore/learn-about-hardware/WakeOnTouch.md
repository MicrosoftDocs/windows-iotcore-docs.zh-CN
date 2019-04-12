---
title: 唤醒触摸
author: jordanrh1
ms.author: jordanrh
ms.date: 09/17/2018
ms.topic: article
description: 配置用于唤醒触摸设备
keywords: windows iot、 屏幕、 休眠、 唤醒、 触摸、 待机、 power
ms.custom: RS5
ms.openlocfilehash: 7c0fc9613f1b1ed45fb8d69a18d82b034eb366fb
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510799"
---
# <a name="configure-your-device-to-wake-on-touch"></a>配置用于唤醒触摸设备

在某些情况下，你想在不使用时关闭和开启快速时用户涉及在触摸屏设备的屏幕。 本文档介绍如何配置你的设备以实现此方案。

## <a name="setting-a-video-idle-timeout"></a>设置视频的空闲超时

你可以配置屏幕来设置视频的空闲超时将处于非活动状态一段时间后关闭。 当用户不与指定的时间长度的设备交互时，屏幕将关闭。 这将使设备可以通过关闭组件显示相关的输入低功耗状态。

```
    powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setdcvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setactive SCHEME_CURRENT
```

有关详细信息，请参阅[显示器空闲超时](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout)并[显示，进入睡眠状态，并进入休眠状态的空闲计时器](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers)。

## <a name="disabling-modern-standby"></a>禁用现代待机状态

AoAC 在系统上 （其中包括所有 ARM 系统），系统会自动进入[现代待机](/windows-hardware/design/device-experiences/modern-standby)时，显示器变。 现代的备用系统时，只能由特定输入唤醒。 这不是详尽的列表，但这些输入包括按电源按钮，打开在便携式计算机，合上的盖子或单击鼠标。 触摸屏幕将唤醒从待机现代设备。 如果你想通过触摸唤醒设备，必须配置该设备无法进入现代待机状态。 若要禁用现代待机状态，请设置以下注册表项和重新启动。

```
    reg add HKLM\System\CurrentControlSet\Control\Power /v PlatformAoAcOverride /t REG_DWORD /d 0
```
    
当系统处于空闲状态时，禁用现代待机状态可能会影响功率消耗。 应采用现代的备用模式启用和禁用之前做出的决策，若要禁用现代待机状态来测量系统的功率消耗。

现代备用操作主机是一种软件机制，尝试尽可能多地，从而允许硬件进入低功耗状态无人参与的系统活动。 从理论上讲，具有现代备用已禁用的足够静默设备可以实现为在现代备用设备相同的低功率消耗。 请务必最大程度减少后台活动，包括软件计时器和定期任务，如果禁用了现代待机状态。
