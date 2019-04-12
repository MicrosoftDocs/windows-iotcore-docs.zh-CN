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
# <a name="configure-your-device-to-wake-on-touch"></a><span data-ttu-id="2d871-104">配置用于唤醒触摸设备</span><span class="sxs-lookup"><span data-stu-id="2d871-104">Configure your device to wake on touch</span></span>

<span data-ttu-id="2d871-105">在某些情况下，你想在不使用时关闭和开启快速时用户涉及在触摸屏设备的屏幕。</span><span class="sxs-lookup"><span data-stu-id="2d871-105">In some scenarios, you want your device's screen to turn off while not in use and to turn on quickly when a user touches the touchscreen.</span></span> <span data-ttu-id="2d871-106">本文档介绍如何配置你的设备以实现此方案。</span><span class="sxs-lookup"><span data-stu-id="2d871-106">This document describes how to configure your device to achieve this scenario.</span></span>

## <a name="setting-a-video-idle-timeout"></a><span data-ttu-id="2d871-107">设置视频的空闲超时</span><span class="sxs-lookup"><span data-stu-id="2d871-107">Setting a video idle timeout</span></span>

<span data-ttu-id="2d871-108">你可以配置屏幕来设置视频的空闲超时将处于非活动状态一段时间后关闭。</span><span class="sxs-lookup"><span data-stu-id="2d871-108">You can configure the screen to turn off after a period of inactivity by setting a video idle timeout.</span></span> <span data-ttu-id="2d871-109">当用户不与指定的时间长度的设备交互时，屏幕将关闭。</span><span class="sxs-lookup"><span data-stu-id="2d871-109">When the user has not interacted with the device for a specified length of time, the screen will turn off.</span></span> <span data-ttu-id="2d871-110">这将使设备可以通过关闭组件显示相关的输入低功耗状态。</span><span class="sxs-lookup"><span data-stu-id="2d871-110">This will enable the device to enter a low power state by powering down components related to the display.</span></span>

```
    powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setdcvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setactive SCHEME_CURRENT
```

<span data-ttu-id="2d871-111">有关详细信息，请参阅[显示器空闲超时](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout)并[显示，进入睡眠状态，并进入休眠状态的空闲计时器](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers)。</span><span class="sxs-lookup"><span data-stu-id="2d871-111">For more information, see [Display Idle Timeout](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) and [Display, sleep, and hibernate idle timers](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers).</span></span>

## <a name="disabling-modern-standby"></a><span data-ttu-id="2d871-112">禁用现代待机状态</span><span class="sxs-lookup"><span data-stu-id="2d871-112">Disabling modern standby</span></span>

<span data-ttu-id="2d871-113">AoAC 在系统上 （其中包括所有 ARM 系统），系统会自动进入[现代待机](/windows-hardware/design/device-experiences/modern-standby)时，显示器变。</span><span class="sxs-lookup"><span data-stu-id="2d871-113">On AoAC systems (which includes all ARM systems), the system will automatically enter [modern standby](/windows-hardware/design/device-experiences/modern-standby) when the display goes off.</span></span> <span data-ttu-id="2d871-114">现代的备用系统时，只能由特定输入唤醒。</span><span class="sxs-lookup"><span data-stu-id="2d871-114">When a system is in modern standby, it can only be woken by certain inputs.</span></span> <span data-ttu-id="2d871-115">这不是详尽的列表，但这些输入包括按电源按钮，打开在便携式计算机，合上的盖子或单击鼠标。</span><span class="sxs-lookup"><span data-stu-id="2d871-115">This is not an exhaustive list, but these inputs include pressing the power button, opening the lid on a laptop, or clicking the mouse.</span></span> <span data-ttu-id="2d871-116">触摸屏幕将唤醒从待机现代设备。</span><span class="sxs-lookup"><span data-stu-id="2d871-116">Touching the screen will not wake up the device from modern standby.</span></span> <span data-ttu-id="2d871-117">如果你想通过触摸唤醒设备，必须配置该设备无法进入现代待机状态。</span><span class="sxs-lookup"><span data-stu-id="2d871-117">If you want your device to wake up by touch, you have to configure the device not to enter modern standby.</span></span> <span data-ttu-id="2d871-118">若要禁用现代待机状态，请设置以下注册表项和重新启动。</span><span class="sxs-lookup"><span data-stu-id="2d871-118">To disable modern standby, set the following registry key and reboot.</span></span>

```
    reg add HKLM\System\CurrentControlSet\Control\Power /v PlatformAoAcOverride /t REG_DWORD /d 0
```
    
<span data-ttu-id="2d871-119">当系统处于空闲状态时，禁用现代待机状态可能会影响功率消耗。</span><span class="sxs-lookup"><span data-stu-id="2d871-119">Disabling modern standby can impact power consumption when the system is idle.</span></span> <span data-ttu-id="2d871-120">应采用现代的备用模式启用和禁用之前做出的决策，若要禁用现代待机状态来测量系统的功率消耗。</span><span class="sxs-lookup"><span data-stu-id="2d871-120">You should measure your system's power consumption with modern standby enabled and disabled before making the decision to disable modern standby.</span></span>

<span data-ttu-id="2d871-121">现代备用操作主机是一种软件机制，尝试尽可能多地，从而允许硬件进入低功耗状态无人参与的系统活动。</span><span class="sxs-lookup"><span data-stu-id="2d871-121">Modern standby is a software mechanism that attempts to quiet system activity as much as possible, thereby allowing hardware to enter a low power state.</span></span> <span data-ttu-id="2d871-122">从理论上讲，具有现代备用已禁用的足够静默设备可以实现为在现代备用设备相同的低功率消耗。</span><span class="sxs-lookup"><span data-stu-id="2d871-122">In theory, a sufficiently quiet device with modern standby disabled can achieve the same low power consumption as a device in modern standby.</span></span> <span data-ttu-id="2d871-123">请务必最大程度减少后台活动，包括软件计时器和定期任务，如果禁用了现代待机状态。</span><span class="sxs-lookup"><span data-stu-id="2d871-123">It is important to minimize background activity including software timers and periodic tasks if modern standby is disabled.</span></span>
