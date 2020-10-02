---
title: 触控唤醒
author: jordanrh1
ms.author: jordanrh
ms.date: 09/17/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 将设备配置为在触摸时唤醒，以便在不使用的情况下关闭设备，但在触摸屏幕时可以快速打开。 设置视频空闲超时。
keywords: windows iot，屏幕，睡眠，唤醒，touch，待机，电源
ms.custom: RS5
ms.openlocfilehash: 25a09499ebc2fa9e2242ff0cc21054061bdf1edc
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655633"
---
# <a name="configure-your-device-to-wake-on-touch"></a>将设备配置为在触摸时唤醒

在某些情况下，你希望设备的屏幕在不使用时关闭，并在用户接触触摸屏时快速打开。 本文档介绍如何将设备配置为实现此方案。

## <a name="setting-a-video-idle-timeout"></a>设置视频空闲超时

可以通过设置视频空闲超时，将屏幕配置为在一段非活动期后关闭。 当用户在指定的时间长度未与设备交互时，屏幕将会关闭。 这将允许设备通过关闭与显示器相关的组件来进入低功耗状态。

```powershell
    powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setdcvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setactive SCHEME_CURRENT
```

有关详细信息，请参阅 [显示空闲超时](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) 和 [显示、睡眠和休眠空闲计时器](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers)。

## <a name="disabling-modern-standby"></a>禁用新式备用

在 AoAC systems (包括) 的所有 ARM 系统）时，当显示器关闭时，系统将自动进入 [新式备用](/windows-hardware/design/device-experiences/modern-standby) 。 当系统处于新式备用状态时，它只能由某些输入唤醒。 这并不是一个详尽的列表，但这些输入包括按下电源按钮、打开便携式计算机的盖子或单击鼠标。 触摸屏幕将不会从新式备用设备唤醒设备。 如果希望设备通过触摸屏唤醒，则必须将设备配置为不进入新式备用。 若要禁用新式备用，请设置以下注册表项并重新启动。

```powershell
    reg add HKLM\System\CurrentControlSet\Control\Power /v PlatformAoAcOverride /t REG_DWORD /d 0
```
    
禁用新式备用会影响系统空闲时的功率消耗。 在决定禁用新式备用之前，应使用新式备用来度量系统的功耗并禁用。

新式备用是一种软件机制，它尝试尽可能地安静系统活动，从而允许硬件进入低功耗状态。 从理论上讲，具有新式备用禁用功能的足够安静的设备可实现与新式备用设备相同的低功耗。 如果禁用新式备用，则最大程度地减少后台活动（包括软件计时器和周期性任务）十分重要。
