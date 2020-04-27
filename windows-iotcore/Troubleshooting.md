---
Description: 排查与开发相关的不同问题。
title: 疑难解答
ms.date: 08/28/2018
ms.topic: article
ms.openlocfilehash: 6118a5a5006d79c65681400de45fb7626f96836d
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2020
ms.locfileid: "75721513"
---
# <a name="troubleshooting"></a><span data-ttu-id="edfed-103">疑难解答</span><span class="sxs-lookup"><span data-stu-id="edfed-103">Troubleshooting</span></span>
<span data-ttu-id="edfed-104">本文包含用户遇到的常见故障排除问题。</span><span class="sxs-lookup"><span data-stu-id="edfed-104">This is an article that contains common troubleshooting issues that people have come across.</span></span> <span data-ttu-id="edfed-105">若要查找特定内容（字词或短语），请使用 Ctrl+F。</span><span class="sxs-lookup"><span data-stu-id="edfed-105">To find something specific, use Ctrl+F to find a word or phrase.</span></span> <span data-ttu-id="edfed-106">想要表达你自己的见解？</span><span class="sxs-lookup"><span data-stu-id="edfed-106">Have any insight you want to add?</span></span> <span data-ttu-id="edfed-107">请针对本文档创建一个 PR，或者在下面提供内容反馈。</span><span class="sxs-lookup"><span data-stu-id="edfed-107">Create a PR for this documentation or provident content feedback below.</span></span>

> [!TIP]
> <span data-ttu-id="edfed-108">若要排查与制造相关的问题，请阅读制造指南中的[故障排除文档](https://docs.microsoft.com/windows-hardware/manufacture/iot/troubleshooting)。</span><span class="sxs-lookup"><span data-stu-id="edfed-108">For troubleshooting issues related to manufacturing, please read the [Troubleshooting doc](https://docs.microsoft.com/windows-hardware/manufacture/iot/troubleshooting) in our manufacturing guide.</span></span>

## <a name="asus-tinkerboard-and-rockchip-support"></a><span data-ttu-id="edfed-109">ASUS Tinkerboard 和 Rockchip 支持</span><span class="sxs-lookup"><span data-stu-id="edfed-109">ASUS Tinkerboard and Rockchip support</span></span>

<span data-ttu-id="edfed-110">虽然我们不正式支持 ASUS Tinkerboard 和 Rockchip，但有时候，Rockchip 可以通过其他的第三方在 Windows 10 IoT 核心版上使用 SoC。</span><span class="sxs-lookup"><span data-stu-id="edfed-110">While the ASUS Tinkerboard and Rockchip are not officially supported by us, there are cases where Rockchip has worked with other third parties to get SoC working on Windows 10 IoT Core.</span></span>

## <a name="issue-when-connecting-a-mbm-device-when-roaming"></a><span data-ttu-id="edfed-111">在漫游时连接 MBM 设备出现问题</span><span class="sxs-lookup"><span data-stu-id="edfed-111">Issue when connecting a MBM device when roaming</span></span>

<span data-ttu-id="edfed-112">在启用漫游时需考虑两个事项：</span><span class="sxs-lookup"><span data-stu-id="edfed-112">There are two things to consider when enabling roaming:</span></span>

1. <span data-ttu-id="edfed-113">profile.xml 用于配置漫游并设置自动连接到手机网络的行为。</span><span class="sxs-lookup"><span data-stu-id="edfed-113">The profile.xml configures roaming and sets the behavior to automatically establish a connection to the cellular network.</span></span>
<span data-ttu-id="edfed-114">若要设置漫游配置文件，请参阅[此文](https://docs.microsoft.com/windows/desktop/mbn/schema-root)。</span><span class="sxs-lookup"><span data-stu-id="edfed-114">To set a profile for roaming please refer to [this article](https://docs.microsoft.com/windows/desktop/mbn/schema-root).</span></span>

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

<span data-ttu-id="edfed-115">若要设置用于自动连接的配置文件，请选择 "auto"：</span><span class="sxs-lookup"><span data-stu-id="edfed-115">To set a profile for automatic connection, select "auto":</span></span>

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

2. <span data-ttu-id="edfed-116">另一因素是，必须满足每个接口的漫游策略。</span><span class="sxs-lookup"><span data-stu-id="edfed-116">Another factor is that the per-interface roaming policy must be satisfied.</span></span> <span data-ttu-id="edfed-117">默认情况下，该策略设置为 FALSE（“仅限家庭运营商”）。</span><span class="sxs-lookup"><span data-stu-id="edfed-117">By default, that policy is set to FALSE ("home carrier only").</span></span> <span data-ttu-id="edfed-118">可以在命令行中通过 `netsh mbn get/set dataroamcontrol.` 对此项进行查询和更改</span><span class="sxs-lookup"><span data-stu-id="edfed-118">This can be queried and changed in command line via `netsh mbn get/set dataroamcontrol.`</span></span>

<span data-ttu-id="edfed-119">示例：</span><span class="sxs-lookup"><span data-stu-id="edfed-119">Example:</span></span>

```
    netsh mbn show dataroamcontrol int=*
    netsh mbn set dataroamcontrol interface=Cellular profileset=all state=all
    netsh mbn set dataroamcontrol help
```

<span data-ttu-id="edfed-120">如果设备在漫游，但漫游策略禁止数据漫游，则可能出现错误 **0x139f (ERROR_INVALID_STATE)** - 在将连接请求发送到 wwansvc 时出错。</span><span class="sxs-lookup"><span data-stu-id="edfed-120">You may get error **0x139f (ERROR_INVALID_STATE)** in the case when the device is roaming but the roaming policy disallows data roaming - error on a connect request sent to wwansvc.</span></span>

## <a name="raspberry-pi-3b-booting-issues"></a><span data-ttu-id="edfed-121">Raspberry Pi 3B+ 启动问题</span><span class="sxs-lookup"><span data-stu-id="edfed-121">Raspberry Pi 3B+ booting issues</span></span>

> [!NOTE]
> <span data-ttu-id="edfed-122">Raspberry Pi 3B+ 的此版本是不受支持的技术预览版。</span><span class="sxs-lookup"><span data-stu-id="edfed-122">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="edfed-123">已完成有限的验证和启用。</span><span class="sxs-lookup"><span data-stu-id="edfed-123">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="edfed-124">若要获得更好的评估体验，或者要将产品商用化，请使用 Raspberry Pi 3B 或者其他带有受支持的 Intel、Qualcomm 或 NXP SoC 的设备。</span><span class="sxs-lookup"><span data-stu-id="edfed-124">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="edfed-125">若要排查 Raspberry Pi 3B+ 的问题，请参阅[此处](https://docs.microsoft.com/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues)的故障排除指南。</span><span class="sxs-lookup"><span data-stu-id="edfed-125">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

<span data-ttu-id="edfed-126">Raspberry Pi 3 的 B+ 型号是 Raspberry Pi 3 系列的最新产品，拥有以 1.4GHz 运行的 64 位四核处理器、2.4GHz 和 5GHz 双频段无线 LAN、蓝牙 4.2/BLE、更快速的以太网，以及通过独立 PoE HA 实现的 PoE 功能。</span><span class="sxs-lookup"><span data-stu-id="edfed-126">The Raspberry Pi 3 Model B+ is the latest product in the Raspberry Pi 3 range, boasting a 64-bit quad core processor running at 1.4GHz, dual-band 2.4GHz and 5GHz wireless LAN, Bluetooth 4.2/BLE, faster Ethernet, and PoE capability via a separate PoE HA.</span></span>

<span data-ttu-id="edfed-127">最近，许多对 Windows 10 IoT 核心版感兴趣的客户遇到一个问题：设备在刷写 Windows 10 IoT 核心版后无法正常启动，但其上的 Raspbian 正常。</span><span class="sxs-lookup"><span data-stu-id="edfed-127">Recently, many customers who are interested in Windows 10 IoT Core encountered a problem where the device could not boot normally after flashing Windows 10 IoT Core, but the Raspbian works fine on it.</span></span> <span data-ttu-id="edfed-128">下面是关于如何排查此启动问题的一些建议。</span><span class="sxs-lookup"><span data-stu-id="edfed-128">The following are some suggestions on how to troubleshoot the boot problem.</span></span>

<span data-ttu-id="edfed-129">此 Insider Preview 映像中存在一些已知的问题。</span><span class="sxs-lookup"><span data-stu-id="edfed-129">There are some known issues in this Insider Preview image.</span></span> <span data-ttu-id="edfed-130">请注意：</span><span class="sxs-lookup"><span data-stu-id="edfed-130">Please note that:</span></span>
* <span data-ttu-id="edfed-131">此映像仅适用于 Raspberry Pi 3B+，不会在 Raspbierry Pi 2 上启动。</span><span class="sxs-lookup"><span data-stu-id="edfed-131">This image is only meant for the Raspberry Pi 3B+ and will not boot on the Raspbierry Pi 2.</span></span>
* <span data-ttu-id="edfed-132">不能在 Windows 10 IoT 核心版上通过 Visual Studio 进行 F5 驱动程序部署。</span><span class="sxs-lookup"><span data-stu-id="edfed-132">F5 driver deployment from Visual Studio does not work on Windows 10 IoT Core.</span></span>
* <span data-ttu-id="edfed-133">板载 Wi-Fi 和蓝牙不能在 Raspberry Pi 3B+ 上使用。</span><span class="sxs-lookup"><span data-stu-id="edfed-133">Onboard Wi-Fi and Bluetooth do not work on the Raspberry Pi 3B+.</span></span>
* <span data-ttu-id="edfed-134">Ft5406 触摸屏驱动程序在 Raspberry Pi 3B+ 上禁用。</span><span class="sxs-lookup"><span data-stu-id="edfed-134">Ft5406 touch screen driver is disabled on the Raspberry Pi 3B+.</span></span>
* <span data-ttu-id="edfed-135">SD 卡活动 LED 禁用。</span><span class="sxs-lookup"><span data-stu-id="edfed-135">SD card activity LED is disabled.</span></span>

<span data-ttu-id="edfed-136">在选择可以与 Windows 10 IoT 核心版配合使用的 SD 卡时，只需满足两个要求。</span><span class="sxs-lookup"><span data-stu-id="edfed-136">There are only two requirements when choosing which SD cards to use with Windows 10 IoT Core.</span></span> <span data-ttu-id="edfed-137">需使用 Class 10 SD 卡，并确保该卡有足够的空间 - 至少 8 GB 的空间。</span><span class="sxs-lookup"><span data-stu-id="edfed-137">You need to use a class 10 SD card and make sure the card has enough space - at least 8 GB of space.</span></span> <span data-ttu-id="edfed-138">有一些 SD 卡经 Microsoft 验证与 Windows 10 IoT 核心版兼容：</span><span class="sxs-lookup"><span data-stu-id="edfed-138">There are a couple of SD cards that have been verified by Microsoft to be compatible with Windows 10 IoT Core:</span></span>
* <span data-ttu-id="edfed-139">Samsung EVO 32 GB Class 10 Micros SDHC 卡</span><span class="sxs-lookup"><span data-stu-id="edfed-139">Samsung EVO 32 GB class 10 Micros SDHC card</span></span>
* <span data-ttu-id="edfed-140">SanDisk Ultra Micro SDHC 16 GB 卡</span><span class="sxs-lookup"><span data-stu-id="edfed-140">SanDisk Ultra Micro SDHC, 16 GB card</span></span>

<span data-ttu-id="edfed-141">通常情况下，需检查 SD 卡是否为假货，或者是否受到损伤或损坏。</span><span class="sxs-lookup"><span data-stu-id="edfed-141">Generally, you need to check if the SD card is fake or if it is damaged or corrupt.</span></span> <span data-ttu-id="edfed-142">许多因素（例如电力不足或拆除不当）都有相同的几率造成 SD 卡受损。</span><span class="sxs-lookup"><span data-stu-id="edfed-142">The SD card is equally prone to corruption due to a variety of factors such as power shortage or improper removal.</span></span> <span data-ttu-id="edfed-143">必须确保内存卡不受损。</span><span class="sxs-lookup"><span data-stu-id="edfed-143">It is important to safeguard your memroy card from damage.</span></span>

<span data-ttu-id="edfed-144">若要将映像刷写到 SD 卡，可以使用 [Windows 10 IoT 核心版仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)。</span><span class="sxs-lookup"><span data-stu-id="edfed-144">To flash your image to a SD card, you can use the [Windows 10 IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard).</span></span> <span data-ttu-id="edfed-145">需在“OS 内部版本”字段中选择“自定义”，然后选择要刷写的 FFU 文件。</span><span class="sxs-lookup"><span data-stu-id="edfed-145">You will need to choose "Custom" in the OS Build field, then select the FFU file to flash.</span></span> 

<span data-ttu-id="edfed-146">查看设备中是否存在硬件故障。</span><span class="sxs-lookup"><span data-stu-id="edfed-146">Check to see if there are any hardware failure in the device.</span></span> <span data-ttu-id="edfed-147">Raspberry Pi 3B+ 板上有两个 LED，与 3B 一样。</span><span class="sxs-lookup"><span data-stu-id="edfed-147">There are two LEDs on the Raspberry Pi 3B+ board, same as the 3B.</span></span> <span data-ttu-id="edfed-148">一个用于 PWR，另一个用于 ACT。</span><span class="sxs-lookup"><span data-stu-id="edfed-148">One is for PWR while another is for ACT.</span></span> <span data-ttu-id="edfed-149">ACT 灯的闪烁次数将决定板是否启动。</span><span class="sxs-lookup"><span data-stu-id="edfed-149">The number of blinks the ACT light makes will determine whether or not your board is booting.</span></span> <span data-ttu-id="edfed-150">在 Raspberry Pi 3B+ 上启动时，在某些阶段 SD 卡活动 LED 不会闪烁。</span><span class="sxs-lookup"><span data-stu-id="edfed-150">The SD card activity LED will not flash during some portions of booting on the Raspberry Pi 3B+.</span></span>

<span data-ttu-id="edfed-151">当设备启动时，如果设备显示等待页面，请耐心等待。</span><span class="sxs-lookup"><span data-stu-id="edfed-151">When the device is booting and the device shows the waiting page, please wait patiently.</span></span> <span data-ttu-id="edfed-152">通常情况下，这最多持续一分钟的时间。</span><span class="sxs-lookup"><span data-stu-id="edfed-152">Generally, this will last up to a minute.</span></span> <span data-ttu-id="edfed-153">但有时候，由于 SD 卡的读写速度慢，可能需要更长的时间。</span><span class="sxs-lookup"><span data-stu-id="edfed-153">But sometimes, due to the SD card read-write speed, it may take longer.</span></span>

<span data-ttu-id="edfed-154">如果设备在使用 Windows 10 IoT 核心版时无法正常启动，可以尝试将 Linux OS（例如 Raspbian）刷写到 SD 卡中，以确定问题是否是硬件导致的。</span><span class="sxs-lookup"><span data-stu-id="edfed-154">If the device can't boot normally with Windows 10 IoT Core, you can try to flash a Linux OS (such as Raspbian) to the SD card to narrow down whether the issue is caused by hardware.</span></span> 

<span data-ttu-id="edfed-155">如果出现“彩虹屏幕”，请进行检查，确保刷写的是[此处](https://www.microsoft.com/en-us/software-download/windowsiot)提供的 3B+ 发行版。</span><span class="sxs-lookup"><span data-stu-id="edfed-155">If you find that you're getting a "rainbow screen", please check to make sure that you flashed the 3B+ release version, available [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="edfed-156">[此处](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3)是社区提交的 3B+ 刷写教程，可以参阅它来验证你的过程。</span><span class="sxs-lookup"><span data-stu-id="edfed-156">You can verify your process with a community-submitted 3B+ flashing tutorial [here](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3).</span></span>

## <a name="serial-port-communication-on-windows-10-iot-core-for-raspberry-pi"></a><span data-ttu-id="edfed-157">适用于 Raspberry Pi 的 Windows 10 IoT 核心版上的串行端口通信</span><span class="sxs-lookup"><span data-stu-id="edfed-157">Serial Port communication on Windows 10 IoT Core for Raspberry Pi</span></span> 

<span data-ttu-id="edfed-158">在 Raspberry Pi 上，硬件 UART 适配器和 USB UART 适配器均可用于应用程序的串行通信。</span><span class="sxs-lookup"><span data-stu-id="edfed-158">On the Raspberry Pi, hardware UART and USB UART adapters both are usable for your application with serial communicaiton.</span></span> <span data-ttu-id="edfed-159">默认情况下，UART 的传输引脚和接收引脚是 GPIO 排针上的引脚 8 和引脚 10。</span><span class="sxs-lookup"><span data-stu-id="edfed-159">By default, the UART transmit and receive pins are pins 8 and 10 on teh GPIO header.</span></span>

![UART 适配器和 USB UART 适配器](media/Troubleshooting/adapters.png)

<span data-ttu-id="edfed-161">可以阅读[此文](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart)，详细了解如何初始化 UART0 并依次执行写入和读取操作。</span><span class="sxs-lookup"><span data-stu-id="edfed-161">You can read [this article](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) to learn more about how to initialize UART0 and perform a write followed by a read.</span></span>

<span data-ttu-id="edfed-162">另外，射频通信 (RFCOMM) 是经典蓝牙的基础串行通信。</span><span class="sxs-lookup"><span data-stu-id="edfed-162">In addition, Radio Frequency Communication (RFCOMM) is the underlying serial communications for classic Bluetooth.</span></span> <span data-ttu-id="edfed-163">请参阅[此 GitHub 示例](https://github.com/djaus2/iotbluetoothserial)，了解如何在 Windows 10 IoT 核心版上运行 UWP 应用，在通过 IoT 设备连接后进行蓝牙串行通信。</span><span class="sxs-lookup"><span data-stu-id="edfed-163">Refer to [this GitHub sample](https://github.com/djaus2/iotbluetoothserial) to learn about running UWP apps on Windows 10 IoT Core to connected over an IoT device with Bluetooth Serial.</span></span>

<span data-ttu-id="edfed-164">如果发现设备不能通过串行端口读/写数据，请按以下步骤排查问题：</span><span class="sxs-lookup"><span data-stu-id="edfed-164">If you encounter that the device cannot read/write data through the serial port, follow the steps below to troubleshoot:</span></span>

1. <span data-ttu-id="edfed-165">通过跳线将 TX 连接到 RX（如下所示），然后运行示例代码，检查应用能否读/写数据。</span><span class="sxs-lookup"><span data-stu-id="edfed-165">Connect the TX to RX with Jumper - shown below - then run the sample code to check if the app can read/write data.</span></span> <span data-ttu-id="edfed-166">如果以上操作不成功，则表明板上的 IC 可能受损。</span><span class="sxs-lookup"><span data-stu-id="edfed-166">If this does not work, the IC on the board may be broken.</span></span>

![在 Raspberry Pi 上将 TX 连接到 RX](media/Troubleshooting/txrx.png)

2. <span data-ttu-id="edfed-168">确保正确配置了 BaudRate、握手和 StopBit。</span><span class="sxs-lookup"><span data-stu-id="edfed-168">Make sure the BaudRate, Handshaking and StopBits are configured correctly.</span></span> <span data-ttu-id="edfed-169">如果要测试的串行端口有完整的 RS232 接口（例如 DB9），请使用 DB 插头，该插头的 RxTx 交叉线通过典型的握手交叉方式进行连接。</span><span class="sxs-lookup"><span data-stu-id="edfed-169">If the serial port to be tested has a complete RS232 interface (e.g. DB9), use a DB plug with the RxTx crossover wires connected with the typical handshaking crossovers.</span></span> <span data-ttu-id="edfed-170">某些 RS232 端口（或 USB 适配器）要求先断言载波检测 (DCD) 和 DCE 就绪 (DSR) 之类的信号，否则无法正常使用。</span><span class="sxs-lookup"><span data-stu-id="edfed-170">Some RS232 ports (or USB adapters) require signals such as Carrier Detect (DCD) and DCE Ready (DSR) to be asserted before they function properly.</span></span>

3. <span data-ttu-id="edfed-171">若要使用基于 Windows 10 IoT 核心版的 USB UART 适配器，则请注意，下面是支持的项目：</span><span class="sxs-lookup"><span data-stu-id="edfed-171">If you want to use USB UART adapters on Windows 10 IoT Core, the following are supported:</span></span>

* <span data-ttu-id="edfed-172">CP2102 USB 2.0</span><span class="sxs-lookup"><span data-stu-id="edfed-172">CP2102 USB 2.0</span></span>
* <span data-ttu-id="edfed-173">TTL 模块串行转换器</span><span class="sxs-lookup"><span data-stu-id="edfed-173">TTL Module Serial Converter</span></span>
* <span data-ttu-id="edfed-174">FTDI</span><span class="sxs-lookup"><span data-stu-id="edfed-174">FTDI</span></span>
* <span data-ttu-id="edfed-175">通用 usbser.sys</span><span class="sxs-lookup"><span data-stu-id="edfed-175">Generic usbser.sys</span></span>

<span data-ttu-id="edfed-176">也可使用 devcon.exe stack \* 和 devcon.exe status\* cmdlet 在 Windows 10 IoT 核心版上检查预期的驱动程序堆栈和驱动程序状态。</span><span class="sxs-lookup"><span data-stu-id="edfed-176">You can also use the devcon.exe stack \* and devcon.exe status\* cmdlet to check the expected drivers stack and drivers status on Windows 10 IoT Core.</span></span>

```
USB\VID_10C4&PID_EA60\0001
    Name: Silicon Labs CP210x USB to UART Bridge
    Setup Class: {4d36e978-e325-11ce-bfc1-08002be10318} Ports
    Controlling service:
        silabser
```
<span data-ttu-id="edfed-177">[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) 是另一项有用的工具，用于排查串行端口问题。</span><span class="sxs-lookup"><span data-stu-id="edfed-177">[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) is another helpful tool to troubleshoot serial port issues.</span></span> <span data-ttu-id="edfed-178">此工具可以枚举端口、给出其易记名称和设备 ID、打开端口、配置设置（即波特率、停止位，等等），以及发送和接收数据。</span><span class="sxs-lookup"><span data-stu-id="edfed-178">This tool can enumerate ports, give you their friendly name and Device ID, open ports, configure settings (i.e. baud rate, stop bits, etc.) and send and receive data.</span></span> 

## <a name="sirep-test-service"></a><span data-ttu-id="edfed-179">Sirep 测试服务</span><span class="sxs-lookup"><span data-stu-id="edfed-179">Sirep Test service</span></span>
<span data-ttu-id="edfed-180">Sirep 测试服务在零售映像中并没有默认启用，即便如此，如果你仍然需要在启动时禁用 Sirep 服务，也可以登录后在自动启动中禁用 Sirep。</span><span class="sxs-lookup"><span data-stu-id="edfed-180">Even though the Sirep Test service is not enabled by default in retail images, in case you still want to disable the Sirep service on startup, you can login and disable Sirep from autostart.</span></span> 

<span data-ttu-id="edfed-181">可以使用以下 PowerShell 命令来这样做，如下所示：</span><span class="sxs-lookup"><span data-stu-id="edfed-181">You can use the following PowerShell commands to do so, as shown below:</span></span>

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

## <a name="tablet-mode"></a><span data-ttu-id="edfed-182">平板模式</span><span class="sxs-lookup"><span data-stu-id="edfed-182">Tablet mode</span></span>

<span data-ttu-id="edfed-183">“平板模式”是仅存在于桌面 shell 上的概念，不适用于 IoT 核心版。</span><span class="sxs-lookup"><span data-stu-id="edfed-183">"Tablet Mode" is a concept that only exist on Desktop shell and doesn’t apply to IoT Core.</span></span> 

<span data-ttu-id="edfed-184">如果设备有支持的硬件（不管是通过 I2C 还是通过 USB HID 触摸进行支持），则应可通过内置型驱动程序自动启用触摸功能。</span><span class="sxs-lookup"><span data-stu-id="edfed-184">If the device have supported hardware (either through I2C or USB HID touch), touch should function automatically using the inbox class drivers.</span></span> <span data-ttu-id="edfed-185">你可以在[此处](https://docs.microsoft.com/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity)阅读有关此问题的详细信息。</span><span class="sxs-lookup"><span data-stu-id="edfed-185">You can read more about this [here](https://docs.microsoft.com/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity).</span></span>


## <a name="yubikey-support"></a><span data-ttu-id="edfed-186">Yubikey 支持</span><span class="sxs-lookup"><span data-stu-id="edfed-186">Yubikey support</span></span>

<span data-ttu-id="edfed-187">Windows 10 IoT 核心版没有智能卡支持。</span><span class="sxs-lookup"><span data-stu-id="edfed-187">Windows 10 IoT Core does not have smart card support.</span></span> <span data-ttu-id="edfed-188">但是，智能卡通常是用于用户标识而非设备标识的设备，因为智能卡受 PIN 的保护，而使用 Yubikey 时只需按一下按钮即可。</span><span class="sxs-lookup"><span data-stu-id="edfed-188">However, smart cards are usually devices used for user identity and not device identity because they are secured with PINs and, in the case of the Yubikey, a button to press.</span></span> <span data-ttu-id="edfed-189">这与 IoT 设备不协调。</span><span class="sxs-lookup"><span data-stu-id="edfed-189">This does not harmonize with an IoT device.</span></span> <span data-ttu-id="edfed-190">若要寻找替代品，则设备上的 TPM 2.0 可能比 Yubikey 或智能卡要好。</span><span class="sxs-lookup"><span data-stu-id="edfed-190">If you're looking for an alternative, a TPM 2.0 on the device may serve better than a Yubikey or smart card.</span></span> <span data-ttu-id="edfed-191">我们有针对 TPM 的完整证书支持，它们用于存储设备和用户证书以及 Azure IoT 访问凭据 (Limpet)。</span><span class="sxs-lookup"><span data-stu-id="edfed-191">We have full certificate support for TPMs and they are meant to store devices as well as user certificates and Azure IoT access credentials (Limpets).</span></span>
