---
title: 建议的原型板
ms.date: 04/17/2018
ms.topic: article
description: 了解建议用于 Windows 10 IoT 的原型板。
keywords: windows iot, 开发设备, 板, Raspberry Pi 2, Raspberry Pi 3, Minnowboard Max, Dragonboard
ms.openlocfilehash: d1dde3bf04622dfdbdc611fcca96f3fdd3cfae3c
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721882"
---
# <a name="suggested-prototype-boards"></a>建议的原型板

## <a name="windows-10-iot-core-development-devices"></a>Windows 10 IoT 核心版开发设备
下面你会发现我们建议的用于 Windows 10 IoT 核心版入门的板。 这些板提供完整闪存更新 (FFU) 映像，通过现成的映像加快原型制作的速度，使得 Windows 10 IoT 核心版的刷写过程变得很轻松。

> [!IMPORTANT]
> 如果计划将设备商业化，你必须创建自己的映像，不得使用下面提供的映像。

> [!NOTE]
> Raspberry Pi 3B+ 与 Windows 10 IoT 核心版有限兼容。 有关详细信息，请查看[发行说明](https://docs.microsoft.com/windows/iot-core/release-notes/insider/rpi3bp)。 如需更完整的 Windows 10 IoT 核心版体验，请使用 Raspberry Pi 3B、DragonBoard、Up2 板或 NXP 设备。 


| 板 | 详细信息 | FFU 链接 | 如何设置 | 入门 |
|-----------|----------|---------|---------|---------|---------|-------|
| [AAEON Up Squared](https://up-board.org/upsquared/specifications/) | [Up Board 站点](https://up-shop.org/28-up-squared) | [下载 FFU](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) | [设置 Intel 设备](https://docs.microsoft.com/windows/iot-core/tutorials/intel) | [商业化](https://up-shop.org/home/270-up-squared.html) | 
| [DragonBoard 410c](https://developer.qualcomm.com/hardware/dragonboard-410c) | [Arrow 站点](https://www.arrow.com/en/products/dragonboard410c/arrow-development-tools) | [下载 FFU](https://www.microsoft.com/software-download/windows10IoTCore#!) | [设置 Dragonboard](https://docs.microsoft.com/windows/iot-core/tutorials/dragonboard)、<br>[设置 Qualcomm 设备](https://docs.microsoft.com/windows/iot-core/tutorials/qualcomm) | [商业化](https://www.arrow.com/en/products/dragonboard410c/arrow-development-tools) | 
| [Keith & Koep i-PAN M7 CoverLens](https://keith-koep.com/de/produkte/produkte-hmi/i-pan-m7-coverlens-arm-touch-panel-pc-eigenschaften/) | [Keith & Koep 站点](https://keith-koep.com/de/produkte/produkte-hmi/i-pan-m7-coverlens-arm-touch-panel-computer-technische-daten/) | [下载 FFU](https://support.keith-koep.com/service/doku.php/service/winiot/images) | [Keith & Koep Wiki](https://support.keith-koep.com/service/doku.php/service/hardware/panel/ipanm7) | [i-PAN M7 CoverLens 初学者工具包](https://keith-koep.com/de/produkte/produkte-eval-kits/i-pan-m7-coverlens-starter-kit-technische-daten/) | 
| [Keith & Koep i-PAN T7 CoverLens](https://keith-koep.com/de/produkte/produkte-hmi/i-pan-t7-coverlens-arm-touch-panel-pc-eigenschaften/) | [Keith & Koep 站点](https://keith-koep.com/de/produkte/produkte-hmi/i-pan-t7-coverlens-arm-touch-panel-computer-technische-daten/) | [下载 FFU](https://support.keith-koep.com/service/doku.php/service/winiot/images) | [Keith & Koep Wiki](https://support.keith-koep.com/service/doku.php/service/hardware/panel/ipant7) | [i-PAN T7 CoverLens 评估工具包](https://keith-koep.com/de/produkte/produkte-eval-kits/i-pan-t7-coverlens-eval-kit-technische-daten/) | 
| [MinnowBoard Turbot](https://minnowboard.org) | [Minnowboard 站点](https://minnowboard.org/get-a-board) | [下载 FFU](https://www.microsoft.com/software-download/windows10IoTCore#!) | [设置 MinnowBoard](https://docs.microsoft.com/windows/iot-core/tutorials/minnowboard) | N/A |
| [NXP i.MX 6](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors:IMX6X_SERIES) | [NXP 站点](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors:IMX6X_SERIES) | [下载 FFU](https://github.com/ms-iot/imx-iotcore) | [设置 NXP 设备](https://docs.microsoft.com/windows/iot-core/tutorials/nxp) | [商业化](https://www.solid-run.com/nxp-family/hummingboard/imx6-win-10-iot-core/) | 
| [NXP i.MX 7](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-7-processors:IMX7-SERIES) | [NXP 站点](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-7-processors:IMX7-SERIES) | [下载 FFU](https://github.com/ms-iot/imx-iotcore) | [设置 NXP 设备](https://docs.microsoft.com/windows/iot-core/tutorials/nxp) | [商业化](https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/) | 
| [NXP i.MX 8M/8M Mini](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-8-processors:IMX8-SERIES) | [NXP 站点](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-8-processors:IMX8-SERIES) | [下载 FFU](https://github.com/ms-iot/imx-iotcore) | [设置 NXP 设备](https://docs.microsoft.com/windows/iot-core/tutorials/nxp) | [8M 开发工具包](https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK)或 [8M Mini 开发工具包](https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-mini-applications-processor:8MMINILPD4-EVK) |
| [Raspberry Pi 2](https://www.raspberrypi.org/products/raspberry-pi-2-model-b/)<br> （1.2 不受支持） | [Raspberry Pi 站点](https://www.raspberrypi.org/products/raspberry-pi-2-model-b/) | [下载 FFU](https://www.microsoft.com/software-download/windows10IoTCore#!) | [设置 Raspberry Pi](https://docs.microsoft.com/windows/iot-core/tutorials/rpi) | [Adafruit 工具包](https://docs.microsoft.com/windows/iot-core/tutorials/adafruitkit) | 
| [Raspberry Pi 3B](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/)<br> （3B+ 是不受支持的技术预览版） | [Raspberry Pi 站点](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/) | [下载 FFU](https://www.microsoft.com/software-download/windows10IoTCore#!) | [设置 Raspberry Pi](https://docs.microsoft.com/windows/iot-core/tutorials/rpi) | [Adafruit 工具包](https://docs.microsoft.com/windows/iot-core/tutorials/adafruitkit) |
