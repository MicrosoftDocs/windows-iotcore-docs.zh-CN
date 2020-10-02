---
title: 'Internet 连接共享教程 (2015 年11月版) '
ms.date: 09/06/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何启用和配置 Windows 2015 年11月版的 internet 连接共享。
keywords: windows iot，Internet 连接共享，ICS，设备门户
ms.openlocfilehash: 523fce338a6461a9c7f765b54c6448afe7423008
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656773"
---
# <a name="internet-connection-sharing-tutorial-november-2015-release"></a>Internet 连接共享教程 (2015 年11月版) 

本文档介绍在运行 Windows 10 IoT Core 11 月2015版的设备上 (ICS) 启用 Internet 连接共享的步骤。 目标是在软件 Wi-fi 接入点 (SoftAP) 与以太网适配器之间共享 Internet 连接。 如果使用的是 Windows 10 IoT Core 周年版，请参阅 [Internet 连接共享教程](InternetConnectionSharing.md)。

## <a name="prerequisites"></a>必备条件

* 运行 Windows 10 IoT Core 11 月2015版的设备。
* Wi-fi USB 设备能够启动 SoftAP。 请参阅支持的 Wi-fi USB 设备的 [硬件兼容性列表](../learn-about-hardware/HardwareCompatList.md) 。
* 与 Internet 访问的以太网连接。


## <a name="setup"></a>设置

### <a name="step-1-gathering-network-information"></a>步骤1：收集网络信息

1. 用接通电源的设备启动设备，并插入以太网电缆。
2. 从 IoT Core 设备启动 SoftAP。

   默认情况下，Microsoft 提供的映像将启动一个 IoT 载入应用程序，该应用程序将设置 SoftAP （如果 Wi-fi 无线功能可用且未添加任何 WLAN 配置文件）。 若要启动 SoftAP，UWP 应用程序可使用 [WiFiDirect. WIFIDIRECTADVERTISEMENTPUBLISHER API](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx)。 IoT 载入应用程序的源代码可以位于 GitHub [IoTOnboarding](https://github.com/ms-iot/samples/tree/develop/IotOnboarding)上。

   记录 SoftAP 网络的 SSID。 稍后你将需要它通过 Wi-fi 连接到 IoT Core 设备。 对于 IoT 载入应用程序，SSID 将以 "AJ \_ SoftAPSsid \_ " 开头，可以在应用程序的配置 [文件](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml)中进行更改。

3. [使用 ssh](ssh.md)远程连接到 IoT Core 设备。
4. 通过查找网络设备索引和说明收集有关设备网络的信息。 这是声明要桥接哪些网络所必需的。

   在设备上，运行 **路由打印** 并收集以下数据：

   * 为以太网记录公共接口网络索引。
   * 记录 SoftAP (的专用接口网络索引，例如 "Microsoft Wi-fi Direct 虚拟适配器 #2" ) 。

   例如，SoftAP 通过接口索引5、适配器说明 "Microsoft Wi-fi Direct 虚拟适配器 #2" 公开。

   ![路由打印](../media/InternetConnectionSharing/internetconnectionsharing_route.png)

   在设备上，运行 **ipconfig/all** 并收集以下数据：
    
   * 记录 SoftAP 的专用接口网络适配器名称

   例如，运行 "ipconfig/all" 将查找名为 "本地连接" 的特定适配器，该适配器的描述为 "Microsoft Wi-fi Direct 虚拟适配器 #2"。 使用此方法可以从 "路由打印" 中返回的描述中手动查找适配器名称。

   ![全部 ipconfig](../media/InternetConnectionSharing/internetconnectionsharing_ipconfig.png)

### <a name="step-2-scripting-internet-connection-sharing-trigger"></a>步骤2：编写 Internet 连接共享的脚本触发器

在两个网络之间启动 Internet 连接共享需要执行以下步骤：

* 设置注册表项以将专用 (SoftAP) 和公共 (以太网) 网络接口设置为桥。
* 设置适当的防火墙规则。
* 关闭专用接口上的 DHCP。
* 设置专用接口上的静态 IP 地址。
* 启动 Win2k3 服务。
* 将命令代码 "129" 发送到 Win2k3 服务。


#### <a name="create-a-script-to-automate-the-ics-settings"></a>创建脚本以自动执行 ICS 设置

下面是一个脚本和代码示例，用于自动执行上面列出的可集成到设备启动序列中的步骤。 使用以下内容创建一个脚本文件 (例如 **ConfigureICS**) ：

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

此脚本将执行所有操作，但不会启动/停止 Win2k3 服务，也不会发送服务命令。 对于它调用 SharedAccessUtility.exe 的任务，需要创建该任务。

#### <a name="build-the-sharedaccessutility-application"></a>生成 SharedAccessUtility 应用程序
在安装了 [Windows IoT Core 项目模板扩展](https://go.microsoft.com/fwlink/?linkid=847472) 的 Visual Studio 中，创建一个名为 **SharedAccessUtility**的新的 "空白 Windows Iot core 控制台应用程序" Visual C++ 项目。

![VS 新项目](../media/InternetConnectionSharing/internetconnectionsharing_vs.png)

将控制台应用程序的内容替换为以下代码：

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

针对目标体系结构（例如，发布 x86）的生成，并找到输出 **SharedAccessUtility.exe**

### <a name="step-3-starting-internet-connection-sharing"></a>步骤3：启动 Internet 连接共享

1. 将在步骤2中创建的 **ConfigICS** 脚本复制到某个位置的设备，例如 `C:\test\`
2. 将步骤2中创建的 **SharedAccessUtility.exe** 复制到同一位置中的设备，例如 `C:\test`\
3. 在设备上，运行 **C:\test\ConfigureICS.cmd start [public index] [private index] [private adapter name]** 在本示例中，这意味着 <strong>C:\test\ConfigureICS.cmd Start 4 5 "Local Area Connection * 3"</strong>

此时，设备已为连接到设备的播发 SSID 的任何客户端启用了 Internet 连接共享。
