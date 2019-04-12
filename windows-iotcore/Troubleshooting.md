---
author: saraclay
Description: 不同的开发相关问题进行疑难解答。
title: 疑难解答
ms.author: saclayt
ms.date: 08/28/18
ms.topic: article
ms.openlocfilehash: 00c748e4ce06e960dbc2a4250fb3cb279f4d092a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510866"
---
# <a name="troubleshooting"></a><span data-ttu-id="7d797-103">疑难解答</span><span class="sxs-lookup"><span data-stu-id="7d797-103">Troubleshooting</span></span>
<span data-ttu-id="7d797-104">这是包含用户偶然遇到的常见故障排除问题的文章。</span><span class="sxs-lookup"><span data-stu-id="7d797-104">This is an article that contains common troubleshooting issues that people have come across.</span></span> <span data-ttu-id="7d797-105">若要查找某些具体内容，请使用 Ctrl + F 来查找单词或短语。</span><span class="sxs-lookup"><span data-stu-id="7d797-105">To find something specific, use Ctrl+F to find a word or phrase.</span></span> <span data-ttu-id="7d797-106">是否有任何你想要添加的见解？</span><span class="sxs-lookup"><span data-stu-id="7d797-106">Have any insight you want to add?</span></span> <span data-ttu-id="7d797-107">创建此文档或下面 provident 内容反馈的拉取请求。</span><span class="sxs-lookup"><span data-stu-id="7d797-107">Create a PR for this documentation or provident content feedback below.</span></span>

> [!TIP]
> <span data-ttu-id="7d797-108">有关故障排除与生产相关的问题，请阅读[故障排除文档](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting)中我们生产的指南。</span><span class="sxs-lookup"><span data-stu-id="7d797-108">For troubleshooting issues related to manufacturing, please read the [Troubleshooting doc](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting) in our manufacturing guide.</span></span>

## <a name="asus-tinkerboard-and-rockchip-support"></a><span data-ttu-id="7d797-109">ASUS Tinkerboard 和 Rockchip 支持</span><span class="sxs-lookup"><span data-stu-id="7d797-109">ASUS Tinkerboard and Rockchip support</span></span>

<span data-ttu-id="7d797-110">虽然我们不正式支持 ASUS Tinkerboard 和 Rockchip，有 Rockchip 一直从事其他第三方以获取 Windows 10 IoT Core 上使用 SoC 的情况。</span><span class="sxs-lookup"><span data-stu-id="7d797-110">While the ASUS Tinkerboard and Rockchip are not officially supported by us, there are cases where Rockchip has worked with other third parties to get SoC working on Windows 10 IoT Core.</span></span>

## <a name="issue-when-connecting-a-mbm-device-when-roaming"></a><span data-ttu-id="7d797-111">MBM 设备漫游时进行连接时出现的问题</span><span class="sxs-lookup"><span data-stu-id="7d797-111">Issue when connecting a MBM device when roaming</span></span>

<span data-ttu-id="7d797-112">有两个需要时启用漫游，请考虑的事项：</span><span class="sxs-lookup"><span data-stu-id="7d797-112">There are two things to consider when enabling roaming:</span></span>

1. <span data-ttu-id="7d797-113">Profile.xml 配置漫游，并设置以自动建立到移动电话网络连接的行为。</span><span class="sxs-lookup"><span data-stu-id="7d797-113">The profile.xml configures roaming and sets the behavior to automatically establish a connection to the cellular network.</span></span>
<span data-ttu-id="7d797-114">若要设置的配置文件漫游，请参阅[这篇文章](https://docs.microsoft.com/windows/desktop/mbn/schema-root)。</span><span class="sxs-lookup"><span data-stu-id="7d797-114">To set a profile for roaming please refer to [this article](https://docs.microsoft.com/windows/desktop/mbn/schema-root).</span></span>

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

<span data-ttu-id="7d797-115">若要设置自动连接的配置文件，选择"自动":</span><span class="sxs-lookup"><span data-stu-id="7d797-115">To set a profile for automatic connection, select "auto":</span></span>

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

2. <span data-ttu-id="7d797-116">另一个因素是必须满足每个接口漫游策略。</span><span class="sxs-lookup"><span data-stu-id="7d797-116">Another factor is that the per-interface roaming policy must be satisfied.</span></span> <span data-ttu-id="7d797-117">默认情况下，该策略设置为 FALSE （"家庭运营商仅"）。</span><span class="sxs-lookup"><span data-stu-id="7d797-117">By default, that policy is set to FALSE ("home carrier only").</span></span> <span data-ttu-id="7d797-118">这可查询，通过命令行中进行更改</span><span class="sxs-lookup"><span data-stu-id="7d797-118">This can be queried and changed in command line via</span></span> `netsh mbn get/set dataroamcontrol.`

<span data-ttu-id="7d797-119">例如：</span><span class="sxs-lookup"><span data-stu-id="7d797-119">Example:</span></span>

```
    netsh mbn show dataroamcontrol int=*
    netsh mbn set dataroamcontrol interface=Cellular profileset=all state=all
    netsh mbn set dataroamcontrol help
```

<span data-ttu-id="7d797-120">你可能会收到错误**0x139f (ERROR_INVALID_STATE)** 在这种情况时漫游设备但漫游策略不允许数据漫游的错误在连接请求发送到 wwansvc。</span><span class="sxs-lookup"><span data-stu-id="7d797-120">You may get error **0x139f (ERROR_INVALID_STATE)** in the case when the device is roaming but the roaming policy disallows data roaming - error on a connect request sent to wwansvc.</span></span>

## <a name="raspberry-pi-3b-booting-issues"></a><span data-ttu-id="7d797-121">Raspberry Pi 3B + 启动问题</span><span class="sxs-lookup"><span data-stu-id="7d797-121">Raspberry Pi 3B+ booting issues</span></span>

> [!NOTE]
> <span data-ttu-id="7d797-122">此版本中的 Raspberry Pi 3B + 是不受支持的 technical preview。</span><span class="sxs-lookup"><span data-stu-id="7d797-122">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="7d797-123">已完成有限的验证和支持。</span><span class="sxs-lookup"><span data-stu-id="7d797-123">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="7d797-124">为更好地评估体验和对于任何商业产品，请使用 Raspberry Pi 3B 或其他设备使用受支持的 Intel、 Qualcomm 或 NXP Soc。</span><span class="sxs-lookup"><span data-stu-id="7d797-124">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="7d797-125">解决问题的 Raspberry Pi 3B +，请参阅我们的故障排除指南，[此处](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues)。</span><span class="sxs-lookup"><span data-stu-id="7d797-125">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

<span data-ttu-id="7d797-126">Raspberry Pi 3 模型 B + 是在 Raspberry Pi 3 范围内，最新的产品纳入 1.4 GHz、 双外 2.4 GHz 和 5 GHz 无线 LAN、 蓝牙 4.2/BLE，更快地以太网，在运行 64 位四核处理器和通过的单独波 HA 波功能。</span><span class="sxs-lookup"><span data-stu-id="7d797-126">The Raspberry Pi 3 Model B+ is the latest product in the Raspberry Pi 3 range, boasting a 64-bit quad core processor running at 1.4GHz, dual-band 2.4GHz and 5GHz wireless LAN, Bluetooth 4.2/BLE, faster Ethernet, and PoE capability via a separate PoE HA.</span></span>

<span data-ttu-id="7d797-127">最近，许多客户想要在 Windows 10 IoT Core 人员遇到的问题，设备无法刷新 Windows 10 IoT Core 之后, 正常启动，但在其上正常工作的 Raspbian。</span><span class="sxs-lookup"><span data-stu-id="7d797-127">Recently, many customers who are interested in Windows 10 IoT Core encountered a problem where the device could not boot normally after flushing Windows 10 IoT Core, but the Raspbian works fine on it.</span></span> <span data-ttu-id="7d797-128">以下是一些有关如何解决启动问题的建议。</span><span class="sxs-lookup"><span data-stu-id="7d797-128">The following are some suggestions on how to troubleshoot the boot problem.</span></span>

<span data-ttu-id="7d797-129">此 Insider Preview 映像中有一些已知的问题。</span><span class="sxs-lookup"><span data-stu-id="7d797-129">There are some known issues in this Insider Preview image.</span></span> <span data-ttu-id="7d797-130">请注意：</span><span class="sxs-lookup"><span data-stu-id="7d797-130">Please note that:</span></span>
* <span data-ttu-id="7d797-131">此映像仅适用于 Raspberry Pi 3B +，将不会启动 Raspbierry Pi 2 上。</span><span class="sxs-lookup"><span data-stu-id="7d797-131">This image is only meant for the Raspberry Pi 3B+ and will not boot on the Raspbierry Pi 2.</span></span>
* <span data-ttu-id="7d797-132">从 Visual Studio 的 F5 驱动程序部署不适用于 Windows 10 IoT Core。</span><span class="sxs-lookup"><span data-stu-id="7d797-132">F5 driver deployment from Visual Studio does not work on Windows 10 IoT Core.</span></span>
* <span data-ttu-id="7d797-133">要登记的 Wi-fi 和蓝牙不适用于 Raspberry Pi 3B +。</span><span class="sxs-lookup"><span data-stu-id="7d797-133">Onboard Wi-Fi and Bluetooth do not work on the Raspberry Pi 3B+.</span></span>
* <span data-ttu-id="7d797-134">在 Raspberry Pi 3B + 禁用 Ft5406 触摸屏幕驱动程序。</span><span class="sxs-lookup"><span data-stu-id="7d797-134">Ft5406 touch screen driver is disabled on the Raspberry Pi 3B+.</span></span>
* <span data-ttu-id="7d797-135">禁用 SD 卡活动 LED。</span><span class="sxs-lookup"><span data-stu-id="7d797-135">SD card activity LED is disabled.</span></span>

<span data-ttu-id="7d797-136">选择要用于 Windows 10 IoT Core 的 SD 卡时，有只有两个要求。</span><span class="sxs-lookup"><span data-stu-id="7d797-136">There are only two requirements when choosing which SD cards to use with Windows 10 IoT Core.</span></span> <span data-ttu-id="7d797-137">您需要使用类 10 SD 卡并确保卡具有足够的空间-至少 8 GB 的空间。</span><span class="sxs-lookup"><span data-stu-id="7d797-137">You need to use a class 10 SD card and make sure the card has enough space - at least 8 GB of space.</span></span> <span data-ttu-id="7d797-138">有几个已通过 Microsoft 与 Windows 10 IoT 核心版兼容的 SD 卡：</span><span class="sxs-lookup"><span data-stu-id="7d797-138">There are a couple of SD cards that have been verified by Microsoft to be compatible with Windows 10 IoT Core:</span></span>
* <span data-ttu-id="7d797-139">Samsung EVO 32 GB 类 10 Micros SDHC 卡</span><span class="sxs-lookup"><span data-stu-id="7d797-139">Samsung EVO 32 GB class 10 Micros SDHC card</span></span>
* <span data-ttu-id="7d797-140">SanDisk 超高的微 SDHC，16 GB 卡</span><span class="sxs-lookup"><span data-stu-id="7d797-140">SanDisk Ultra Micro SDHC, 16 GB card</span></span>

<span data-ttu-id="7d797-141">通常情况下，您需要检查 SD 卡是假，或者如果它已损坏或已损坏。</span><span class="sxs-lookup"><span data-stu-id="7d797-141">Generally, you need to check if the SD card is fake or if it is damaged or corrupt.</span></span> <span data-ttu-id="7d797-142">SD 卡是由于多种因素，例如 power 不足或不正确删除损坏同样容易。</span><span class="sxs-lookup"><span data-stu-id="7d797-142">The SD card is equally prone to corruption due to a variety of factors such as power shortage or improper removal.</span></span> <span data-ttu-id="7d797-143">请务必保护您免遭损坏的内存卡。</span><span class="sxs-lookup"><span data-stu-id="7d797-143">It is important to safeguard your memroy card from damage.</span></span>

<span data-ttu-id="7d797-144">若要刷写到 SD 卡映像，可以使用[Windows 10 IoT 核心版仪表板](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard)。</span><span class="sxs-lookup"><span data-stu-id="7d797-144">To flash your image to a SD card, you can use the [Windows 10 IoT Core Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard).</span></span> <span data-ttu-id="7d797-145">你将需要在操作系统内部版本字段中，选择"自定义"，然后选择要刷写 FFU 文件。</span><span class="sxs-lookup"><span data-stu-id="7d797-145">You will need to choose "Custom" in the OS Build field, then select the FFU file to flash.</span></span> 

<span data-ttu-id="7d797-146">检查以查看设备中是否有任何硬件故障。</span><span class="sxs-lookup"><span data-stu-id="7d797-146">Check to see if there are any hardware failure in the device.</span></span> <span data-ttu-id="7d797-147">在 Raspberry Pi 3B + 板 3B 相同上有两个 Led。</span><span class="sxs-lookup"><span data-stu-id="7d797-147">There are two LEDs on the Raspberry Pi 3B+ board, same as the 3B.</span></span> <span data-ttu-id="7d797-148">其中一个是电源而另一种是 act。</span><span class="sxs-lookup"><span data-stu-id="7d797-148">One is for PWR while another is for ACT.</span></span> <span data-ttu-id="7d797-149">眨眼浅将使数将确定启动板。</span><span class="sxs-lookup"><span data-stu-id="7d797-149">The number of blinks the ACT light makes will determine whether or not your board is booting.</span></span> <span data-ttu-id="7d797-150">SD 卡活动 LED 将闪烁期间在 Raspberry Pi 3B + 上启动的某些部分。</span><span class="sxs-lookup"><span data-stu-id="7d797-150">The SD card activity LED will not flash during some portions of booting on the Raspberry Pi 3B+.</span></span>

<span data-ttu-id="7d797-151">当启动设备并将设备显示等待页上时，请耐心等待。</span><span class="sxs-lookup"><span data-stu-id="7d797-151">When the device is booting and the device shows the waiting page, please wait patiently.</span></span> <span data-ttu-id="7d797-152">通常情况下，这将持续长达一分钟。</span><span class="sxs-lookup"><span data-stu-id="7d797-152">Generally, this will last up to a minute.</span></span> <span data-ttu-id="7d797-153">但有时，由于 SD 卡读写速度，可能需要花费更长。</span><span class="sxs-lookup"><span data-stu-id="7d797-153">But sometimes, due to the SD card read-write speed, it may take longer.</span></span>

<span data-ttu-id="7d797-154">如果使用 Windows 10 IoT Core 设备无法正常启动，您可以尝试闪烁，Linux OS （如 Raspbian) 到 SD 卡以缩小问题由硬件。</span><span class="sxs-lookup"><span data-stu-id="7d797-154">If the device can't boot normally with Windows 10 IoT Core, you can try to flash a Linux OS (such as Raspbian) to the SD card to narrow down whether the issue is caused by hardware.</span></span> 

<span data-ttu-id="7d797-155">如果您发现您将获得"彩虹屏幕"，请检查以确保闪存 3B + 发行版中，可用[此处](https://www.microsoft.com/en-us/software-download/windowsiot)。</span><span class="sxs-lookup"><span data-stu-id="7d797-155">If you find that you're getting a "rainbow screen", please check to make sure that you flashed the 3B+ release version, available [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="7d797-156">你可以验证您闪烁的教程的过程与社区提交的 3B +[此处](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3)。</span><span class="sxs-lookup"><span data-stu-id="7d797-156">You can verify your process with a community-submitted 3B+ flashing tutorial [here](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3).</span></span>

## <a name="serial-port-communication-on-windows-10-iot-core-for-raspberry-pi"></a><span data-ttu-id="7d797-157">Raspberry Pi 在 Windows 10 IoT Core 上的串行端口通信</span><span class="sxs-lookup"><span data-stu-id="7d797-157">Serial Port communication on Windows 10 IoT Core for Raspberry Pi</span></span> 

<span data-ttu-id="7d797-158">在 Raspberry Pi 硬件 UART 和 USB UART 适配器这两个是可用于将应用程序与串行通信。</span><span class="sxs-lookup"><span data-stu-id="7d797-158">On the Raspberry Pi, hardware UART and USB UART adapters both are usable for your application with serial communicaiton.</span></span> <span data-ttu-id="7d797-159">通过默认情况下，UART 传输和接收 pin 是插针 8 和 10 上的 GPIO 标头。</span><span class="sxs-lookup"><span data-stu-id="7d797-159">By default, the UART transmit and receive pins are pins 8 and 10 on teh GPIO header.</span></span>

![UART 和 USB UART 适配器](media/Troubleshooting/adapters.png)

<span data-ttu-id="7d797-161">可以读取[这篇文章](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart)若要了解有关如何初始化 UART0 和执行读取和写入的详细信息。</span><span class="sxs-lookup"><span data-stu-id="7d797-161">You can read [this article](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) to learn more about how to initialize UART0 and perform a write followed by a read.</span></span>

<span data-ttu-id="7d797-162">此外，射频通信 (RFCOMM) 是对经典蓝牙基础串行通信。</span><span class="sxs-lookup"><span data-stu-id="7d797-162">In addition, Radio Frequency Communication (RFCOMM) is the underlying serial communications for classic Bluetooth.</span></span> <span data-ttu-id="7d797-163">请参阅[此 GitHub 示例](https://github.com/djaus2/iotbluetoothserial)，了解如何运行 UWP 应用在 Windows 10 IoT Core 上连接到对 IoT 设备蓝牙序列号。</span><span class="sxs-lookup"><span data-stu-id="7d797-163">Refer to [this GitHub sample](https://github.com/djaus2/iotbluetoothserial) to learn about running UWP apps on Windows 10 IoT Core to connected over an IoT device with Bluetooth Serial.</span></span>

<span data-ttu-id="7d797-164">如果你遇到的设备不能读取/写入的数据通过串行端口，请执行以下步骤来进行故障排除：</span><span class="sxs-lookup"><span data-stu-id="7d797-164">If you encounter that the device cannot read/write data through the serial port, follow the steps below to troubleshoot:</span></span>

1. <span data-ttu-id="7d797-165">TX 连接到具有跳线--如下所示的 RX，然后运行示例代码以检查如果应用程序可以读取/写入数据。</span><span class="sxs-lookup"><span data-stu-id="7d797-165">Connect the TX to RX with Jumper - shown below - then run the sample code to check if the app can read/write data.</span></span> <span data-ttu-id="7d797-166">如果这不起作用，看板上的 IC 可能被破坏。</span><span class="sxs-lookup"><span data-stu-id="7d797-166">If this does not work, the IC on the board may be broken.</span></span>

![到 Raspberry Pi 上的 RX TX](media/Troubleshooting/txrx.png)

2. <span data-ttu-id="7d797-168">请确保正确配置了 BaudRate、 握手和 StopBits。</span><span class="sxs-lookup"><span data-stu-id="7d797-168">Make sure the BaudRate, Handshaking and StopBits are configured correctly.</span></span> <span data-ttu-id="7d797-169">如果要测试的串行端口具有完整 RS232 接口 (例如 DB9)，使用 RxTx 交叉电线连接使用典型握手 crossovers DB 插件。</span><span class="sxs-lookup"><span data-stu-id="7d797-169">If the serial port to be tested has a complete RS232 interface (e.g. DB9), use a DB plug with the RxTx crossover wires connected with the typical handshaking crossovers.</span></span> <span data-ttu-id="7d797-170">某些 RS232 端口 （或 USB 适配器） 需要如运营商检测 (DCD) 和 DCE 就绪 (DSR) 之前它们正常运行要断言的信号。</span><span class="sxs-lookup"><span data-stu-id="7d797-170">Some RS232 ports (or USB adapters) require signals such as Carrier Detect (DCD) and DCE Ready (DSR) to be asserted before they function properly.</span></span>

3. <span data-ttu-id="7d797-171">如果你想要在 Windows 10 IoT Core 上使用 USB UART 适配器，支持以下各项：</span><span class="sxs-lookup"><span data-stu-id="7d797-171">If you want to use USB UART adapters on Windows 10 IoT Core, the following are supported:</span></span>

* <span data-ttu-id="7d797-172">CP2102 USB 2.0</span><span class="sxs-lookup"><span data-stu-id="7d797-172">CP2102 USB 2.0</span></span>
* <span data-ttu-id="7d797-173">TTL 模块串行转换器</span><span class="sxs-lookup"><span data-stu-id="7d797-173">TTL Module Serial Converter</span></span>
* <span data-ttu-id="7d797-174">FTDI</span><span class="sxs-lookup"><span data-stu-id="7d797-174">FTDI</span></span>
* <span data-ttu-id="7d797-175">泛型 usbser.sys</span><span class="sxs-lookup"><span data-stu-id="7d797-175">Generic usbser.sys</span></span>

<span data-ttu-id="7d797-176">此外可以使用 devcon.exe 堆栈 \* 和 devcon.exe 状态 \* cmdlet 进行检查，预期的驱动程序堆栈和 Windows 10 IoT Core 上的驱动程序状态。</span><span class="sxs-lookup"><span data-stu-id="7d797-176">You can also use the devcon.exe stack \* and devcon.exe status\* cmdlet to check the expected drivers stack and drivers status on Windows 10 IoT Core.</span></span>

```
USB\VID_10C4&PID_EA60\0001
    Name: Silicon Labs CP210x USB to UART Bridge
    Setup Class: {4d36e978-e325-11ce-bfc1-08002be10318} Ports
    Controlling service:
        silabser
```
<span data-ttu-id="7d797-177">[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm)是另一个串行端口的问题进行疑难解答的有用工具。</span><span class="sxs-lookup"><span data-stu-id="7d797-177">[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) is another helpful tool to troubleshoot serial port issues.</span></span> <span data-ttu-id="7d797-178">此工具可以枚举端口，为您提供其友好名称和设备 ID、 打开端口，配置设置 （即波特率、 停止位等） 并发送和接收数据。</span><span class="sxs-lookup"><span data-stu-id="7d797-178">This tool can enumerate ports, give you their friendly name and Device ID, open ports, configure settings (i.e. baud rate, stop bits, etc.) and send and receive data.</span></span> 

## <a name="sirep-test-service"></a><span data-ttu-id="7d797-179">Sirep 测试服务</span><span class="sxs-lookup"><span data-stu-id="7d797-179">Sirep Test service</span></span>
<span data-ttu-id="7d797-180">即使在零售映像中，默认情况下未启用 Sirep 测试服务，以防你仍想要禁用 Sirep 服务在启动时，可以登录并禁用 Sirep 从自动启动。</span><span class="sxs-lookup"><span data-stu-id="7d797-180">Even though the Sirep Test service is not enabled by default in retail images, in case you still want to disable the Sirep service on startup, you can login and disable Sirep from autostart.</span></span> 

<span data-ttu-id="7d797-181">可以使用以下 PowerShell 命令来执行此操作，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7d797-181">You can use the following PowerShell commands to do so, as shown below:</span></span>

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

## <a name="tablet-mode"></a><span data-ttu-id="7d797-182">平板电脑模式</span><span class="sxs-lookup"><span data-stu-id="7d797-182">Tablet mode</span></span>

<span data-ttu-id="7d797-183">"平板电脑模式"是一个仅存在于桌面外壳程序的概念并不能应用于 IoT Core。</span><span class="sxs-lookup"><span data-stu-id="7d797-183">"Tablet Mode" is a concept that only exist on Desktop shell and doesn’t apply to IoT Core.</span></span> 

<span data-ttu-id="7d797-184">如果设备有支持的硬件 （或者通过 I2C 或 USB HID 触摸），触摸应正常自动使用收件箱的类驱动程序。</span><span class="sxs-lookup"><span data-stu-id="7d797-184">If the device have supported hardware (either through I2C or USB HID touch), touch should function automatically using the inbox class drivers.</span></span> <span data-ttu-id="7d797-185">你可以在[此处](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity)阅读有关此问题的详细信息。</span><span class="sxs-lookup"><span data-stu-id="7d797-185">You can read more about this [here](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity).</span></span>


## <a name="yubikey-support"></a><span data-ttu-id="7d797-186">Yubikey 支持</span><span class="sxs-lookup"><span data-stu-id="7d797-186">Yubikey support</span></span>

<span data-ttu-id="7d797-187">Windows 10 IoT 核心版不具有智能卡支持。</span><span class="sxs-lookup"><span data-stu-id="7d797-187">Windows 10 IoT Core does not have smart card support.</span></span> <span data-ttu-id="7d797-188">但是，智能卡通常是因为它们安全的 Pin，然后在 Yubikey，若要按一个按钮的情况下用于用户标识而不是设备标识设备。</span><span class="sxs-lookup"><span data-stu-id="7d797-188">However, smart cards are usually devices used for user identity and not device identity because they are secured with PINs and, in the case of the Yubikey, a button to press.</span></span> <span data-ttu-id="7d797-189">这不会使用 IoT 设备不协调。</span><span class="sxs-lookup"><span data-stu-id="7d797-189">This does not harmonize with an IoT device.</span></span> <span data-ttu-id="7d797-190">如果您正在寻找一种替代方法，TPM 2.0 设备上可能会提供优于 Yubikey 或智能卡。</span><span class="sxs-lookup"><span data-stu-id="7d797-190">If you're looking for an alternative, a TPM 2.0 on the device may serve better than a Yubikey or smart card.</span></span> <span data-ttu-id="7d797-191">我们提供完整的证书支持的 Tpm 和它们专门用于存储设备和用户证书和 Azure IoT 访问凭据 (Limpets)。</span><span class="sxs-lookup"><span data-stu-id="7d797-191">We have full certificate support for TPMs and they are meant to store devices as well as user certificates and Azure IoT access credentials (Limpets).</span></span>
