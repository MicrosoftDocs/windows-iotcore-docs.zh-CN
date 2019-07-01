---
author: saraclay
Description: 排查与开发相关的不同问题。
title: 疑难解答
ms.author: saclayt
ms.date: 08/28/18
ms.topic: article
ms.openlocfilehash: 8b93ad987c27e1123d68c4d22148447ccc99e37d
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2019
ms.locfileid: "66491710"
---
# <a name="troubleshooting"></a>疑难解答
本文包含用户遇到的常见故障排除问题。 若要查找特定内容（字词或短语），请使用 Ctrl+F。 想要表达你自己的见解？ 请针对本文档创建一个 PR，或者在下面提供内容反馈。

> [!TIP]
> 若要排查与制造相关的问题，请阅读制造指南中的[故障排除文档](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting)。

## <a name="asus-tinkerboard-and-rockchip-support"></a>ASUS Tinkerboard 和 Rockchip 支持

虽然我们不正式支持 ASUS Tinkerboard 和 Rockchip，但有时候，Rockchip 可以通过其他的第三方在 Windows 10 IoT 核心版上使用 SoC。

## <a name="issue-when-connecting-a-mbm-device-when-roaming"></a>在漫游时连接 MBM 设备出现问题

在启用漫游时需考虑两个事项：

1. profile.xml 用于配置漫游并设置自动连接到手机网络的行为。
若要设置漫游配置文件，请参阅[此文](https://docs.microsoft.com/windows/desktop/mbn/schema-root)。

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

若要设置用于自动连接的配置文件，请选择 "auto"：

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

2. 另一因素是，必须满足每个接口的漫游策略。 默认情况下，该策略设置为 FALSE（“仅限家庭运营商”）。 可以在命令行中通过 `netsh mbn get/set dataroamcontrol.` 对此项进行查询和更改

示例：

```
    netsh mbn show dataroamcontrol int=*
    netsh mbn set dataroamcontrol interface=Cellular profileset=all state=all
    netsh mbn set dataroamcontrol help
```

如果设备在漫游，但漫游策略禁止数据漫游，则可能出现错误 **0x139f (ERROR_INVALID_STATE)** - 在将连接请求发送到 wwansvc 时出错。

## <a name="raspberry-pi-3b-booting-issues"></a>Raspberry Pi 3B+ 启动问题

> [!NOTE]
> Raspberry Pi 3B+ 的此版本是不受支持的技术预览版。 已完成有限的验证和启用。 若要获得更好的评估体验，或者要将产品商用化，请使用 Raspberry Pi 3B 或者其他带有受支持的 Intel、Qualcomm 或 NXP SoC 的设备。 若要排查 Raspberry Pi 3B+ 的问题，请参阅[此处](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues)的故障排除指南。 

Raspberry Pi 3 的 B+ 型号是 Raspberry Pi 3 系列的最新产品，拥有以 1.4GHz 运行的 64 位四核处理器、2.4GHz 和 5GHz 双频段无线 LAN、蓝牙 4.2/BLE、更快速的以太网，以及通过独立 PoE HA 实现的 PoE 功能。

最近，许多对 Windows 10 IoT 核心版感兴趣的客户遇到一个问题：设备在刷写 Windows 10 IoT 核心版后无法正常启动，但其上的 Raspbian 正常。 下面是关于如何排查此启动问题的一些建议。

此 Insider Preview 映像中存在一些已知的问题。 请注意：
* 此映像仅适用于 Raspberry Pi 3B+，不会在 Raspbierry Pi 2 上启动。
* 不能在 Windows 10 IoT 核心版上通过 Visual Studio 进行 F5 驱动程序部署。
* 板载 Wi-Fi 和蓝牙不能在 Raspberry Pi 3B+ 上使用。
* Ft5406 触摸屏驱动程序在 Raspberry Pi 3B+ 上禁用。
* SD 卡活动 LED 禁用。

在选择可以与 Windows 10 IoT 核心版配合使用的 SD 卡时，只需满足两个要求。 需使用 Class 10 SD 卡，并确保该卡有足够的空间 - 至少 8 GB 的空间。 有一些 SD 卡经 Microsoft 验证与 Windows 10 IoT 核心版兼容：
* Samsung EVO 32 GB Class 10 Micros SDHC 卡
* SanDisk Ultra Micro SDHC 16 GB 卡

通常情况下，需检查 SD 卡是否为假货，或者是否受到损伤或损坏。 许多因素（例如电力不足或拆除不当）都有相同的几率造成 SD 卡受损。 必须确保内存卡不受损。

若要将映像刷写到 SD 卡，可以使用 [Windows 10 IoT 核心版仪表板](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard)。 需在“OS 内部版本”字段中选择“自定义”，然后选择要刷写的 FFU 文件。 

查看设备中是否存在硬件故障。 Raspberry Pi 3B+ 板上有两个 LED，与 3B 一样。 一个用于 PWR，另一个用于 ACT。 ACT 灯的闪烁次数将决定板是否启动。 在 Raspberry Pi 3B+ 上启动时，在某些阶段 SD 卡活动 LED 不会闪烁。

当设备启动时，如果设备显示等待页面，请耐心等待。 通常情况下，这最多持续一分钟的时间。 但有时候，由于 SD 卡的读写速度慢，可能需要更长的时间。

如果设备在使用 Windows 10 IoT 核心版时无法正常启动，可以尝试将 Linux OS（例如 Raspbian）刷写到 SD 卡中，以确定问题是否是硬件导致的。 

如果出现“彩虹屏幕”，请进行检查，确保刷写的是[此处](https://www.microsoft.com/en-us/software-download/windowsiot)提供的 3B+ 发行版。 [此处](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3)是社区提交的 3B+ 刷写教程，可以参阅它来验证你的过程。

## <a name="serial-port-communication-on-windows-10-iot-core-for-raspberry-pi"></a>适用于 Raspberry Pi 的 Windows 10 IoT 核心版上的串行端口通信 

在 Raspberry Pi 上，硬件 UART 适配器和 USB UART 适配器均可用于应用程序的串行通信。 默认情况下，UART 的传输引脚和接收引脚是 GPIO 排针上的引脚 8 和引脚 10。

![UART 适配器和 USB UART 适配器](media/Troubleshooting/adapters.png)

可以阅读[此文](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart)，详细了解如何初始化 UART0 并依次执行写入和读取操作。

另外，射频通信 (RFCOMM) 是经典蓝牙的基础串行通信。 请参阅[此 GitHub 示例](https://github.com/djaus2/iotbluetoothserial)，了解如何在 Windows 10 IoT 核心版上运行 UWP 应用，在通过 IoT 设备连接后进行蓝牙串行通信。

如果发现设备不能通过串行端口读/写数据，请按以下步骤排查问题：

1. 通过跳线将 TX 连接到 RX（如下所示），然后运行示例代码，检查应用能否读/写数据。 如果以上操作不成功，则表明板上的 IC 可能受损。

![在 Raspberry Pi 上将 TX 连接到 RX](media/Troubleshooting/txrx.png)

2. 确保正确配置了 BaudRate、握手和 StopBit。 如果要测试的串行端口有完整的 RS232 接口（例如 DB9），请使用 DB 插头，该插头的 RxTx 交叉线通过典型的握手交叉方式进行连接。 某些 RS232 端口（或 USB 适配器）要求先断言载波检测 (DCD) 和 DCE 就绪 (DSR) 之类的信号，否则无法正常使用。

3. 若要使用基于 Windows 10 IoT 核心版的 USB UART 适配器，则请注意，下面是支持的项目：

* CP2102 USB 2.0
* TTL 模块串行转换器
* FTDI
* 通用 usbser.sys

也可使用 devcon.exe stack * 和 devcon.exe status* cmdlet 在 Windows 10 IoT 核心版上检查预期的驱动程序堆栈和驱动程序状态。

```
USB\VID_10C4&PID_EA60\0001
    Name: Silicon Labs CP210x USB to UART Bridge
    Setup Class: {4d36e978-e325-11ce-bfc1-08002be10318} Ports
    Controlling service:
        silabser
```
[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) 是另一项有用的工具，用于排查串行端口问题。 此工具可以枚举端口、给出其易记名称和设备 ID、打开端口、配置设置（即波特率、停止位，等等），以及发送和接收数据。 

## <a name="sirep-test-service"></a>Sirep 测试服务
Sirep 测试服务在零售映像中并没有默认启用，即便如此，如果你仍然需要在启动时禁用 Sirep 服务，也可以登录后在自动启动中禁用 Sirep。 

可以使用以下 PowerShell 命令来这样做，如下所示：

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

## <a name="tablet-mode"></a>平板模式

“平板模式”是仅存在于桌面 shell 上的概念，不适用于 IoT 核心版。 

如果设备有支持的硬件（不管是通过 I2C 还是通过 USB HID 触摸进行支持），则应可通过内置型驱动程序自动启用触摸功能。 你可以在[此处](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity)阅读有关此问题的详细信息。


## <a name="yubikey-support"></a>Yubikey 支持

Windows 10 IoT 核心版没有智能卡支持。 但是，智能卡通常是用于用户标识而非设备标识的设备，因为智能卡受 PIN 的保护，而使用 Yubikey 时只需按一下按钮即可。 这与 IoT 设备不协调。 若要寻找替代品，则设备上的 TPM 2.0 可能比 Yubikey 或智能卡要好。 我们有针对 TPM 的完整证书支持，它们用于存储设备和用户证书以及 Azure IoT 访问凭据 (Limpet)。
