---
title: Windows IoT 和 NXP i.MX
author: chsha
ms.author: chsha
ms.date: 02/22/2019
ms.topic: article
description: 了解 Windows 10 IoT 核心版和 NXP i.MX Soc
keywords: Windows 10 IoT 核心版，开始，i.MX，NXP
ms.openlocfilehash: a6331b8f5695c2a432e1b22f1ba275cd48c549e4
ms.sourcegitcommit: 3eacb968296e79e7e981fdc2a6f7f4f69c0920d1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2019
ms.locfileid: "65040181"
---
# <a name="window-10-iot-core-and-nxp-imx-socs"></a>窗口 10 IoT 核心版和 NXP i.MX Soc

在 2018 中，Microsoft 和 NXP 宣布的 Windows 10 IoT Core 上 NXP i.MX 6 和 i.MX 7 硅谷的专用预览版并开始工作的 i.MX 8 分钟 Soc。 数百个商业开发人员、 研究人员和决策者表示其感兴趣的 10 年的 Windows 安全更新和大的灵活性和可靠性 NXP 硅谷的组合。 
 
预览期间，Microsoft 和 NXP 工程师所用的数千个小时优化和提高 BSP 基于来自这些评估解决方案的输入。 我们与客户兴趣现代化旧工业控制器，开发新的云连接构建自动化解决方案，并具有网关类领先的安全，如[受信任的 I/O](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97)。
 
基于解决方案中感兴趣者甚众，Microsoft 和 NXP 现在将 Bsp i.MX 6、 7，i.MX 和 i.MX 8 分钟系列 Soc 提供作为非商业公共预览版。 由于长历史记录 Microsoft 和 NXP 中具有嵌入和 IoT 市场，我们了解来提高设计灵活性需求。 因此，除了多个单一板计算机和模块解决方案 Microsoft 上的系统、 NXP 和我们合作伙伴已启用的硬件，i.MX 6、 7、 i.MX 和 i.MX 8 分钟 Bsp 提供开放源代码许可下。 现在，每个人都将能够访问 i.MX 6、 7、 i.MX 和 i.MX 8 分钟的评估其硬件和 2018 年 10 月版本的 Windows 10 IoT Core 上使用的产品系列的完整 BSP 内容。


## <a name="bsp-access"></a>BSP 访问

如果您想要启用对 i.MX 硬件的支持，请访问 BSP 源和文档上[Github]( https://github.com/ms-iot/imx-iotcore)。 除非另有说明，大多数源 MIT 许可证下提供。 代码仍处于开发阶段。 并非所有平台功能完全启用或优化。 代码当前适用于非商业开发仅在时间时。 专业质量的发行版预计在 2019年更高版本。

如果你有 NXP 硬件/BSP 报告相关问题或反馈上 BSP 可以更好地支持你有针对性的解决方案，请将问题发布到[NXP 社区](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D)。 对于任何 Windows 相关的问题，请使用[Microsoft Community](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT)。


## <a name="ecosystem-resources"></a>生态系统资源

有多个 Microsoft 和 NXP 合作伙伴已经启用了商业 i.MX 6，i.MX 7，并且具有 i.MX 8 分钟设备支持的 Windows 10 IoT 核心版。 请联系合作伙伴，直接获取硬件和平台映像。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">设备</th>
<th align="left">联系人</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="https://www.aaeon.com/en/p/pico-itx-boards-pico-imx6/">Aaeon PICO-IMX6</a></p></td>
<td align="left"><p><p><a href="mailto:davidhung@aaeon.com.tw">David 挂起</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858">Advantech RSB-4411</a></p></td>
<td align="left"><p><p><a href="mailto:buy@advantech.com">buy@advantech.com</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/">Compulab IoT-Gate</a></p></td>
<td align="left"><p><p><a href="mailto:igor@compulab.co.il">Igor Vaisbein</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.geniatech.com/product/som-imx6q-q7/">Geniatech SoM-iMX6Q-Q7</a></p></td>
<td align="left"><p><p><a href="mailto:mike.decker@geniatech.com">Mike 德克尔</a>或<a href="mailto:Fjj@geniatech.com">Fang Jijun</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.geniatech.com/product/som-imx7d/">Geniatech SoM-iMX7D</a></p></td>
<td align="left"><p><p><a href="mailto:mike.decker@geniatech.com">Mike 德克尔</a>或<a href="mailto:Fjj@geniatech.com">Fang Jijun</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.karo-electronics.de/tx-standard.html?&L=1">Ka Ro 电子 TX6UL，TX6S，TX6DL 和 TX6Q</a></p></td>
<td align="left"><p><p><a href="mailto:us@karo-electronics.de">Uwe Steinkohl</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/">Keith 和 pConXS</a>与<a href="https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/">Trizeps VII</a></p></td>
<td align="left"><p><p><a href="mailto:contact@keith-koep.com">contact@keith-koep.com</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html">Kontron SMARC-sAMX6i</a></p></td>
<td align="left"><p><p><a href="mailto:martin.unverdorben@kontron.com">Martin Unverdorben</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://phytec.com/product/phyboard-imx7-development-kit/">phyBOARD i.MX 7 开发工具包</a></p></td>
<td align="left"><p><p><a href="mailto:sales@phytec.com">Fernando Benitez</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.solid-run.com/imx6-win-10-iot-core/">实体运行 Hummingboard 边缘</a></p></td>
<td align="left"><p><p><a href="mailto:ilya@solid-run.com">Ilya Viten</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.viaembeddedstore.com/shop/boards/vab-820/">VIA VAB-820</a></p></td>
<td align="left"><p><p><a href="mailto:MichaelFox@via.com.tw">Michael Fox</a>或<a href="mailto:dreamku@via.com.tw">梦想 Ku</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors/evaluation-kit-for-the-i.mx-6ull-and-6ulz-applications-processor:MCIMX6ULL-EVK">MCIMX6ULL-EVK</a></p></td>
<td align="left"><p><p><a href="mailto:Wei.A.Wang@nxp.com">Wei Wang</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK">MCIMX8M-EVK</a></p></td>
<td align="left"></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="http://www.nxp.com/imx8mminievk">MCIMX8MMINI-EVK</a></p></td>
<td align="left"></td>
</tr>
</tbody>
</table>
