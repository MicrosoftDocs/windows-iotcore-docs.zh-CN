---
title: 触控唤醒
author: jordanrh1
ms.author: jordanrh
ms.date: 09/17/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 将设备配置为触控时唤醒，以便设备在不使用时关闭，但在触摸屏幕时快速打开。 设置视频空闲超时。
keywords: windows iot， 屏幕， 睡眠， 唤醒， 触摸， 待机， 电源
ms.custom: RS5
ms.openlocfilehash: 0e2aa787b4950914d14630c44b38a9e42f06f4fc
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228693"
---
# <a name="configure-your-device-to-wake-on-touch"></a><span data-ttu-id="24c6b-105">将设备配置为触控唤醒</span><span class="sxs-lookup"><span data-stu-id="24c6b-105">Configure your device to wake on touch</span></span>

<span data-ttu-id="24c6b-106">在某些情况下，希望设备屏幕在不使用时关闭，在用户触摸触摸屏时快速打开。</span><span class="sxs-lookup"><span data-stu-id="24c6b-106">In some scenarios, you want your device's screen to turn off while not in use and to turn on quickly when a user touches the touchscreen.</span></span> <span data-ttu-id="24c6b-107">本文档介绍如何配置设备以实现此方案。</span><span class="sxs-lookup"><span data-stu-id="24c6b-107">This document describes how to configure your device to achieve this scenario.</span></span>

## <a name="setting-a-video-idle-timeout"></a><span data-ttu-id="24c6b-108">设置视频空闲超时</span><span class="sxs-lookup"><span data-stu-id="24c6b-108">Setting a video idle timeout</span></span>

<span data-ttu-id="24c6b-109">可以通过设置视频空闲超时，将屏幕配置为在处于非活动状态一段时间后关闭。</span><span class="sxs-lookup"><span data-stu-id="24c6b-109">You can configure the screen to turn off after a period of inactivity by setting a video idle timeout.</span></span> <span data-ttu-id="24c6b-110">如果用户在指定的时间长度内未与设备交互，屏幕将关闭。</span><span class="sxs-lookup"><span data-stu-id="24c6b-110">When the user has not interacted with the device for a specified length of time, the screen will turn off.</span></span> <span data-ttu-id="24c6b-111">这将通过关闭与显示器相关的组件，使设备能够进入低功率状态。</span><span class="sxs-lookup"><span data-stu-id="24c6b-111">This will enable the device to enter a low-power state by powering down components related to the display.</span></span>

```powershell
    powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setdcvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setactive SCHEME_CURRENT
```

<span data-ttu-id="24c6b-112">有关详细信息，请参阅显示[空闲超时](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout)[和显示、睡眠和休眠空闲计时器](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers)。</span><span class="sxs-lookup"><span data-stu-id="24c6b-112">For more information, see [Display Idle Timeout](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) and [Display, sleep, and hibernate idle timers](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers).</span></span>

## <a name="disabling-modern-standby"></a><span data-ttu-id="24c6b-113">禁用新式待机</span><span class="sxs-lookup"><span data-stu-id="24c6b-113">Disabling modern standby</span></span>

<span data-ttu-id="24c6b-114">在包含所有 ARM (的 AoAC 系统上) ，当显示器关闭时，系统将自动[](/windows-hardware/design/device-experiences/modern-standby)进入新式待机。</span><span class="sxs-lookup"><span data-stu-id="24c6b-114">On AoAC systems (which includes all ARM systems), the system will automatically enter [modern standby](/windows-hardware/design/device-experiences/modern-standby) when the display goes off.</span></span> <span data-ttu-id="24c6b-115">当系统处于新式待机状态时，它只能被某些输入唤醒。</span><span class="sxs-lookup"><span data-stu-id="24c6b-115">When a system is in modern standby, it can only be woken by certain inputs.</span></span> <span data-ttu-id="24c6b-116">这不是详尽列表，但这些输入包括按电源按钮、打开笔记本电脑上的盖或单击鼠标。</span><span class="sxs-lookup"><span data-stu-id="24c6b-116">This is not an exhaustive list, but these inputs include pressing the power button, opening the lid on a laptop, or clicking the mouse.</span></span> <span data-ttu-id="24c6b-117">触摸屏幕不会从新式待机唤醒设备。</span><span class="sxs-lookup"><span data-stu-id="24c6b-117">Touching the screen will not wake up the device from modern standby.</span></span> <span data-ttu-id="24c6b-118">如果希望设备通过触摸唤醒，必须配置设备，不进入新式待机。</span><span class="sxs-lookup"><span data-stu-id="24c6b-118">If you want your device to wake up by touch, you have to configure the device not to enter modern standby.</span></span> <span data-ttu-id="24c6b-119">若要禁用新式待机，请设置以下注册表项并重新启动。</span><span class="sxs-lookup"><span data-stu-id="24c6b-119">To disable modern standby, set the following registry key and reboot.</span></span>

```powershell
    reg add HKLM\System\CurrentControlSet\Control\Power /v PlatformAoAcOverride /t REG_DWORD /d 0
```
    
<span data-ttu-id="24c6b-120">当系统处于空闲状态时，禁用新式待机可能会影响功耗。</span><span class="sxs-lookup"><span data-stu-id="24c6b-120">Disabling modern standby can impact power consumption when the system is idle.</span></span> <span data-ttu-id="24c6b-121">在决定禁用新式待机之前，应在启用和禁用新式待机时测量系统的功耗。</span><span class="sxs-lookup"><span data-stu-id="24c6b-121">You should measure your system's power consumption with modern standby enabled and disabled before making the decision to disable modern standby.</span></span>

<span data-ttu-id="24c6b-122">新式待机是一种软件机制，它尝试尽可能使系统活动静默，从而使硬件进入低功率状态。</span><span class="sxs-lookup"><span data-stu-id="24c6b-122">Modern standby is a software mechanism that attempts to quiet system activity as much as possible, thereby allowing hardware to enter a low-power state.</span></span> <span data-ttu-id="24c6b-123">从理论上讲，禁用新式待机的足够静默的设备可以实现与新式待机设备相同的低能耗。</span><span class="sxs-lookup"><span data-stu-id="24c6b-123">In theory, a sufficiently quiet device with modern standby disabled can achieve the same low power consumption as a device in modern standby.</span></span> <span data-ttu-id="24c6b-124">如果禁用新式待机，必须尽量减少后台活动，包括软件计时器和定期任务。</span><span class="sxs-lookup"><span data-stu-id="24c6b-124">It is important to minimize background activity including software timers and periodic tasks if modern standby is disabled.</span></span>
