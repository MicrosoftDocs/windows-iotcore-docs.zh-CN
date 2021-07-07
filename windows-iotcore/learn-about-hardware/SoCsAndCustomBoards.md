---
title: Windows 10 IoT 核心版的 soc 和自定义 Boards
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解各种建议的板和社区设备的硬件功能。
keywords: windows iot，开发设备，板，SOC，SOM，芯片上的系统，Raspberry Pi 2，Raspberry Pi 3，Minnowboard Max，DragonBoard
ms.openlocfilehash: 8a9500c2e12180e2e479d63a6ef6fd3002e8aa49
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228753"
---
# <a name="socs-and-custom-boards"></a>SoC 和自定义板

## <a name="microsoft-enabled-socs"></a>支持 Microsoft 的 Soc

Microsoft 与 Broadcom、Intel、NXP 和 Qualcomm 一起工作，验证对芯片 (soc) 上的多个供应商系统的 Windows 10 IoT 核心版支持。 这些支持 IoT 核心的 Soc 在数百个不同的设备中使用，你可以使用它们来原型和商业化你的想法。

| Broadcom | Intel | Qualcomm | NXP |
|----------|-------|----------|-----|
| BCM2837 | [Intel® Atom®处理器 E3900 系列 (Apollo Lake) ](https://ark.intel.com/products/codename/80644/#@embedded)                                | [Snapdragon 410 (APQ8016) ](https://www.qualcomm.com/products/snapdragon/processors/410) | [i.MX 6 系列](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/iotnxp) |
| BCM2836 | [Intel®赛扬® processor N3350 (Apollo Lake) ](https://ark.intel.com/products/codename/80644/#@embedded)                                    | [Snapdragon 212 (APQ8009) ](https://www.qualcomm.com/products/snapdragon/processors/212) | [i.MX 7 系列](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/iotnxp)     |
|         | [Intel®奔腾® processor N4200 platform (Apollo Lake) ](https://ark.intel.com/products/codename/80644/#@embedded)                           |                                                                                         | [i.MX 8 分钟和8分钟微型系列](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/iotnxp) |
|         | [Intel®奔腾®和赛扬® Processor N3000 系列 (Braswell) ](http://ark.intel.com/products/codename/66094/#@embedded)                    |                                                                                         |      |
|         | [Intel® Atom® x5-E8000 处理器 (Braswell) ](http://ark.intel.com/products/codename/66094/#@embedded)                                        |                                                                                         |  |
|         | [Intel® Atom® x5-Z8350 处理器 (挑拣轨迹) ](https://ark.intel.com/products/93361/Intel-Atom-x5-Z8350-Processor-2M-Cache-up-to-1_92-GHz) |                                                                                         |     |
|         | [Intel® Atom®处理器 E3800 产品系列 (托架踪迹-I) ](http://ark.intel.com/products/codename/55844/#@Embedded)                     |                                                                                         |  |
|         | [Intel®奔腾®和赛扬®处理器 N 和 J 系列 (托架踪迹-M/D) ](http://ark.intel.com/products/codename/55844/)                     |                                                                                         |       |

选择采用的 SoC 将取决于注意事项，如性能要求、电源配置文件、成本、物理连接选项、长期支持和操作条件。

你还需要决定是要使用现成的板还是设备，使用模块 (SoM) 和自定义运营商板上的系统生成自定义设备，还是构建完整的自定义板。 成本和自定义的程度是此决定的关键因素，这两者通常在你进一步自定义时增加。

## <a name="windows-10-iot-core-features-by-processor-family"></a>Windows 10 IoT 核心版按处理器系列的功能

> [!NOTE]
> 此列表考虑非商业公共预览版中的处理器。

为了帮助你为设备选择正确的平台，下表显示了具有 Windows 10 IoT 核心版的处理器系列支持的功能。 Windows 10 IoT 核心版中支持下面列出的所有功能，但某些 soc 可能未包含在其设计中的特定 IP，这种情况下表示为 "N/A"。 在这种情况下，可以将第三方解决方案合并到设计中，以提供所需的功能。  在有限的情况下，如果在处理器上未实现 Windows 10 IoT 核心版功能，该项将留空。

> | Feature | Intel  |  Qualcomm  | NXP MX6 | NXP MX7 | NXP MX8M | Broadcom |
> |----|--------|------------|-----------|-----------|------------|----------|
> | 音频 | x | x | x | x | x | x |
> | GPIO | x | x | x | x | x | x |
> | I2C | x | x | x | x | x | x |
> | 以太网 | x | 空值 | x | x | x | x |
> | SPI | x | x | x | x | x | x |
> | 显示 | x | x | x | x | x | x |
> | UART | x | x | x | x | x | x |
> | USB | x | x | x | x | x | x |
> | PCIe | x | 空值 | x | 正在开发 | 正在开发 | 空值 |
> |MIPI-CSI | 空值 | x | 空值 | 空值 | 空值 | 空值 |
> | 图形/视频 | x | x | 软件呈现 | 软件呈现 | 软件呈现 | 软件呈现 |
> | GPS | 空值 | x | 空值 | 空值 | 空值 | 空值 |
> | Wi-fi/BT | 空值 | x | 空值 | 空值 | 空值 | 空值 |
> | 可信 i/o | 空值 | 空值 | x | x | x | 空值 |
> | 处理器电源管理 |  | x | x | x | 正在开发 | |
> | TPM | x | x | x | x | x | 空值 |
> | 安全启动 | x | x | 正在开发 | 正在开发 | 正在开发 | |
> | 休眠 | x | | | | | |
> | PWM | x | 空值 | x | x | x | |
> | JTAG | x | 空值 | x | x | x | |
> | eMMC | x | x | x | x | x | |
> | SDHC | x | x | x | x | x | x |

## <a name="customized-boards"></a>自定义板

如果离架设备的外形规格包含适用于你的方案的连接选项，则通常是最具成本效益和时间的选择。  

对于大多数人而言，开发完整的自定义板可在产品预计在超过数十甚至几百个单位的卷中销售时发挥作用。 对于较小的卷，使用 SoM 并设计自定义电信板，而不是设计全新的板，可以显著降低成本和上市时间，并简化软件开发和集成。

每个平台都具有在实现过程中需要注意的独特的特点。  下面是有关如何开始的一些建议。 尽管有很多公司在 Windows 10 IoT 核心版上构建，但下面列出了一些已获经验证使用 Windows 10 IoT 核心版的人员：

* __[Raspberry Pi](#raspberry-pi-derived-custom-design)__
* __[Intel](#intel-based-custom-design)__
* __[Qualcomm](#qualcomm-dragonboard-410c-apq8016-based-custom-design)__
* __[NXP](#nxp-preview)__

*如果你是 SoM 提供商或 ODM，并且想要添加到下面的列表中，请向发送电子邮件 [winiotsomhelp@microsoft.com](mailto:winiotsomhelp@microsoft.com) 或直接编辑此页面并提交拉取请求。*

*此处所列的许多公司都很大且复杂。 如果你遇到问题，请发送电子邮件， [winiotsomhelp@microsoft.com](mailto:winiotsomhelp@microsoft.com) 我们会尽力将你连接到正确的人员。*

### <a name="raspberry-pi-derived-custom-design"></a>**Raspberry Pi-派生自定义设计**

[元素 14](https://www.element14.com/community/docs/DOC-76955/l/raspberry-pi-customization-service) 提供适用于 Raspberry Pi 的板自定义服务，以允许您添加或删除连接选项。 如果还需要对 BSP 进行自定义，可以[在 GitHub 上利用开源 BSP 代码](https://github.com/ms-iot/rpi-iotcore)。

### <a name="intel-based-custom-design"></a>**基于 Intel 的自定义设计**

适用于 Windows 的[经验丰富的经验丰富的 Intel 设备构建](https://solutionsdirectory.intel.com/solutions-directory/processors/278/processors/309/processors/402/processors/782/processors/788/processors/1103/processors/1107/processors/1110/processors/1175/processors/1344/processors/1348/processors/1349)群体。 与更常见的 pc 相比，设计用于运行 Windows 10 IoT 核心版的 Intel 设备具有几个不同之处：

1. 如果需要提供用户模式通用 Windows 平台 (UWP) API 访问 I2C、GPIO 和 SPI 等简单总线，需要确保 UEFI 固件中的 ACPI 表包含 RHProxy 的相应条目。 有关详细信息，请参阅 [用户模式访问权限](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) 。
2. 必须确保固件中的 SMBIOS 包含 [OEM 许可证要求](https://docs.microsoft.com/windows/iot-core/commercialize-your-device/oemlicenserequirements)中所列的信息。

如果你正在构建自己的板，请联系你的 BIOS 供应商，以了解有关 ACPI 或 SMBIOS 更改的指导。

#### <a name="experienced-partners"></a>*经验丰富的合作伙伴*

* [Aaeon](http://www.aaeon.com/en/)
* [Advantech](http://www.advantech.com/) - buy@advantech.tw
* [Kontron](http://www.kontron.com/) - martin.unverdorben@kontron.com
* [Nexcom](http://www.nexcom.com/)

### <a name="qualcomm-dragonboard-410c-apq8016-based-custom-design"></a>**Qualcomm DragonBoard 410c (APQ8016 基于) 的自定义设计**

基于 Qualcomm AQP8016 SoC) 的 DragonBoard 410c (的二进制 BSP 可从 [Qualcomm 开发人员网络](https://developer.qualcomm.com/hardware/dragonboard-410c/software)下载。

BSP 包包含 ACPI 的源代码，以允许只需 ACPI 更改的简单硬件自定义。  

> [!IMPORTANT]
> 如果需要额外的硬件自定义，例如使用特定的 MIPI-DSI 显示面板，请启用平台安全启动、RF 校准和认证 (例如。 FCC、CE) ，你将需要成为一个 Qualcomm BSP 源代码，或与具有访问权限的提供商合作 (在) 的经验丰富的合作伙伴。

建议：

1. 如果可能，请与有经验的 SoM 供应商合作，以实现自定义设计。
2. 如果要构建自定义板，请使用 SoM 供应商或经验丰富的 Qualcomm BSP 自定义服务提供程序，如用于 BSP 自定义和设计帮助的 [Intrinsyc](https://www.intrinsyc.com/) 或 [Thundersoft](http://www.thundersoft.com/) 。
3. 如果预计容量非常大 (百万) ，请 [联系 Qualcomm](https://assets.qualcomm.com/contact-sales-iot.html)。

#### <a name="experienced-partners"></a>*经验丰富的合作伙伴*

* [Intrinsyc](https://www.intrinsyc.com/computing-platforms/410-som/) -标记 Waldenberg (mwaldenberg@intrinsyc.com) 
* [Keith & Koep](https://keith-koep.com/en/products/products-som/myon-1-features-snapdragon-410/) - contact@keith-koep.com
* [Reycom](http://www.reycom.swiss/en/home-swiss.html) - welcome@reycom.swiss
* [Unitech](http://ute.com/products_info.php?pc1=4&pc2=461&rbu=0&pid=2395) (saml@tw.ute.com) ;Perry (perryt@te.ute.com) 

### <a name="nxp-preview"></a>**NXP 预览**

NXP 支持 Windows 10 IoT 核心版提供公共预览版。 有关详细信息，请访问 BSP 或查找硬件合作伙伴，请访问 [NXP SoC 页面](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/iotnxp)。

你还可以与我们正在使用的合作伙伴联系：

* Advantech [RSB-4411](http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858) - buy@advantech.tw
* Keith & Koep [pConXS](https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/
) WITH [Trizeps VII](https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/) - contact@keith-koep.com
* Kontron [SMARC-SAMX6i](https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html) Unverdorben (martin.unverdorben@kontron.com) 
* 稳定运行 [Hummingboard Edge](https://www.solid-run.com/imx6-win-10-iot-core/ )-Ilya Viten (ilya@solid-run.com) 
* Geniatech [som-iMX6Q-问题 7](https://www.geniatech.com/product/som-imx6q-q7/)  &  [som-iMX7D](https://www.geniatech.com/product/som-imx7d/) -Mike Decker (mike.decker@geniatech.com) 或 Fang Jijun (Fjj@geniatech.com) 
* 通过 [VAB-820](https://www.viaembeddedstore.com/shop/boards/vab-820/) -Michael Fox (MichaelFox@via.com.tw) 或梦寐以求 (dreamku@via.com.tw) 
* Phytec [PHYBOARD-I MX7](https://phytec.com/products/single-board-computers/phyboard-i.mx7/) -Brad Dodson (sales@phytec.com) 


## <a name="other-options"></a>其他选项

如果你发现你仍想要创建自定义的板，我们提供了下面的制造商建议，这些建议可帮助你了解板的图表和布局。

* [所有 PCB](http://www.allpcb.com/)
* [Geppetto/Gumstix](https://www.gumstix.com/geppetto/)
* [JLC PCB](https://jlcpcb.com/)
* [Myro PCB](http://www.myropcb.com/)
* [OSH 寄存](https://oshpark.com/)
* [seeed studio](https://www.seeedstudio.com/)
