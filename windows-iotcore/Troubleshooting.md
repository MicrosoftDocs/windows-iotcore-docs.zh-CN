---
author: saraclay
Description: 不同的开发相关问题进行疑难解答。
title: 疑难解答
ms.author: saclayt
ms.date: 08/28/18
ms.topic: article
ms.openlocfilehash: 8b93ad987c27e1123d68c4d22148447ccc99e37d
ms.sourcegitcommit: 2e7e9555fe71ca60b5f41dbf06051a50520a368a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2019
ms.locfileid: "66491710"
---
# <a name="troubleshooting"></a>疑难解答
这是包含用户偶然遇到的常见故障排除问题的文章。 若要查找某些具体内容，请使用 Ctrl + F 来查找单词或短语。 是否有任何你想要添加的见解？ 创建此文档或下面 provident 内容反馈的拉取请求。

> [!TIP]
> 有关故障排除与生产相关的问题，请阅读[故障排除文档](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting)中我们生产的指南。

## <a name="asus-tinkerboard-and-rockchip-support"></a>ASUS Tinkerboard 和 Rockchip 支持

虽然我们不正式支持 ASUS Tinkerboard 和 Rockchip，有 Rockchip 一直从事其他第三方以获取 Windows 10 IoT Core 上使用 SoC 的情况。

## <a name="issue-when-connecting-a-mbm-device-when-roaming"></a>MBM 设备漫游时进行连接时出现的问题

有两个需要时启用漫游，请考虑的事项：

1. Profile.xml 配置漫游，并设置以自动建立到移动电话网络连接的行为。
若要设置的配置文件漫游，请参阅[这篇文章](https://docs.microsoft.com/windows/desktop/mbn/schema-root)。

```
  <!-- applicability to any combination of home carrier, partner MOs and non-partner MOs, except for HomeAndNonPartner -->
  <xs:simpleType name="roamApplicabilityType">
    <xs:restriction base="xs:token">
       <xs:enumeration value="NonPartnerOnly"/>
       <xs:enumeration value="PartnerOnly"/>
       <xs:enumeration value="HomeOnly"/>
       <xs:enumeration value="HomeAndPartner"/>
       <xs:enumeration value="PartnerAndNonpartner"/>
       <xs:enumeration value="AllRoaming"/>
    </xs:restriction>
  </xs:simpleType>
  
  <xs:simpleType name="roamControlType">
    <xs:restriction base="xs:token">
       <xs:enumeration value="AllRoamAllowed"/>
       <xs:enumeration value="PartnerRoamAllowed"/>
       <xs:enumeration value="NoRoamAllowed"/>
    </xs:restriction>
  </xs:simpleType>
``` 

若要设置自动连接的配置文件，选择"自动":

```  
<!-- Connection Mode, default is "manual" -->
    <xs:element name="ConnectionMode" minOccurs="0">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <!-- manual connect always -->
          <xs:enumeration value="manual" />
          <!-- auto connect always -->
          <xs:enumeration value="auto" />
          <!-- auto connect when not roaming -->
          <xs:enumeration value="auto-home"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

2. 另一个因素是必须满足每个接口漫游策略。 默认情况下，该策略设置为 FALSE （"家庭运营商仅"）。 这可查询，通过命令行中进行更改 `netsh mbn get/set dataroamcontrol.`

例如：

```
    netsh mbn show dataroamcontrol int=*
    netsh mbn set dataroamcontrol interface=Cellular profileset=all state=all
    netsh mbn set dataroamcontrol help
```

你可能会收到错误**0x139f (ERROR_INVALID_STATE)** 在这种情况时漫游设备但漫游策略不允许数据漫游的错误在连接请求发送到 wwansvc。

## <a name="raspberry-pi-3b-booting-issues"></a>Raspberry Pi 3B + 启动问题

> [!NOTE]
> 此版本中的 Raspberry Pi 3B + 是不受支持的 technical preview。 已完成有限的验证和支持。 为更好地评估体验和对于任何商业产品，请使用 Raspberry Pi 3B 或其他设备使用受支持的 Intel、 Qualcomm 或 NXP Soc。 解决问题的 Raspberry Pi 3B +，请参阅我们的故障排除指南，[此处](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues)。 

Raspberry Pi 3 模型 B + 是在 Raspberry Pi 3 范围内，最新的产品纳入 1.4 GHz、 双外 2.4 GHz 和 5 GHz 无线 LAN、 蓝牙 4.2/BLE，更快地以太网，在运行 64 位四核处理器和通过的单独波 HA 波功能。

最近，许多客户想要在 Windows 10 IoT Core 人员遇到的问题，设备无法正常情况下刷新后无法启动 Windows 10 IoT 核心版，但在其上正常工作 Raspbian。 以下是一些有关如何解决启动问题的建议。

此 Insider Preview 映像中有一些已知的问题。 请注意：
* 此映像仅适用于 Raspberry Pi 3B +，将不会启动 Raspbierry Pi 2 上。
* 从 Visual Studio 的 F5 驱动程序部署不适用于 Windows 10 IoT Core。
* 要登记的 Wi-fi 和蓝牙不适用于 Raspberry Pi 3B +。
* 在 Raspberry Pi 3B + 禁用 Ft5406 触摸屏幕驱动程序。
* 禁用 SD 卡活动 LED。

选择要用于 Windows 10 IoT Core 的 SD 卡时，有只有两个要求。 您需要使用类 10 SD 卡并确保卡具有足够的空间-至少 8 GB 的空间。 有几个已通过 Microsoft 与 Windows 10 IoT 核心版兼容的 SD 卡：
* Samsung EVO 32 GB 类 10 Micros SDHC 卡
* SanDisk 超高的微 SDHC，16 GB 卡

通常情况下，您需要检查 SD 卡是假，或者如果它已损坏或已损坏。 SD 卡是由于多种因素，例如 power 不足或不正确删除损坏同样容易。 请务必保护您免遭损坏的内存卡。

若要刷写到 SD 卡映像，可以使用[Windows 10 IoT 核心版仪表板](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard)。 你将需要在操作系统内部版本字段中，选择"自定义"，然后选择要刷写 FFU 文件。 

检查以查看设备中是否有任何硬件故障。 在 Raspberry Pi 3B + 板 3B 相同上有两个 Led。 其中一个是电源而另一种是 act。 眨眼浅将使数将确定启动板。 SD 卡活动 LED 将闪烁期间在 Raspberry Pi 3B + 上启动的某些部分。

当启动设备并将设备显示等待页上时，请耐心等待。 通常情况下，这将持续长达一分钟。 但有时，由于 SD 卡读写速度，可能需要花费更长。

如果使用 Windows 10 IoT Core 设备无法正常启动，您可以尝试闪烁，Linux OS （如 Raspbian) 到 SD 卡以缩小问题由硬件。 

如果您发现您将获得"彩虹屏幕"，请检查以确保闪存 3B + 发行版中，可用[此处](https://www.microsoft.com/en-us/software-download/windowsiot)。 你可以验证您闪烁的教程的过程与社区提交的 3B +[此处](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3)。

## <a name="serial-port-communication-on-windows-10-iot-core-for-raspberry-pi"></a>Raspberry Pi 在 Windows 10 IoT Core 上的串行端口通信 

在 Raspberry Pi 硬件 UART 和 USB UART 适配器这两个是可用于将应用程序与串行通信。 通过默认情况下，UART 传输和接收 pin 是插针 8 和 10 上的 GPIO 标头。

![UART 和 USB UART 适配器](media/Troubleshooting/adapters.png)

可以读取[这篇文章](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart)若要了解有关如何初始化 UART0 和执行读取和写入的详细信息。

此外，射频通信 (RFCOMM) 是对经典蓝牙基础串行通信。 请参阅[此 GitHub 示例](https://github.com/djaus2/iotbluetoothserial)，了解如何运行 UWP 应用在 Windows 10 IoT Core 上连接到对 IoT 设备蓝牙序列号。

如果你遇到的设备不能读取/写入的数据通过串行端口，请执行以下步骤来进行故障排除：

1. TX 连接到具有跳线--如下所示的 RX，然后运行示例代码以检查如果应用程序可以读取/写入数据。 如果这不起作用，看板上的 IC 可能被破坏。

![到 Raspberry Pi 上的 RX TX](media/Troubleshooting/txrx.png)

2. 请确保正确配置了 BaudRate、 握手和 StopBits。 如果要测试的串行端口具有完整 RS232 接口 (例如 DB9)，使用 RxTx 交叉电线连接使用典型握手 crossovers DB 插件。 某些 RS232 端口 （或 USB 适配器） 需要如运营商检测 (DCD) 和 DCE 就绪 (DSR) 之前它们正常运行要断言的信号。

3. 如果你想要在 Windows 10 IoT Core 上使用 USB UART 适配器，支持以下各项：

* CP2102 USB 2.0
* TTL 模块串行转换器
* FTDI
* 泛型 usbser.sys

此外可以使用 devcon.exe 堆栈 * 和 devcon.exe 状态 * cmdlet 进行检查，预期的驱动程序堆栈和 Windows 10 IoT Core 上的驱动程序状态。

```
USB\VID_10C4&PID_EA60\0001
    Name: Silicon Labs CP210x USB to UART Bridge
    Setup Class: {4d36e978-e325-11ce-bfc1-08002be10318} Ports
    Controlling service:
        silabser
```
[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm)是另一个串行端口的问题进行疑难解答的有用工具。 此工具可以枚举端口，为您提供其友好名称和设备 ID、 打开端口，配置设置 （即波特率、 停止位等） 并发送和接收数据。 

## <a name="sirep-test-service"></a>Sirep 测试服务
即使在零售映像中，默认情况下未启用 Sirep 测试服务，以防你仍想要禁用 Sirep 服务在启动时，可以登录并禁用 Sirep 从自动启动。 

可以使用以下 PowerShell 命令来执行此操作，如下所示：

```
administrator@MINWINPC C:\Data\Users\administrator>sc stop TestSirepSvc

SERVICE_NAME: TestSirepSvc
       TYPE               : 20  WIN32_SHARE_PROCESS
        STATE              : 3  STOP_PENDING
                                (STOPPABLE, NOT_PAUSABLE, ACCEPTS_PRESHUTDOWN)
        WIN32_EXIT_CODE    : 0  (0x0)
        SERVICE_EXIT_CODE  : 0  (0x0)
        CHECKPOINT         : 0x4
        WAIT_HINT          : 0x1770

administrator@MINWINPC C:\Data\Users\administrator>sc query TestSirepSvc

SERVICE_NAME: TestSirepSvc
        TYPE               : 20  WIN32_SHARE_PROCESS
        STATE              : 1  STOPPED
        WIN32_EXIT_CODE    : 0  (0x0)
        SERVICE_EXIT_CODE  : 0  (0x0)
        CHECKPOINT         : 0x0
        WAIT_HINT          : 0x0

administrator@MINWINPC C:\Data\Users\administrator>sc config TestSirepSvc start=disabled
[SC] ChangeServiceConfig SUCCESS
```

## <a name="tablet-mode"></a>平板电脑模式

"平板电脑模式"是一个仅存在于桌面外壳程序的概念并不能应用于 IoT Core。 

如果设备有支持的硬件 （或者通过 I2C 或 USB HID 触摸），触摸应正常自动使用收件箱的类驱动程序。 你可以在[此处](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity)阅读有关此问题的详细信息。


## <a name="yubikey-support"></a>Yubikey 支持

Windows 10 IoT 核心版不具有智能卡支持。 但是，智能卡通常是因为它们安全的 Pin，然后在 Yubikey，若要按一个按钮的情况下用于用户标识而不是设备标识设备。 这不会使用 IoT 设备不协调。 如果您正在寻找一种替代方法，TPM 2.0 设备上可能会提供优于 Yubikey 或智能卡。 我们提供完整的证书支持的 Tpm 和它们专门用于存储设备和用户证书和 Azure IoT 访问凭据 (Limpets)。
