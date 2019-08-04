---
title: Windows IoT 和 NXP i.MX
author: chsha
ms.author: chsha
ms.date: 02/22/2019
ms.topic: article
description: 了解 Windows 10 IoT Core 和 NXP i.MX Soc
keywords: Windows 10 IoT Core, 入门, i.MX, NXP
ms.openlocfilehash: 244d767507393680df7a48487522ff62be40692d
ms.sourcegitcommit: c5552007f5456e57512307f51b146406a23fa723
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2019
ms.locfileid: "68739815"
---
# <a name="window-10-iot-core-and-nxp-imx-socs"></a>Windows 10 IoT Core 和 NXP i.MX Soc

在2018中, Microsoft 和 NXP 在 NXP i.MX 6 和 i.MX 7 硅上公布了 Windows 10 IoT Core 的个人预览版, 并开始在 i.MX 8 分钟 Soc 上工作。 数百个商业开发人员、研究人员和开发人员在10年的 Windows 安全更新和灵活性和可靠性上都有了 NXP 硅的兴趣。 
 
在预览版期间, Microsoft 和 NXP 工程师会花费数千个小时的时间来优化并改善 BSP, 这是基于评估解决方案的输入。 我们与对现代化旧式工业控制器感兴趣的客户合作, 开发新的云连接构建自动化解决方案, 和具有一流的安全性 (如[受信任 i/o](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97)) 的网关。
 
基于解决方案的主要兴趣, Microsoft 和 NXP 现在将 Bsp 作为非商业公共预览版提供 i.MX 6、i.MX 7 和 i.MX 8 分钟系列。 由于 Microsoft 和 NXP 在内嵌和 IoT 市场中具有较长的历史记录, 因此我们了解设计灵活性的需求。 因此, 除了在模块解决方案 Microsoft、NXP 和我们的硬件合作伙伴上启用的多单板计算机和系统外, 还会在开放源代码许可下提供 i.MX 6、i.MX 7 和 i.MX 8 分钟 Bsp。 现在, 每个人都可以访问 i.MX 6、i.MX 7 和 i.MX 8 分钟产品系列的完整 BSP 内容, 以便在其硬件上进行评估, 以及2018年10月版的 Windows 10 IoT Core。


## <a name="bsp-access"></a>BSP 访问

如果你有兴趣启用对你自己的 i.MX 硬件的支持, 请访问[Github]( https://github.com/ms-iot/imx-iotcore)上的 BSP 源和文档。 除非另行说明, 否则在 MIT 许可证下提供了大部分来源。 此代码由 NXP 提供支持的商业使用发布, 可在[此处](https://www.nxp.com/support/developer-resources/evaluation-and-development-boards/i.mx-evaluation-and-development-boards/i.mx-software-and-development-tool:IMX-SW)找到。

如果你有 NXP 硬件/BSP 报告相关问题或有关 BSP 如何更好地支持你的目标解决方案的信息, 请将其发布到[NXP 社区](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D)。 对于任何与 Windows 相关的问题, 请使用[Microsoft 社区](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT)。


## <a name="ecosystem-resources"></a>生态系统资源

一些 Microsoft 和 NXP 合作伙伴已启用商用 i.MX 6、i.MX 7 和 i.MX 8 分钟设备, 支持 Windows 10 IoT Core。 请直接与合作伙伴联系以获取硬件和平台映像。


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
