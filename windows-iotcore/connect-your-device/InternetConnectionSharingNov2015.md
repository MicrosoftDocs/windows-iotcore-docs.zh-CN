---
title: Internet 连接共享教程 （2015 年 11 月发行版）
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
description: 了解如何启用和配置 internet 连接的 2015 年 11 月发行版的 Windows 共享。
keywords: windows iot，Internet 连接共享，ICS，设备门户
ms.openlocfilehash: c8f27b48197a0ec881a66da5d3e81272b3076100
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510802"
---
# <a name="internet-connection-sharing-tutorial-november-2015-release"></a><span data-ttu-id="6108c-104">Internet 连接共享教程 （2015 年 11 月发行版）</span><span class="sxs-lookup"><span data-stu-id="6108c-104">Internet Connection Sharing Tutorial (November 2015 Release)</span></span>

<span data-ttu-id="6108c-105">本文档介绍的步骤，若要运行 Windows 10 IoT 核心版的设备上启用 Internet 连接共享 (ICS) 2015 年 11 月发布。</span><span class="sxs-lookup"><span data-stu-id="6108c-105">This document describes the steps to enable Internet Connection Sharing (ICS) on a device running Windows 10 IoT Core November 2015 Release.</span></span> <span data-ttu-id="6108c-106">目的是要共享 Internet 连接的软件的 Wi-fi 访问点 (SoftAP) 和以太网适配器之间。</span><span class="sxs-lookup"><span data-stu-id="6108c-106">The objective is to share an Internet connection between a software Wi-Fi access point (SoftAP) and an Ethernet adapter.</span></span> <span data-ttu-id="6108c-107">如果使用 Windows 10 IoT Core 周年版本，请参阅[Internet 连接共享教程](InternetConnectionSharing.md)。</span><span class="sxs-lookup"><span data-stu-id="6108c-107">If you are using the Windows 10 IoT Core Anniversary Release please refer to the [Internet Connection Sharing Tutorial](InternetConnectionSharing.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6108c-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="6108c-108">Prerequisites</span></span>

* <span data-ttu-id="6108c-109">运行 Windows 10 IoT Core 设备 2015 年 11 月发布。</span><span class="sxs-lookup"><span data-stu-id="6108c-109">Device running Windows 10 IoT Core November 2015 Release.</span></span>
* <span data-ttu-id="6108c-110">支持启动 SoftAP 的 WLAN USB 设备。</span><span class="sxs-lookup"><span data-stu-id="6108c-110">Wi-Fi USB device capable of starting a SoftAP.</span></span> <span data-ttu-id="6108c-111">请参阅[硬件兼容性列表](../learn-about-hardware/HardwareCompatList.md)对于支持的 Wi-fi USB 设备。</span><span class="sxs-lookup"><span data-stu-id="6108c-111">Please refer to the [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md) for supported Wi-Fi USB devices.</span></span>
* <span data-ttu-id="6108c-112">具有 Internet 访问权限的以太网连接。</span><span class="sxs-lookup"><span data-stu-id="6108c-112">Ethernet connection with Internet Access.</span></span>


## <a name="setup"></a><span data-ttu-id="6108c-113">安装</span><span class="sxs-lookup"><span data-stu-id="6108c-113">Setup</span></span>

### <a name="step-1-gathering-network-information"></a><span data-ttu-id="6108c-114">第 1 步：收集网络信息</span><span class="sxs-lookup"><span data-stu-id="6108c-114">Step 1: Gathering Network Information</span></span>

1. <span data-ttu-id="6108c-115">在插入 WLAN 硬件保护装置、插入以太网电缆的情况下启动设备。</span><span class="sxs-lookup"><span data-stu-id="6108c-115">Boot up device with Wi-Fi dongle plugged in, Ethernet cable plugged in.</span></span>
2. <span data-ttu-id="6108c-116">从 IoT 核心版设备启动 SoftAP。</span><span class="sxs-lookup"><span data-stu-id="6108c-116">Start SoftAP from the IoT Core device.</span></span>

   <span data-ttu-id="6108c-117">默认情况下，Microsoft 将在安装程序 SoftAP 如果 Wi-fi 无线电能够并且没有 WLAN 配置文件已添加的 IoT 载入应用程序提供映像开始。</span><span class="sxs-lookup"><span data-stu-id="6108c-117">By default, the Microsoft provided images start an IoT Onboarding application that will setup a SoftAP if Wi-Fi radio is capable and no WLAN profile has been added.</span></span> <span data-ttu-id="6108c-118">若要启动 SoftAP，UWP 应用程序可以使用 [Windows.Devices.WiFiDirect.WiFiDirectAdvertisementPublisher API](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6108c-118">To start SoftAP, UWP applications can use the [Windows.Devices.WiFiDirect.WiFiDirectAdvertisementPublisher API](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx).</span></span> <span data-ttu-id="6108c-119">IoT 登记应用程序的源代码可在 GitHub 上[IoTOnboarding](https://github.com/ms-iot/samples/tree/develop/IotOnboarding)。</span><span class="sxs-lookup"><span data-stu-id="6108c-119">The source code for the IoT Onboarding application can be on GitHub [IoTOnboarding](https://github.com/ms-iot/samples/tree/develop/IotOnboarding).</span></span>

   <span data-ttu-id="6108c-120">记录 SoftAP 网络的 SSID。</span><span class="sxs-lookup"><span data-stu-id="6108c-120">Record the SSID of the SoftAP network.</span></span> <span data-ttu-id="6108c-121">你以后将需要它来通过 WLAN 连接到 IoT 核心版设备。</span><span class="sxs-lookup"><span data-stu-id="6108c-121">You will need it later to connect to your IoT Core device via Wi-Fi.</span></span> <span data-ttu-id="6108c-122">IoT 登记应用程序的 SSID 将启动与"AJ\_SoftAPSsid\_"，并且可以在应用程序的配置更改[文件](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml)。</span><span class="sxs-lookup"><span data-stu-id="6108c-122">For IoT Onboarding application the SSID will start with "AJ\_SoftAPSsid\_" and can be changed in application's configuration [file](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml).</span></span>

3. <span data-ttu-id="6108c-123">远程连接到 IoT Core 设备[使用 ssh](ssh.md)。</span><span class="sxs-lookup"><span data-stu-id="6108c-123">Remotely connect to the IoT Core device [using ssh](ssh.md).</span></span>
4. <span data-ttu-id="6108c-124">通过查找网络设备索引和描述来收集有关设备网络的信息。</span><span class="sxs-lookup"><span data-stu-id="6108c-124">Collect information about device networks by finding network device indexes and descriptions.</span></span> <span data-ttu-id="6108c-125">声明要桥接哪些网络需要执行此操作。</span><span class="sxs-lookup"><span data-stu-id="6108c-125">This is needed to declare which networks to bridge.</span></span>

   <span data-ttu-id="6108c-126">在设备上，运行 **route print** 并收集以下数据：</span><span class="sxs-lookup"><span data-stu-id="6108c-126">On device, run **route print** and collect the following data:</span></span>

   * <span data-ttu-id="6108c-127">记录以太网的公共接口网络索引。</span><span class="sxs-lookup"><span data-stu-id="6108c-127">Record PUBLIC Interface network index for the Ethernet.</span></span>
   * <span data-ttu-id="6108c-128">记录 SoftAP 的专用接口网络索引（例如“Microsoft WLAN Direct 虚拟适配器 #2”）。</span><span class="sxs-lookup"><span data-stu-id="6108c-128">Record PRIVATE Interface network index for the SoftAP (e.g. “Microsoft Wi-Fi Direct Virtual Adapter #2”).</span></span>

   <span data-ttu-id="6108c-129">例如，SoftAP 通过接口索引 5 公开，适配器描述为“Microsoft WLAN Direct 虚拟适配器 #2”。</span><span class="sxs-lookup"><span data-stu-id="6108c-129">For example, the SoftAP is exposed through interface index 5, adapter description “Microsoft Wi-Fi Direct Virtual Adapter #2”.</span></span>

   ![route print](../media/InternetConnectionSharing/internetconnectionsharing_route.png)

   <span data-ttu-id="6108c-131">在设备上，运行 **ipconfig /all** 并收集以下数据：</span><span class="sxs-lookup"><span data-stu-id="6108c-131">On device, run **ipconfig /all** and collect the following data:</span></span>
    
   * <span data-ttu-id="6108c-132">记录 SoftAP 的专用接口网络适配器名称</span><span class="sxs-lookup"><span data-stu-id="6108c-132">Record PRIVATE Interface network adapter name for the SoftAP</span></span>

   <span data-ttu-id="6108c-133">例如，运行"ipconfig /all"查找特定的适配器名为"本地区域连接 \* 3"、"Microsoft Wi-Fi Direct 虚拟适配器 #2"的描述。</span><span class="sxs-lookup"><span data-stu-id="6108c-133">For example, running "ipconfig /all" finds the specific adapter named “Local Area Connection\* 3” that has a description of “Microsoft Wi-Fi Direct Virtual Adapter #2”.</span></span> <span data-ttu-id="6108c-134">使用此方法从“route print”中返回的描述中查找适配器名称。</span><span class="sxs-lookup"><span data-stu-id="6108c-134">Use this method to manually find Adapter Name from the Description returned in “route print”.</span></span>

   ![ipconfig all](../media/InternetConnectionSharing/internetconnectionsharing_ipconfig.png)

### <a name="step-2-scripting-internet-connection-sharing-trigger"></a><span data-ttu-id="6108c-136">步骤 2：编写 Internet 连接共享触发器脚本</span><span class="sxs-lookup"><span data-stu-id="6108c-136">Step 2: Scripting Internet Connection Sharing trigger</span></span>

<span data-ttu-id="6108c-137">从 Internet 连接共享开始两个网络之间需要执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="6108c-137">Starting Internet Connection Sharing between two networks requires the following steps:</span></span>

* <span data-ttu-id="6108c-138">设置注册表项来设置要桥接的专用 (SoftAP) 和公共（以太网）网络接口。</span><span class="sxs-lookup"><span data-stu-id="6108c-138">Set registry keys to set private (SoftAP) and public (Ethernet) network interfaces to bridge.</span></span>
* <span data-ttu-id="6108c-139">设置相应的防火墙规则。</span><span class="sxs-lookup"><span data-stu-id="6108c-139">Set appropriate firewall rules.</span></span>
* <span data-ttu-id="6108c-140">在专用接口上关闭 DHCP。</span><span class="sxs-lookup"><span data-stu-id="6108c-140">Turns off DHCP on private interface.</span></span>
* <span data-ttu-id="6108c-141">在专用接口上设置静态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="6108c-141">Sets static IP address on private interface.</span></span>
* <span data-ttu-id="6108c-142">启动 SharedAccess 服务。</span><span class="sxs-lookup"><span data-stu-id="6108c-142">Starts SharedAccess service.</span></span>
* <span data-ttu-id="6108c-143">将命令代码“129”发送到 SharedAccess 服务。</span><span class="sxs-lookup"><span data-stu-id="6108c-143">Sends command code “129” to SharedAccess service.</span></span>


#### <a name="create-a-script-to-automate-the-ics-settings"></a><span data-ttu-id="6108c-144">创建一个脚本来自动执行 ICS 设置</span><span class="sxs-lookup"><span data-stu-id="6108c-144">Create a script to automate the ICS settings</span></span>

<span data-ttu-id="6108c-145">下面是脚本的示例和代码来自动执行上面列出的步骤可以集成到设备启动顺序。</span><span class="sxs-lookup"><span data-stu-id="6108c-145">Below is an example of a scripts and code to automate the steps listed above that can be integrated into the device startup sequence.</span></span> <span data-ttu-id="6108c-146">创建脚本文件 (例如**ConfigureICS.cmd**) 包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="6108c-146">Create a script file (e.g. **ConfigureICS.cmd**) with the following content:</span></span>

```
echo off

set START_OR_STOP=%1
set PUBLIC_INDEX=%2
set PRIVATE_INDEX=%3
set PRIVATE_INTERFACE_NAME=%4

if not defined PRIVATE_INTERFACE_NAME (
  goto usage
)

if "%START_OR_STOP%"=="start" (

  REM Set the public and private interface registry keys
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v private /t REG_DWORD /d %PRIVATE_INDEX%
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v public /t REG_DWORD /d %PUBLIC_INDEX%

  REM Set the firewall rules to allow DHCP to work
  netsh advfirewall firewall add rule name=\"AllowPort67In\" protocol=UDP dir=in localport=67 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort68In\" protocol=UDP dir=in localport=68 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort67Out\" protocol=UDP dir=out localport=67 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort68Out\" protocol=UDP dir=out localport=68 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort53Out\" protocol=UDP dir=out localport=53 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort53In\" protocol=UDP dir=in localport=53 action=allow

  REM Turn off DHCP and set static IP for private interface
  netsh interface ip set address %4 static 192.168.137.1

  REM Start sharing
  call SharedAccessUtility.exe start

) else if "%START_OR_STOP%"=="stop" (

  REM Stop sharing
  call SharedAccessUtility.exe stop

  REM Set the public and private interface registry keys
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v private /t REG_DWORD /d 0
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v public /t REG_DWORD /d 0

  REM Clear the firewall rules
  netsh advfirewall firewall delete rule name="AllowPort67In"
  netsh advfirewall firewall delete rule name="AllowPort68In"
  netsh advfirewall firewall delete rule name="AllowPort67Out"
  netsh advfirewall firewall delete rule name="AllowPort68Out"
  netsh advfirewall firewall delete rule name="AllowPort53Out"
  netsh advfirewall firewall delete rule name="AllowPort53In"

  REM Reenable DHCP for private interface
  netsh interface ip set address %4 dhcp

) else (
  goto usage
)

goto eof

:usage
ECHO USAGE: %0 [start ^| stop] [public interface index] [private interface index] [private interface name]
ECHO e.g. %0 start 1 2 "Ethernet"

:eof
```

<span data-ttu-id="6108c-147">此脚本将执行除启动/停止 SharedAccess 服务之外的一切操作，并且不会发送服务命令。</span><span class="sxs-lookup"><span data-stu-id="6108c-147">This script will do everything but start/stop SharedAccess service, and does not send service command.</span></span> <span data-ttu-id="6108c-148">对于这些任务，它调用到 SharedAccessUtility.exe（需要创建此程序）。</span><span class="sxs-lookup"><span data-stu-id="6108c-148">For those tasks it calls to SharedAccessUtility.exe, which needs to be created.</span></span>

#### <a name="build-the-sharedaccessutility-application"></a><span data-ttu-id="6108c-149">生成 SharedAccessUtility 应用程序</span><span class="sxs-lookup"><span data-stu-id="6108c-149">Build the SharedAccessUtility application</span></span>
<span data-ttu-id="6108c-150">在安装了 [Windows IoT 核心版项目模板扩展](https://go.microsoft.com/fwlink/?linkid=847472)的 Visual Studio 中，创建新的名为“SharedAccessUtility”的“空白 Windows IoT 核心版控制台应用程序”。</span><span class="sxs-lookup"><span data-stu-id="6108c-150">In Visual Studio with [Windows IoT Core Project Templates extensions](https://go.microsoft.com/fwlink/?linkid=847472) installed, create a new “Blank Windows IoT Core Console Application” Visual C++ project, named **SharedAccessUtility**.</span></span>

![VS 新建项目](../media/InternetConnectionSharing/internetconnectionsharing_vs.png)

<span data-ttu-id="6108c-152">将 ConsoleApplication.cpp 的内容替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="6108c-152">Replace contents of ConsoleApplication.cpp with the following code:</span></span>

```C++
#include "pch.h"
#include <ws2tcpip.h>
#include <iphlpapi.h>
#include <mstcpip.h>
#include <stdio.h>

#define SHARED_ACCESS_NAME L"SharedAccess"
#define START_SHARING_CONTROL 129

DWORD StartSharedAccessService(SC_HANDLE *phScm, SC_HANDLE *phSvc)
{
    DWORD dwError = ERROR_SUCCESS;
    SERVICE_STATUS svcStatus = { 0 };

    // open a handle to SCM
    *phScm = OpenSCManager(NULL, NULL, SC_MANAGER_CONNECT);
    if (*phScm == NULL)
    {
        dwError = GetLastError();
        printf("\nOpenSCManager failed; error = %d", dwError);
    }
    else
    {
        // open a handle to the service
        *phSvc = OpenService(*phScm, SHARED_ACCESS_NAME, SERVICE_START | SERVICE_QUERY_STATUS | SERVICE_QUERY_CONFIG | SERVICE_STOP | SERVICE_USER_DEFINED_CONTROL);
        if (*phSvc == NULL)
        {
            dwError = GetLastError();
            printf("\nOpenService failed; error = %d", dwError);
        }
        else
        {
            if (!StartService(*phSvc, 0, NULL))
            {
                dwError = GetLastError();
                if (dwError != ERROR_SERVICE_ALREADY_RUNNING)
                {
                    printf("\nStartService failed; error = %d", dwError);
                }
                else
                {
                    dwError = ERROR_SUCCESS;
                    printf("\nService already running.");
                }
            }

            if (dwError == ERROR_SUCCESS)
            {
                if (QueryServiceStatus(*phSvc, &svcStatus) && svcStatus.dwCurrentState != SERVICE_RUNNING)
                {
                    for (int i = 0; i < 10; i++)
                    {
                        printf("\nWaiting 1 second for service to start.");
                        Sleep(1000);
                        if (QueryServiceStatus(*phSvc, &svcStatus))
                        {
                            if (svcStatus.dwCurrentState == SERVICE_RUNNING)
                            {
                                printf("\nService is running.");
                                // it is, so break out
                                dwError = ERROR_SUCCESS;
                                break;
                            }
                            else
                            {
                                if (svcStatus.dwCurrentState == SERVICE_STOPPED)
                                {
                                    printf("\nService could not run.");
                                    // it is, so break out
                                    dwError = ERROR_SERVICE_NOT_ACTIVE;
                                    break;
                                }
                            }
                        }
                        else
                        {
                            printf("\nWaiting more time.");
                        }
                    }
                }
            }
        }
    }

    if (dwError == ERROR_SUCCESS) //service is running
    {
        if (!ControlService(*phSvc, START_SHARING_CONTROL, &svcStatus))
        {
            dwError = GetLastError();
            printf("\nControl service for start sharing failure, %d", dwError);
        }
        else
        {
            printf("\nSharing started");
        }
    }

    // Service cleanup done at the main.
    return dwError;
}


DWORD StopSharedAccessService(SC_HANDLE *phSvc)
{
    DWORD dwError = ERROR_SUCCESS;
    SERVICE_STATUS svcStatus = { 0 };

    if (!QueryServiceStatus(*phSvc, &svcStatus))
    {
        dwError = GetLastError();
        printf("\nFailed to query sharedaccess, %d", dwError);
    }
    else
    {
        if (svcStatus.dwCurrentState != SERVICE_STOPPED)
        {
            if (ControlService(*phSvc, SERVICE_CONTROL_STOP, &svcStatus))
            {
                if (QueryServiceStatus(*phSvc, &svcStatus) && svcStatus.dwCurrentState != SERVICE_STOPPED)
                {
                    for (int i = 0; i < 10; i++)
                    {
                        printf("\nWaiting 1 second for service to stop.");
                        Sleep(1000);
                        if (QueryServiceStatus(*phSvc, &svcStatus))
                        {
                            if (svcStatus.dwCurrentState == SERVICE_STOPPED)
                            {
                                printf("\nService stopped.");
                                // it is, so break out
                                dwError = ERROR_SUCCESS;
                                break;
                            }
                            else
                            {
                                printf("\nWaiting more time.");
                            }
                        }
                    }
                }
            }
        }
    }
    return dwError;
}

void ShowUsage()
{
    printf("Usage: SharedAccessUtility.exe start | stop\n"
        "Setup: Make sure the public and private interfaces are up and running and that the SharedAccess registry keys are set.");
}

int __cdecl
main(
    __in int argc,
    __in_ecount(argc) LPSTR argv[]
    )
{
    SC_HANDLE hScm = NULL;
    SC_HANDLE hSvc = NULL;
    DWORD dwError = NO_ERROR;
    bool startSharing = true;

    if (argc < 2)
    {
        ShowUsage();
        return -1;
    }
    else
    {
        if (strcmp(argv[1], "start") == 0 || strcmp(argv[1], "/start") == 0)
        {
            startSharing = true;
        }
        else if (strcmp(argv[1], "stop") == 0 || strcmp(argv[1], "/stop") == 0)
        {
            startSharing = false;
        }
        else
        {
            ShowUsage();
            return -1;
        }
    }

    dwError = startSharing ? StartSharedAccessService(&hScm, &hSvc) : StopSharedAccessService(&hSvc);

    // Cleanup
    if (hSvc != NULL)
    {
        CloseServiceHandle(hSvc);
        hSvc = NULL;
    }
    if (hScm != NULL)
    {
        CloseServiceHandle(hScm);
        hScm = NULL;
    }
    return 0;
}
```

<span data-ttu-id="6108c-153">针对目标体系结构（例如版本 x86 ）进行生成，并找到输出 **SharedAccessUtility.exe**</span><span class="sxs-lookup"><span data-stu-id="6108c-153">Build for target architecture, e.g. Release x86, and locate output **SharedAccessUtility.exe**</span></span>

### <a name="step-3-starting-internet-connection-sharing"></a><span data-ttu-id="6108c-154">步骤 3:启动 Internet 连接共享</span><span class="sxs-lookup"><span data-stu-id="6108c-154">Step 3: Starting Internet Connection Sharing</span></span>

1. <span data-ttu-id="6108c-155">复制**ConfigICS.cmd**步骤 2 中创建到设备中某个位置，例如到脚本</span><span class="sxs-lookup"><span data-stu-id="6108c-155">Copy **ConfigICS.cmd** script created in Step 2 to the device in some location, e.g. to</span></span> `C:\test\`
2. <span data-ttu-id="6108c-156">复制**SharedAccessUtility.exe**步骤 2 中创建到设备中相同的位置，例如 `C:\test`\\</span><span class="sxs-lookup"><span data-stu-id="6108c-156">Copy **SharedAccessUtility.exe** created in Step 2 to the device in the same location, e.g. `C:\test`\\</span></span>
3. <span data-ttu-id="6108c-157">在设备上运行**C:\test\ConfigureICS.cmd 开始 [公共 index] [专用索引] [专用适配器名称]** 在此示例中，这可能是<strong>C:\test\ConfigureICS.cmd 启动 4 5"本地区域连接 \* 3"</strong></span><span class="sxs-lookup"><span data-stu-id="6108c-157">On the device, run **C:\test\ConfigureICS.cmd start [public index] [private index] [private adapter name]** In this example, this would mean <strong>C:\test\ConfigureICS.cmd start 4 5 "Local Area Connection\* 3"</strong></span></span>

<span data-ttu-id="6108c-158">此时设备已启用 Internet 连接共享的任何客户端连接到设备的播发 SSID。</span><span class="sxs-lookup"><span data-stu-id="6108c-158">At this point the device has enabled Internet Connection Sharing for any client connected to the device’s advertised SSID.</span></span>
