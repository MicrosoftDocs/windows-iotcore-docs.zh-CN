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
# <a name="window-10-iot-core-and-nxp-imx-socs"></a><span data-ttu-id="5252a-104">窗口 10 IoT 核心版和 NXP i.MX Soc</span><span class="sxs-lookup"><span data-stu-id="5252a-104">Window 10 IoT Core and NXP i.MX SoCs</span></span>

<span data-ttu-id="5252a-105">在 2018 中，Microsoft 和 NXP 宣布的 Windows 10 IoT Core 上 NXP i.MX 6 和 i.MX 7 硅谷的专用预览版并开始工作的 i.MX 8 分钟 Soc。</span><span class="sxs-lookup"><span data-stu-id="5252a-105">In 2018, Microsoft and NXP announced a private preview of Windows 10 IoT Core on NXP i.MX 6 and i.MX 7 silicon and began work on the i.MX 8M SoCs.</span></span> <span data-ttu-id="5252a-106">数百个商业开发人员、 研究人员和决策者表示其感兴趣的 10 年的 Windows 安全更新和大的灵活性和可靠性 NXP 硅谷的组合。</span><span class="sxs-lookup"><span data-stu-id="5252a-106">Hundreds of commercial developers, researchers, and Makers expressed their interest in the combination of 10 years of Windows security updates and the flexibility and reliability of NXP silicon.</span></span> 
 
<span data-ttu-id="5252a-107">预览期间，Microsoft 和 NXP 工程师所用的数千个小时优化和提高 BSP 基于来自这些评估解决方案的输入。</span><span class="sxs-lookup"><span data-stu-id="5252a-107">During the preview, Microsoft and NXP engineers spent thousands of hours tuning and improving the BSP based on input from those evaluating the solution.</span></span> <span data-ttu-id="5252a-108">我们与客户兴趣现代化旧工业控制器，开发新的云连接构建自动化解决方案，并具有网关类领先的安全，如[受信任的 I/O](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97)。</span><span class="sxs-lookup"><span data-stu-id="5252a-108">We worked with customers interested in modernizing legacy industrial controllers, developing new cloud connected building automation solutions, and gateways with class leading security such as [trusted I/O](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97).</span></span>
 
<span data-ttu-id="5252a-109">基于解决方案中感兴趣者甚众，Microsoft 和 NXP 现在将 Bsp i.MX 6、 7，i.MX 和 i.MX 8 分钟系列 Soc 提供作为非商业公共预览版。</span><span class="sxs-lookup"><span data-stu-id="5252a-109">Based on the overwhelming interest in the solution, Microsoft and NXP are now making BSPs for the i.MX 6, i.MX 7, and i.MX 8M family of SoCs available as a non-commercial public preview.</span></span> <span data-ttu-id="5252a-110">由于长历史记录 Microsoft 和 NXP 中具有嵌入和 IoT 市场，我们了解来提高设计灵活性需求。</span><span class="sxs-lookup"><span data-stu-id="5252a-110">Because of the long history Microsoft and NXP have in the embedded and IoT markets, we understand the need for design flexibility.</span></span> <span data-ttu-id="5252a-111">因此，除了多个单一板计算机和模块解决方案 Microsoft 上的系统、 NXP 和我们合作伙伴已启用的硬件，i.MX 6、 7、 i.MX 和 i.MX 8 分钟 Bsp 提供开放源代码许可下。</span><span class="sxs-lookup"><span data-stu-id="5252a-111">Therefore, in addition to the multiple single board computers and system on module solutions Microsoft, NXP, and our hardware partners have enabled, the i.MX 6, i.MX 7, and i.MX 8M BSPs are provided under open source licensing.</span></span> <span data-ttu-id="5252a-112">现在，每个人都将能够访问 i.MX 6、 7、 i.MX 和 i.MX 8 分钟的评估其硬件和 2018 年 10 月版本的 Windows 10 IoT Core 上使用的产品系列的完整 BSP 内容。</span><span class="sxs-lookup"><span data-stu-id="5252a-112">Now, everyone will be able to access the complete BSP contents for the i.MX 6, i.MX 7, and i.MX 8M product families for evaluation use on their hardware along with the October 2018 release of Windows 10 IoT Core.</span></span>


## <a name="bsp-access"></a><span data-ttu-id="5252a-113">BSP 访问</span><span class="sxs-lookup"><span data-stu-id="5252a-113">BSP Access</span></span>

<span data-ttu-id="5252a-114">如果您想要启用对 i.MX 硬件的支持，请访问 BSP 源和文档上[Github]( https://github.com/ms-iot/imx-iotcore)。</span><span class="sxs-lookup"><span data-stu-id="5252a-114">If you are interested to enable support for your own i.MX hardware, please access the BSP source and documentation on [Github]( https://github.com/ms-iot/imx-iotcore).</span></span> <span data-ttu-id="5252a-115">除非另有说明，大多数源 MIT 许可证下提供。</span><span class="sxs-lookup"><span data-stu-id="5252a-115">Unless noted, the majority of the source is provided under MIT license.</span></span> <span data-ttu-id="5252a-116">代码仍处于开发阶段。</span><span class="sxs-lookup"><span data-stu-id="5252a-116">The code is still under development.</span></span> <span data-ttu-id="5252a-117">并非所有平台功能完全启用或优化。</span><span class="sxs-lookup"><span data-stu-id="5252a-117">Not all platform features are fully enabled or optimized.</span></span> <span data-ttu-id="5252a-118">代码当前适用于非商业开发仅在时间时。</span><span class="sxs-lookup"><span data-stu-id="5252a-118">The code is currently intended for non-commercial development only at time time.</span></span> <span data-ttu-id="5252a-119">专业质量的发行版预计在 2019年更高版本。</span><span class="sxs-lookup"><span data-stu-id="5252a-119">A commercial quality release is expected later in 2019.</span></span>

<span data-ttu-id="5252a-120">如果你有 NXP 硬件/BSP 报告相关问题或反馈上 BSP 可以更好地支持你有针对性的解决方案，请将问题发布到[NXP 社区](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D)。</span><span class="sxs-lookup"><span data-stu-id="5252a-120">If you have NXP hardware/BSP releated questions or feedback on how the BSP can better support your targeted solution, please post to the [NXP Community](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D).</span></span> <span data-ttu-id="5252a-121">对于任何 Windows 相关的问题，请使用[Microsoft Community](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT)。</span><span class="sxs-lookup"><span data-stu-id="5252a-121">For any Windows related questions, please use the [Microsoft Community](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT).</span></span>


## <a name="ecosystem-resources"></a><span data-ttu-id="5252a-122">生态系统资源</span><span class="sxs-lookup"><span data-stu-id="5252a-122">Ecosystem Resources</span></span>

<span data-ttu-id="5252a-123">有多个 Microsoft 和 NXP 合作伙伴已经启用了商业 i.MX 6，i.MX 7，并且具有 i.MX 8 分钟设备支持的 Windows 10 IoT 核心版。</span><span class="sxs-lookup"><span data-stu-id="5252a-123">Several Microsoft and NXP partners have enabled commercial i.MX 6, i.MX 7, and i.MX 8M devices with support for Windows 10 IoT Core.</span></span> <span data-ttu-id="5252a-124">请联系合作伙伴，直接获取硬件和平台映像。</span><span class="sxs-lookup"><span data-stu-id="5252a-124">Please contact the partner directly for hardware and a platform image.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="5252a-125">设备</span><span class="sxs-lookup"><span data-stu-id="5252a-125">Device</span></span></th>
<th align="left"><span data-ttu-id="5252a-126">联系人</span><span class="sxs-lookup"><span data-stu-id="5252a-126">Contact</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><span data-ttu-id="5252a-127"><a href="https://www.aaeon.com/en/p/pico-itx-boards-pico-imx6/">Aaeon PICO-IMX6</a></span><span class="sxs-lookup"><span data-stu-id="5252a-127"><a href="https://www.aaeon.com/en/p/pico-itx-boards-pico-imx6/">Aaeon PICO-IMX6</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="5252a-128"><a href="mailto:davidhung@aaeon.com.tw">David 挂起</a></span><span class="sxs-lookup"><span data-stu-id="5252a-128"><a href="mailto:davidhung@aaeon.com.tw">David Hung</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="5252a-129"><a href="http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858">Advantech RSB-4411</a></span><span class="sxs-lookup"><span data-stu-id="5252a-129"><a href="http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858">Advantech RSB-4411</a></span></span></p></td>
<td align="left"><p><p><a href="mailto:buy@advantech.com">buy@advantech.com</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="5252a-130"><a href="https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/">Compulab IoT-Gate</a></span><span class="sxs-lookup"><span data-stu-id="5252a-130"><a href="https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/">Compulab IoT-Gate</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="5252a-131"><a href="mailto:igor@compulab.co.il">Igor Vaisbein</a></span><span class="sxs-lookup"><span data-stu-id="5252a-131"><a href="mailto:igor@compulab.co.il">Igor Vaisbein</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="5252a-132"><a href="https://www.geniatech.com/product/som-imx6q-q7/">Geniatech SoM-iMX6Q-Q7</a></span><span class="sxs-lookup"><span data-stu-id="5252a-132"><a href="https://www.geniatech.com/product/som-imx6q-q7/">Geniatech SoM-iMX6Q-Q7</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="5252a-133"><a href="mailto:mike.decker@geniatech.com">Mike 德克尔</a>或<a href="mailto:Fjj@geniatech.com">Fang Jijun</a></span><span class="sxs-lookup"><span data-stu-id="5252a-133"><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> or <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="5252a-134"><a href="https://www.geniatech.com/product/som-imx7d/">Geniatech SoM-iMX7D</a></span><span class="sxs-lookup"><span data-stu-id="5252a-134"><a href="https://www.geniatech.com/product/som-imx7d/">Geniatech SoM-iMX7D</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="5252a-135"><a href="mailto:mike.decker@geniatech.com">Mike 德克尔</a>或<a href="mailto:Fjj@geniatech.com">Fang Jijun</a></span><span class="sxs-lookup"><span data-stu-id="5252a-135"><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> or <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="5252a-136"><a href="https://www.karo-electronics.de/tx-standard.html?&L=1">Ka Ro 电子 TX6UL，TX6S，TX6DL 和 TX6Q</a></span><span class="sxs-lookup"><span data-stu-id="5252a-136"><a href="https://www.karo-electronics.de/tx-standard.html?&L=1">Ka-Ro Electronics TX6UL, TX6S, TX6DL, and TX6Q</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="5252a-137"><a href="mailto:us@karo-electronics.de">Uwe Steinkohl</a></span><span class="sxs-lookup"><span data-stu-id="5252a-137"><a href="mailto:us@karo-electronics.de">Uwe Steinkohl</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="5252a-138"><a href="https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/">Keith 和 pConXS</a>与<a href="https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/">Trizeps VII</a></span><span class="sxs-lookup"><span data-stu-id="5252a-138"><a href="https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/">Keith & Koep pConXS</a> with <a href="https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/">Trizeps VII</a></span></span></p></td>
<td align="left"><p><p><a href="mailto:contact@keith-koep.com">contact@keith-koep.com</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="5252a-139"><a href="https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html">Kontron SMARC-sAMX6i</a></span><span class="sxs-lookup"><span data-stu-id="5252a-139"><a href="https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html">Kontron SMARC-sAMX6i</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="5252a-140"><a href="mailto:martin.unverdorben@kontron.com">Martin Unverdorben</a></span><span class="sxs-lookup"><span data-stu-id="5252a-140"><a href="mailto:martin.unverdorben@kontron.com">Martin Unverdorben</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="5252a-141"><a href="https://phytec.com/product/phyboard-imx7-development-kit/">phyBOARD i.MX 7 开发工具包</a></span><span class="sxs-lookup"><span data-stu-id="5252a-141"><a href="https://phytec.com/product/phyboard-imx7-development-kit/">phyBOARD-i.MX 7 Development Kit</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="5252a-142"><a href="mailto:sales@phytec.com">Fernando Benitez</a></span><span class="sxs-lookup"><span data-stu-id="5252a-142"><a href="mailto:sales@phytec.com">Fernando Benitez</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="5252a-143"><a href="https://www.solid-run.com/imx6-win-10-iot-core/">实体运行 Hummingboard 边缘</a></span><span class="sxs-lookup"><span data-stu-id="5252a-143"><a href="https://www.solid-run.com/imx6-win-10-iot-core/">Solid Run Hummingboard Edge</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="5252a-144"><a href="mailto:ilya@solid-run.com">Ilya Viten</a></span><span class="sxs-lookup"><span data-stu-id="5252a-144"><a href="mailto:ilya@solid-run.com">Ilya Viten</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="5252a-145"><a href="https://www.viaembeddedstore.com/shop/boards/vab-820/">VIA VAB-820</a></span><span class="sxs-lookup"><span data-stu-id="5252a-145"><a href="https://www.viaembeddedstore.com/shop/boards/vab-820/">VIA VAB-820</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="5252a-146"><a href="mailto:MichaelFox@via.com.tw">Michael Fox</a>或<a href="mailto:dreamku@via.com.tw">梦想 Ku</span><span class="sxs-lookup"><span data-stu-id="5252a-146"><a href="mailto:MichaelFox@via.com.tw">Michael Fox</a> or <a href="mailto:dreamku@via.com.tw">Dream Ku</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="5252a-147"><a href="https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors/evaluation-kit-for-the-i.mx-6ull-and-6ulz-applications-processor:MCIMX6ULL-EVK">MCIMX6ULL-EVK</a></span><span class="sxs-lookup"><span data-stu-id="5252a-147"><a href="https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors/evaluation-kit-for-the-i.mx-6ull-and-6ulz-applications-processor:MCIMX6ULL-EVK">MCIMX6ULL-EVK</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="5252a-148"><a href="mailto:Wei.A.Wang@nxp.com">Wei Wang</a></span><span class="sxs-lookup"><span data-stu-id="5252a-148"><a href="mailto:Wei.A.Wang@nxp.com">Wei Wang</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="5252a-149"><a href="https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK">MCIMX8M-EVK</a></span><span class="sxs-lookup"><span data-stu-id="5252a-149"><a href="https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK">MCIMX8M-EVK</a></span></span></p></td>
<td align="left"></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="5252a-150"><a href="http://www.nxp.com/imx8mminievk">MCIMX8MMINI-EVK</a></span><span class="sxs-lookup"><span data-stu-id="5252a-150"><a href="http://www.nxp.com/imx8mminievk">MCIMX8MMINI-EVK</a></span></span></p></td>
<td align="left"></td>
</tr>
</tbody>
</table>
