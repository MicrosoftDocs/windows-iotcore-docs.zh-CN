---
title: Soc 和适用于 Windows 10 IoT Core 的自定义看板
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解有关各种建议看板和社区的设备的硬件功能信息。
keywords: windows iot、 开发设备、 任务板，SOC，SOM，Raspberry Pi 2、 Raspberry Pi 3、 Minnowboard 最大值、 DragonBoard 芯片上的系统
ms.openlocfilehash: b4225937fef1338182c77baa0fd288b7ed597d45
ms.sourcegitcommit: 3eacb968296e79e7e981fdc2a6f7f4f69c0920d1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2019
ms.locfileid: "65040193"
---
# <a name="socs-and-custom-boards"></a>Soc 和自定义看板

## <a name="microsoft-enabled-socs"></a>Microsoft-enabled SoCs

Microsoft 致力于 Broadcom、 Intel、 NXP，和 Qualcomm 要验证支持 Windows 10 IoT Core 芯片 (Soc) 上的多个供应商的系统上。 这些 IoT Core 支持 Soc 可在数百个不同的设备，你可以使用原型和商业化您的创意。

| Broadcom | Intel | Qualcomm | NXP |
|----------|-------|----------|-----|
| BCM2837 | [Intel Atom® 处理器 E3900 系列 (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                                | [Snapdragon 410 (APQ8016)](https://www.qualcomm.com/products/snapdragon/processors/410) | [i.MX 6 系列](http://aka.ms/iotnxp) |
| BCM2836 | [Intel Celeron® 处理器 N3350 (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                                    | [Snapdragon 212 (APQ8009)](https://www.qualcomm.com/products/snapdragon/processors/212) | [i.MX 7 系列](http://aka.ms/iotnxp)     |
|         | [Intel® Pentium® 处理器 N4200 平台 (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                           |                                                                                         | [i.MX 8 M 系列](http://aka.ms/iotnxp) |
|         | [Intel® Pentium® 和 Celeron® 处理器 N3000 系列 (Braswell)](http://ark.intel.com/products/codename/66094/#@embedded)                    |                                                                                         |      |
|         | [Intel® Atom® x5 E8000 处理器 (Braswell)](http://ark.intel.com/products/codename/66094/#@embedded)                                        |                                                                                         |  |
|         | [Intel® Atom® x5 Z8350 处理器 （Cherry 线索）](https://ark.intel.com/products/93361/Intel-Atom-x5-Z8350-Processor-2M-Cache-up-to-1_92-GHz) |                                                                                         |     |
|         | [Intel Atom® 处理器 E3800 产品系列 (Bay 线索-我)](http://ark.intel.com/products/codename/55844/#@Embedded)                     |                                                                                         |  |
|         | [Intel® Pentium® 和 Celeron® 处理器 N 和 J 系列 (Bay 线索-M/D)](http://ark.intel.com/products/codename/55844/)                     |                                                                                         |       |

选择要采用的 SoC 将依赖于如性能要求、 电源配置文件、 成本、 物理连接选项、 长时间术语支持和操作环境的注意事项。

此外需要决定想要使用的现成的看板或设备，生成的模块 (SoM) 再加上自定义的承运人看板，使用系统的自定义设备或生成完整的自定义看板。 成本和自定义级别是在此决策，这两个通常逐渐增加进一步自定义的关键因素。

## <a name="windows-10-iot-core-features-by-processor-family"></a>按处理器系列的 Windows 10 IoT 核心版功能

> [!NOTE]
> 此列表将为非商业公共预览版中不考虑处理器。

为了帮助你选择适当的平台，为你的设备下, 表显示按处理器系列使用 Windows 10 IoT Core 支持的功能。 下面列出的所有功能都支持 Windows 10 IoT 核心版，但某些 Soc 可能没有包含在其设计中的特定 IP，而此类表示具有"n/A"。 在这种情况下，第三方解决方案可以合并到用于提供所需的功能的设计。  在有限数量的处理器不实现 Windows 10 IoT 核心功能的情况下，该条目保留为空。

> |    | Intel  |  Qualcomm  | NXP i.MX6 | NXP i.MX7 | NXP i.MX8M | Broadcom |
> |----|--------|------------|-----------|-----------|------------|----------|
> | Audio | x | x | x | x | x | x |
> | GPIO | x | x | x | x | x | x |
> | I2C | x | x | x | x | x | x |
> | Ethernet | x | 不可用 | x | x | x | x |
> | SPI | x | x | x | x | x | x |
> | 显示 | x | x | x | x | x | x |
> | UART | x | x | x | x | x | x |
> | USB | x | x | x | x | x | x |
> | PCIe | x | 不可用 | x | 在开发 | 在开发 | 不可用 |
> |MIPI-CSI | 不可用 | x | 不可用 | 不可用 | 不可用 | 不可用 |
> | 图形/视频 | x | x | 软件呈现 | 软件呈现 | 软件呈现 | 软件呈现 |
> | GPS | 不可用 | x | 不可用 | 不可用 | 不可用 | 不可用 |
> | Wi-Fi/BT | 不可用 | x | 不可用 | 不可用 | 不可用 | 不可用 |
> | 受信任的 I/O | 不可用 | 不可用 | x | x | x | 不可用 |
> | 处理器电源管理 |  | x | x | x | 在开发 | |
> | TPM | x | x | x | x | x | 不可用 |
> | 安全启动 | x | x | 在开发 | 在开发 | 在开发 | |
> | 休眠 | x | | | | | | 
> | PWM | x | 不可用 | x | x | x | |
> | JTAG | x | 不可用 | x | x | x | |
> | eMMC | x | x | x | x | x | |
> | SDHC | x | x | x | x | x | x |

## <a name="customized-boards"></a>自定义看板

如果在包含连接选项适用于你的方案，窗体中有现成的设备，，通常是最经济和时间的有效选择。  

对于大多数人来说，开发完整的自定义看板将意义时应产品销售卷中大于数十台、 或甚至数百个，数千个单位。 对于较小的卷，使用 SoM 和设计自定义的承运人看板，而不是设计一个全新的看板，可以显著减少成本和时间市场，以及简化软件开发和集成。

每个平台都有唯一的实现过程中需要注意的异常。  以下是有关如何入门的一些建议。 尽管有很多公司在 Windows 10 IoT Core 上构建，此处是一些已证明体验 Windows 10 IoT 核心版所使用的列表：

* __[Raspberry Pi](#raspberry-pi-derived-custom-design)__
* __[Intel](#intel-based-custom-design)__
* __[Qualcomm](#qualcomm-dragonboard-410c-apq8016-based-custom-design)__
* __[NXP](#nxp-preview)__

*如果是 SoM 提供商或考虑了 ODM 并且想要添加到下面的列表，请发送电子邮件至[ winiotsomhelp@microsoft.com ](mailto:winiotsomhelp@microsoft.com)或直接编辑此页并提交拉取请求。*

*此处列出的许多公司都是大型和复杂。如果你遇到达到适当的人的问题，请发送电子邮件[ winiotsomhelp@microsoft.com ](mailto:winiotsomhelp@microsoft.com)我们将执行最大努力来将您连接到正确的人。*

### <a name="raspberry-pi-derived-custom-design"></a>**Raspberry Pi 派生的自定义设计**

[元素 14](https://www.element14.com/community/docs/DOC-76955/l/raspberry-pi-customization-service)产品/服务板 Raspberry Pi，以便您可以添加或删除连接选项的自定义服务。 如果还需要对 BSP 进行自定义，则可以利用[打开 Github 上的源代码 BSP](https://github.com/ms-iot/rpi-iotcore)。

### <a name="intel-based-custom-design"></a>**基于 Intel 的自定义设计**

不存在的一个充满活力的生态系统[遇到 Intel 设备构建者](https://solutionsdirectory.intel.com/solutions-directory/processors/278/processors/309/processors/402/processors/782/processors/788/processors/1103/processors/1107/processors/1110/processors/1175/processors/1344/processors/1348/processors/1349)有关您可以使用的 Windows。 设计为运行 Windows 10 IoT Core 的 Intel 设备有几种更常见的 Pc 的区别：

1. 如果需要提供用户模式通用 Windows 平台 (UWP) API 对 I2C、 GPIO 和 SPI 等简单总线的访问权限，则需要确保在 UEFI 固件中的 ACPI 表包含 RHProxy 合适的条目。 请参阅[用户模式访问](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access)有关详细信息。
2. 必须确保在固件中的 SMBIOS 包含的信息，如下所示[OEM 许可要求](https://docs.microsoft.com/windows/iot-core/commercialize-your-device/oemlicenserequirements)。

如果要生成你自己的看板，请联系 BIOS 供应商，如果您需要的 ACPI 或 SMBIOS 的变化的指南。

#### <a name="experienced-partners"></a>*经验丰富的合作伙伴*

* [Aaeon](http://www.aaeon.com/en/)
* [Advantech](http://www.advantech.com/) - buy@advantech.tw
* [Kontron](http://www.kontron.com/) - martin.unverdorben@kontron.com
* [Nexcom](http://www.nexcom.com/)

### <a name="qualcomm-dragonboard-410c-apq8016-based-custom-design"></a>**Qualcomm DragonBoard 410 c (APQ8016)-基于自定义设计**

可以从下载的 DragonBoard 410 c （基于 AQP8016 Qualcomm SoC） 的二进制 BSP [Qualcomm 开发人员网络](https://developer.qualcomm.com/hardware/dragonboard-410c/software)。

BSP 包包括 ACPI 以便只需要 ACPI 更改的简单硬件自定义的源代码。  

> [!IMPORTANT] 
> 如果需要额外的硬件自定义项，例如，使用特定的 MIPI DSI 显示面板中，启用平台安全启动，RF 校准和证书 （例如。 FCC，CE），您将需要成为 Qualcomm BSP 源代码授权用户，或使用提供程序具有访问权限 （请参阅下面的经验丰富的合作伙伴）。

建议：

1. 如果可能，请使用经验丰富的 SoM 供应商，以启用自定义的设计。
2. 如果您正在构建自定义看板，使用 SoM 供应商或一个有经验的 Qualcomm BSP 自定义服务提供程序，如[Intrinsyc](https://www.intrinsyc.com/)或[Thundersoft](http://www.thundersoft.com/)为 BSP 自定义和设计方面的帮助。
3. 如果您预计有大量 （数百万个），[联系 Qualcomm](https://assets.qualcomm.com/contact-sales-iot.html)。

#### <a name="experienced-partners"></a>*经验丰富的合作伙伴*

* [Intrinsyc](https://www.intrinsyc.com/computing-platforms/410-som/) -标记 Waldenberg (mwaldenberg@intrinsyc.com)
* [Keith 和](https://keith-koep.com/en/products/products-som/myon-1-features-snapdragon-410/)- contact@keith-koep.com
* [Reycom](http://www.reycom.swiss/en/home-swiss.html) - welcome@reycom.swiss
* [Unitech](http://ute.com/products_info.php?pc1=4&pc2=461&rbu=0&pid=2395) -Sam (saml@tw.ute.com);Perry (perryt@te.ute.com)

### <a name="nxp-preview"></a>**NXP 预览**

适用于 Windows 10 IoT Core NXP 支持处于公共预览状态。 有关详细信息，访问 BSP，或若要查找的硬件合作伙伴，请转到[NXP SoC 页](http://aka.ms/iotnxp)。

您还可以通过扩展到合作伙伴我们正在使用：

* Advantech [RSB 4411](http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858) - buy@advantech.tw
* Keith 和[pConXS](https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/)与[Trizeps VII](https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/) - contact@keith-koep.com
* Kontron [SMARC sAMX6i](https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html) -Martin Unverdorben (martin.unverdorben@kontron.com)
* Solid 运行[Hummingboard 边缘](https://www.solid-run.com/imx6-win-10-iot-core/ )-Ilya Viten (ilya@solid-run.com)
* Geniatech[问题 7 iMX6Q SoM](https://www.geniatech.com/product/som-imx6q-q7/) & [SoM iMX7D](https://www.geniatech.com/product/som-imx7d/) -Mike 德克尔 (mike.decker@geniatech.com) 或 Fang Jijun (Fjj@geniatech.com)
* 通过[VAB 820](https://www.viaembeddedstore.com/shop/boards/vab-820/) -Michael Fox (MichaelFox@via.com.tw) 或梦想 Ku (dreamku@via.com.tw)
* Phytec [phyBOARD i.MX7](https://phytec.com/products/single-board-computers/phyboard-i.mx7/) -Brad Dodson (sales@phytec.com)


## <a name="other-options"></a>其他选项

如果您发现，你仍想要创建自定义看板，我们提供的制造商在下面的一些建议可以帮助图表和看板的布局。

* [所有 PCB](http://www.allpcb.com/)
* [Geppetto/Gumstix](https://www.gumstix.com/geppetto/)
* [JLC PCB](https://jlcpcb.com/)
* [Myro PCB](http://www.myropcb.com/)
* [OSH PARK](https://oshpark.com/)
* [seeed studio](https://www.seeedstudio.com/)
