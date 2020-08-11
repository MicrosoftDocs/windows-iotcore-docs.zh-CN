---
title: 触控唤醒
author: jordanrh1
ms.author: jordanrh
ms.date: 09/17/2018
ms.topic: article
description: 将设备配置为在触摸时唤醒，以便在不使用的情况下关闭设备，但在触摸屏幕时可以快速打开。 设置视频空闲超时。
keywords: windows iot，屏幕，睡眠，唤醒，touch，待机，电源
ms.custom: RS5
ms.openlocfilehash: 1d57383d2ae8a3658de507648e6feb0c3ceeb521
ms.sourcegitcommit: 05278f1a522ed498900ce15b98bdd4389b5dde55
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88081302"
---
# <a name="configure-your-device-to-wake-on-touch"></a><span data-ttu-id="d00fb-105">将设备配置为在触摸时唤醒</span><span class="sxs-lookup"><span data-stu-id="d00fb-105">Configure your device to wake on touch</span></span>

<span data-ttu-id="d00fb-106">在某些情况下，你希望设备的屏幕在不使用时关闭，并在用户接触触摸屏时快速打开。</span><span class="sxs-lookup"><span data-stu-id="d00fb-106">In some scenarios, you want your device's screen to turn off while not in use and to turn on quickly when a user touches the touchscreen.</span></span> <span data-ttu-id="d00fb-107">本文档介绍如何将设备配置为实现此方案。</span><span class="sxs-lookup"><span data-stu-id="d00fb-107">This document describes how to configure your device to achieve this scenario.</span></span>

## <a name="setting-a-video-idle-timeout"></a><span data-ttu-id="d00fb-108">设置视频空闲超时</span><span class="sxs-lookup"><span data-stu-id="d00fb-108">Setting a video idle timeout</span></span>

<span data-ttu-id="d00fb-109">可以通过设置视频空闲超时，将屏幕配置为在一段非活动期后关闭。</span><span class="sxs-lookup"><span data-stu-id="d00fb-109">You can configure the screen to turn off after a period of inactivity by setting a video idle timeout.</span></span> <span data-ttu-id="d00fb-110">当用户在指定的时间长度未与设备交互时，屏幕将会关闭。</span><span class="sxs-lookup"><span data-stu-id="d00fb-110">When the user has not interacted with the device for a specified length of time, the screen will turn off.</span></span> <span data-ttu-id="d00fb-111">这将允许设备通过关闭与显示器相关的组件来进入低功耗状态。</span><span class="sxs-lookup"><span data-stu-id="d00fb-111">This will enable the device to enter a low power state by powering down components related to the display.</span></span>

```powershell
    powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setdcvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setactive SCHEME_CURRENT
```

<span data-ttu-id="d00fb-112">有关详细信息，请参阅[显示空闲超时](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout)和[显示、睡眠和休眠空闲计时器](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers)。</span><span class="sxs-lookup"><span data-stu-id="d00fb-112">For more information, see [Display Idle Timeout](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) and [Display, sleep, and hibernate idle timers](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers).</span></span>

## <a name="disabling-modern-standby"></a><span data-ttu-id="d00fb-113">禁用新式备用</span><span class="sxs-lookup"><span data-stu-id="d00fb-113">Disabling modern standby</span></span>

<span data-ttu-id="d00fb-114">在 AoAC systems (包括) 的所有 ARM 系统）时，当显示器关闭时，系统将自动进入[新式备用](/windows-hardware/design/device-experiences/modern-standby)。</span><span class="sxs-lookup"><span data-stu-id="d00fb-114">On AoAC systems (which includes all ARM systems), the system will automatically enter [modern standby](/windows-hardware/design/device-experiences/modern-standby) when the display goes off.</span></span> <span data-ttu-id="d00fb-115">当系统处于新式备用状态时，它只能由某些输入唤醒。</span><span class="sxs-lookup"><span data-stu-id="d00fb-115">When a system is in modern standby, it can only be woken by certain inputs.</span></span> <span data-ttu-id="d00fb-116">这并不是一个详尽的列表，但这些输入包括按下电源按钮、打开便携式计算机的盖子或单击鼠标。</span><span class="sxs-lookup"><span data-stu-id="d00fb-116">This is not an exhaustive list, but these inputs include pressing the power button, opening the lid on a laptop, or clicking the mouse.</span></span> <span data-ttu-id="d00fb-117">触摸屏幕将不会从新式备用设备唤醒设备。</span><span class="sxs-lookup"><span data-stu-id="d00fb-117">Touching the screen will not wake up the device from modern standby.</span></span> <span data-ttu-id="d00fb-118">如果希望设备通过触摸屏唤醒，则必须将设备配置为不进入新式备用。</span><span class="sxs-lookup"><span data-stu-id="d00fb-118">If you want your device to wake up by touch, you have to configure the device not to enter modern standby.</span></span> <span data-ttu-id="d00fb-119">若要禁用新式备用，请设置以下注册表项并重新启动。</span><span class="sxs-lookup"><span data-stu-id="d00fb-119">To disable modern standby, set the following registry key and reboot.</span></span>

```powershell
    reg add HKLM\System\CurrentControlSet\Control\Power /v PlatformAoAcOverride /t REG_DWORD /d 0
```
    
<span data-ttu-id="d00fb-120">禁用新式备用会影响系统空闲时的功率消耗。</span><span class="sxs-lookup"><span data-stu-id="d00fb-120">Disabling modern standby can impact power consumption when the system is idle.</span></span> <span data-ttu-id="d00fb-121">在决定禁用新式备用之前，应使用新式备用来度量系统的功耗并禁用。</span><span class="sxs-lookup"><span data-stu-id="d00fb-121">You should measure your system's power consumption with modern standby enabled and disabled before making the decision to disable modern standby.</span></span>

<span data-ttu-id="d00fb-122">新式备用是一种软件机制，它尝试尽可能地安静系统活动，从而允许硬件进入低功耗状态。</span><span class="sxs-lookup"><span data-stu-id="d00fb-122">Modern standby is a software mechanism that attempts to quiet system activity as much as possible, thereby allowing hardware to enter a low power state.</span></span> <span data-ttu-id="d00fb-123">从理论上讲，具有新式备用禁用功能的足够安静的设备可实现与新式备用设备相同的低功耗。</span><span class="sxs-lookup"><span data-stu-id="d00fb-123">In theory, a sufficiently quiet device with modern standby disabled can achieve the same low power consumption as a device in modern standby.</span></span> <span data-ttu-id="d00fb-124">如果禁用新式备用，则最大程度地减少后台活动（包括软件计时器和周期性任务）十分重要。</span><span class="sxs-lookup"><span data-stu-id="d00fb-124">It is important to minimize background activity including software timers and periodic tasks if modern standby is disabled.</span></span>
