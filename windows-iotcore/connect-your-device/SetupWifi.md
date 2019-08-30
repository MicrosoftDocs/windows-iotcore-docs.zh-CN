---
title: 在 Windows 10 IoT 核心版设备上使用 WiFi
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何在 Windows 10 IoT Core 设备上使用、设置和配置 wifi。
keywords: windows iot, wifi, 安装程序, 设备
ms.openlocfilehash: 20f61114323baa60c8052038df68a8c172ce1c95
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169457"
---
# <a name="using-wifi-on-your-windows-10-iot-core-device"></a>在 Windows 10 IoT 核心版设备上使用 WiFi

在使用 USB WLAN 适配器的过程中，WLAN 在 Windows 10 IoT 核心版设备上受支持。 使用 WLAN 可提供有线连接的所有功能，包括 [SSH](../connect-your-device/SSH.md)、[Powershell](../connect-your-device/PowerShell.md)、[Windows Device Portal](../manage-your-device/DevicePortal.md) 以及应用程序调试和部署。

> [!NOTE]
> 插入有线以太网电缆会将 WiFi 替代为默认网络接口。

### <a name="supported-adapters"></a>支持的适配器
可以在[受支持的硬件](../learn-about-hardware/HardwareCompatList.md)页上找到已在 Windows 10 IoT Core 上测试的 WiFi 适配器列表。

### <a name="configuring-wifi"></a>配置 WLAN
若要使用 WiFi，将需要向 Windows 10 IoT 核心版提供 WiFi 网络凭据。 除了介绍如何生成伴随式应用和 WPS 自定义解决方案的文档外, 还提供了几种不同的选项来执行此操作。

## <a name="custom-companion-app--wps-wi-fi-onboarding-samples"></a>自定义辅助应用 & WPS Wi-fi 载入示例

目前, 我们为开发人员提供了许多方法来为其设备构建自定义的 wifi 载入解决方案。 

> | 示例 | 描述 | 优势  |  弊端  |
> |-------------|----------|---------|---------|
> | [辅助应用](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CompanionApp) | 创建可配置设备 Wi-fi 的简单 Xamarin 应用程序。 |  易于使用;IoT 核心的头或无外设;客户端跨平台工作 | 开发人员正在创建自己的协议;要求开发人员实现安全性 |
> | [具有蓝牙 RFCOMM 的 IoT 载入](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding_RFCOMM) | 创建解决方案, 将无外设 IoT 设备配置为使用 Bluetooth RFCOMM 连接到 Wi-fi。  | 在头设备或无外设设备上相关;使用熟悉的技术和概念;不需要 IoT 设备启动 SoftAP;不需要调整防火墙设置 | 需要对客户端和服务器设备提供蓝牙支持;示例仅提供适用于 Windows 10 的客户端应用;服务器应用预定义/硬编码客户端设备的名称。 |
> | [通过 AllJoyn 加入 IoT](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding) | 通过家庭 Wi-fi 网络远程加入无头 IoT 设备。 | 适用于 AllJoyn | 对 AllJoyn 的某些支持已弃用 |
> | 适用于设备的 wi-fi 保护的安装程序 (WPS) Api | 执行 WPS 发现以查询网络支持的 WPS 方法。 | 只需利用[WiFiAdapter GetWpsConfigurationAsync (WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync)和[WiFiAdapter](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync)方法将 wi-fi 设备连接到特定网络即可。 | 你将需要熟悉这些 Api 才能利用它们。仅兼容启用了 WPS 的路由器|

## <a name="headed-options"></a>有外设选项：

### <a name="option-1-startup-configuration"></a>选项 1：启动配置
**先决条件：** Windows 10 IoT 核心版设备需要插入鼠标、键盘、显示器和 USB WiFi 适配器

首次使用受支持的 USB WiFi 适配器启动 Windows 10 IoT 核心版时，将呈现配置屏幕。
在配置屏幕上，选择想要连接到的 WiFi 网络，并提供密码。 单击“连接”以启动连接。

![启动 WLAN 配置屏幕](../media/SetupWiFi/WiFiStartupConfig.png)

### <a name="option-2-default-app-configuration"></a>选项 2：默认应用配置
**先决条件：** Windows 10 IoT 核心版设备需要插入鼠标、键盘、显示器和 USB WiFi 适配器

配置 WiFi 的替代方法是使用默认应用。 可使用此方法在启动设备后配置或修改 WiFi 设置。

1. 单击主页上的齿轮形设置图标
2. 在左侧窗格中选择“网络和 WLAN”
3. 单击要连接到的 WiFi 网络。 在提示时提供密码，然后单击“连接”

![默认应用 WiFi 配置](../media/SetupWiFi/DefaultAppWiFiConfig.png)

## <a name="headless-options"></a>无外设选项：




### <a name="option-1-web-based-configuration"></a>选项 1：基于 Web 的配置
**先决条件：** 设备已需要通过以太网连接到本地网络，并且应插入了 USB WLAN 适配器

如果设备缺少 UI、屏幕或输入设备，仍可通过 [Windows Device Portal](../manage-your-device/DevicePortal.md) 配置该设备。
在 **Windows 10 IoT 核心版仪表板**上，*单击*设备的“在 Device Portal 中打开”图标。

<!-- This content is replicated at en-US/Docs/KitSetupRPI.md -->

1. 输入“Administrator”作为用户名，并提供密码（默认情况下为 p@ssw0rd）
2. 单击左侧窗格中的 "**网络**"
3. 在“可用网络”下，选择要连接到的网络，并提供连接凭据。 单击“连接”以启动连接

![基于 Web 的 WLAN 配置](../media/SetupWiFi/WebBWiFiConfig.png)

<!-- End of Replicated Content -->


### <a name="option-2-connect-using-wifi-profiles"></a>选项 2：使用 WLAN 配置文件进行连接

**先决条件：** 设备已需要通过以太网连接到本地网络，并且插入了 USB WiFi 适配器。 还需要具有 WiFi 功能的 Windows 电脑。

Windows 10 IoT 核心版支持使用无线配置文件设置 WiFi。 有关详细信息和示例，请参阅 [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853)。

1. 将 Windows 电脑连接到所需的无线网络，并使用以下命令创建 WiFi 配置文件 XML 文件：

    * `netsh wlan show profiles` -> 查找刚添加的配置文件名称

    * `netsh wlan export profile name=<your profilename>`。 这会将配置文件导出到某个 XML 文件

2. 打开“文件资源管理器”窗口，并在地址栏中键入 `\\<TARGET_DEVICE>\C$\`，然后点击 Enter。  在此特定情况下，`<TARGET_DEVICE>` 可以是 Windows 10 IoT 核心版设备的名称或 IP 地址：

    ![使用文件资源管理器的 SMB](../media/SetupWifi/smb1.png)

    如果系统提示输入用户名和密码，请使用以下凭据：

        User Name: <TARGET_DEVICE>\Administrator
        Password:  p@ssw0rd

    ![使用文件资源管理器的 SMB](../media/SetupWifi/cred1.png)

> [!NOTE]
> **强烈建议**你更新管理员帐户的默认密码。  请按照[此处](../connect-your-device/PowerShell.md)的说明进行操作。

3. 将导出的 WiFi 配置文件 XML 文件从 Windows 电脑复制到 Windows 10 IoT 核心版设备

4. 通过执行以下命令，使用 [PowerShell](../connect-your-device/PowerShell.md) 连接到设备，并向你的设备添加新的 WLAN 配置文件

    * `netsh wlan add profile filename=<copied XML path>`

    * `netsh wlan show profiles`

5. 通过 netsh，将 Windows 10 IoT 核心版设备连接到无线网络

    * `netsh wlan connect name=<profile name>`

6. 请验证设备是否连接到无线网络并且可访问 Internet

    * `netsh wlan show interfaces`

    * `ipconfig /all`

    * `ping /S <your WiFi adapter ip address> bing.com`


#### <a name="connecting-to-wpa2-psk-personal-networks"></a>连接到 WPA2-PSK 个人网络

如果需要连接到 WPA2-PSK 个人 WiFi 网络，请首先按照上述说明进行操作，但要对 XML 文件作出以下更改。 唯一的区别是，在 Windows 电脑导出 XML 时，它将对密码进行加密。

> [!WARNING] 
> 这会使连接不安全。

从 Windows 电脑导出的配置文件 XML：

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>true</protected>
        <keyMaterial><Your Encrypted password></keyMaterial>
    </sharedKey>


需要在 Windows 10 IoT 核心版上生效的更改：

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial><Your Unencrypted password></keyMaterial>
    </sharedKey>
