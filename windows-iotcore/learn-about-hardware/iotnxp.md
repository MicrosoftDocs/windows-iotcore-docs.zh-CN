---
title: Windows IoT 和 NXP i.MX
author: chsha
ms.author: chsha
ms.date: 02/22/2019
ms.topic: article
description: 了解 Windows 10 IoT Core 和 NXP i.MX Soc
keywords: Windows 10 IoT Core，入门，i.MX，NXP
ms.openlocfilehash: 79b42c31abc110a3256db32fd67818288f7269aa
ms.sourcegitcommit: 833f64e5c9ef8edc6ea62824d5f4f0b7d5a03270
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/18/2019
ms.locfileid: "74154924"
---
# <a name="window-10-iot-core-and-nxp-imx-socs"></a>Windows 10 IoT Core 和 NXP i.MX Soc

NXP 支持 Windows 10 IoT Core，通过 i.MX 应用程序处理器和精选开发板上的板支持包（Bsp）。 

I.MX 应用程序平台上经过高度优化的 Windows 10 IoT Core Bsp 使你可以更轻松地从设备到云构建安全、可缩放的解决方案，其中包括预配到大规模管理和保护设备。 设计人员可以轻松地运行云服务，从 IoT 设备获得见解。 I.MX 应用程序处理器上的 Windows 10 IoT Core 可以更快地投放市场，其中包含现成的许多用户界面和设备堆栈。

根据客户对使用 NXP i.MX 硅的 Windows 10 IoT Core 的巨大兴趣，Microsoft 和 NXP 已为 i.MX 6、i.MX 7 和 i.MX 8 分钟系列 Soc 提供了 Bsp，可供商业使用。 由于 Microsoft 和 NXP 在内嵌和 IoT 市场中具有较长的历史记录，因此我们了解设计灵活性的需求。 因此，除了在模块解决方案 Microsoft、NXP 和我们的硬件合作伙伴上启用的多单板计算机和系统外，还会在开放源代码许可下提供 i.MX 6、i.MX 7 和 i.MX 8 分钟 Bsp。 现在，每个人都可以访问 i.MX 6、i.MX 7 和 i.MX 8 分钟产品系列的完整 BSP 内容，与 Windows 10 IoT Core 10 月2018版一起使用。

## <a name="bsp-access"></a>BSP 访问

如果你有兴趣为自己的 i/MX 硬件启用商业支持，请访问[NXP 网站](https://www.nxp.com/design/software/embedded-software/windows-10-iotIf-core-for-i.mx-applications-processors:IMXWIN10IOT)上的 BSP 源和文档。 

如果你有 NXP 硬件/BSP 报告相关问题或有关 BSP 如何更好地支持你的目标解决方案的信息，请将其发布到[NXP 社区](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D)。 对于任何与 Windows 相关的问题，请使用[Microsoft 社区](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT)。

如果你需要超出用于 BSP 自定义和 integation i.MX 产品的社区论坛的其他支持，可通过 Pro-Support www.nxp.com/prosupport 获得支持。 可以将查询发送到[prosupport@nxp.com](mailto:prosupport@nxp.com)。 对于 Windows 10 IoT 付费服务和集成，请联系[epsoinfo@microsoft.com](mailto:epsoinfo@microsoft.com)。


## <a name="ecosystem-resources"></a>生态系统资源

一些 Microsoft 和 NXP 合作伙伴已在商业 i.MX 6、i.MX 7 和 i.MX 8 分钟设备上启用了 Windows 10 IoT Core。 请直接联系合作伙伴进行硬件访问。 


> | 设备 | 联系人 |
> |-------|------|
> | [Aaeon PICO-IMX6](https://www.aaeon.com/en/p/pico-itx-boards-pico-imx6/) | [David 挂起](mailto:davidhung@aaeon.com.tw) |
> | [Advantech RSB-4411](http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858) | [buy@advantech.com](mailto:buy@advantech.com) |
> | [Compulab IoT-入口](https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/) | [Igor Vaisbein](mailto:igor@compulab.co.il) | 
> | [FS Eletronik 系统 armStone A9](https://www.fs-net.de/en/products/armstone/armstonea9/) | [support@fs-net.de](mailto:support@fs-net.de) |
> | [Geniatech SoM-iMX6Q-问题7](https://www.geniatech.com/product/som-imx6q-q7/) | [Mike Decker](mailto:mike.decker@geniatech.com)或[Fang Jijun](mailto:Fjj@geniatech.com) |
> | [Geniatech SoM-iMX7D](https://www.geniatech.com/product/som-imx7d/) | [Mike Decker](mailto:mike.decker@geniatech.com)或[Fang Jijun](mailto:Fjj@geniatech.com) |
> | [Ka-Ro 电子 TX6UL、TX6S、TX6DL 和 TX6Q](https://www.karo-electronics.de/tx-standard.html?&L=1) | [Uwe Steinkohl](mailto:us@karo-electronics.de) |
> | [Keith & Koep pConXS](https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/) WITH [Trizeps VII](https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/) | [contact@keith-koep.com](mailto:contact@keith-koep.com) |
> | [Kontron SMARC-sAMX6i](https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html) | [圣马丁 Unverdorben](mailto:martin.unverdorben@kontron.com) |
> | [Novtech Meerkat](http://novtech.com/products/meerkat96.html) | [sales@novtech.com](mailto:sales@novtech.com) |
> | [phyBOARD-i.MX 7 开发工具包](https://phytec.com/product/phyboard-imx7-development-kit/) | [Fernando Benitez](mailto:sales@phytec.com) |
> | [实心运行 Hummingboard 边缘](https://www.solid-run.com/imx6-win-10-iot-core/) | [Ilya Viten](mailto:ilya@solid-run.com) |
> | [VIA VAB-820](https://www.viaembeddedstore.com/shop/boards/vab-820/) | [Michael Fox](mailto:MichaelFox@via.com.tw)或[梦寐以求的 Ku](mailto:dreamku@via.com.tw) |
> | [WeAreDev WAD-MX6W](http://www.wearedev.net/?mod=wadmx6w) | [help@wearedev.net](mailto:help@wearedev.net) |
> | [MCIMX6ULL-EVK](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors/evaluation-kit-for-the-i.mx-6ull-and-6ulz-applications-processor:MCIMX6ULL-EVK) | [Wei Wang](mailto:Wei.A.Wang@nxp.com) |
> | [MCIMX8M-EVK](https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK) |  |
> | [MCIMX8MMINI-EVK](http://www.nxp.com/imx8mminievk) | []() |
> | [i. MX8M MaaXBoard](http://www.embest-tech.com/prod_view.aspx?TypeId=117&Id=388&Fid=t3:117:3) | [chinasales@embest-tech.com](mailto:chinasales@embest-tech.com) |

注意：上述合作伙伴支持其硬件和其硬件的 BSP。 它们可能无法帮助解决其他软件或配置问题。

