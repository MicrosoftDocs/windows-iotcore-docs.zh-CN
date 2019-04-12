---
title: Windows 虚拟 Shields 为 arduino 开发概述
author: saraclay
ms.author: saclayt
ms.date: 09/13/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解如何设置 arduino 开发 Windows 虚拟 Shields 并生成首个 Windows 10 IoT 核心版应用。
keywords: windows iot，WVSA，Windows 虚拟 Shields，Arduino，应用程序
ms.openlocfilehash: bd1dccd59fbc99de9076260f6e21b0ac1403660a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510837"
---
> [!NOTE]
> 你正在查看存档的文档。 Windows 10 IoT 不再支持 AllJoyn。 如有问题，请打开在 GitHub 上或在下面的注释中留下反馈。

# <a name="set-up-windows-virtual-shields-for-arduino"></a>为 Windows 虚拟 Shields 设置 arduino 开发

## <a name="overview"></a>概述
如果使用过[Arduino](https://www.arduino.cc)，您熟悉使用防护的概念。 每个防火墙具有专门的用途 （例如温度防护罩，加速感应器防护罩），并生成具有多个 shields 的设备会很复杂，成本高昂，而且空间效率低下。 现在，假设您可以为一组精简 shields 使用成本较低 Windows Lumia 手机。 Arduino 草图将能够通过易于使用库调用访问数百个传感器以及 Windows Phone 中的功能值得美元。

这正是 Windows 虚拟 Shields Arduino 库使开发人员。 并不是最好的部分-这一技术可所有 Windows 10 设备，因此您可以使用传感器和功能在电脑或图面上也。 此外，Arduino 可以卸载占用计算资源的任务，如语音识别和 web 到 Windows 10 伴侣设备分析 ！

让我们了解如何设置硬件和软件以使用 Windows 虚拟 Shields 适用于 arduino 开发。


## <a name="1-get-your-windows-10-device-ready-for-developing-projects-using-windows-virtual-shields-for-arduino"></a>1.使你的 Windows 10 设备可供开发使用 Windows 虚拟 Shields 适用于 Arduino 的项目。

在本教程的此部分中，你将通过使用 Arduino 应用程序的 Windows 虚拟防护加载它准备所选的 Windows 10 设备-此通用 Windows 应用程序，可使用你的设备作为"虚拟盾牌"arduino 开发板。  此结果中的创建者，从而允许它们使用语音识别某些强有力的可能性相对轻松地触摸屏幕和 Windows 的计算能力。

### <a name="hardware"></a>硬件
Windows 虚拟 Shields Arduino 应用程序可以在任何 Windows 10 设备上运行，但本教程将介绍与 Windows Phone 安装程序。

*所需*Windows Phone 运行 Windows 10-我们建议[Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520)或[Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635)。

*设置 Windows Phone*

如果你的手机已不在运行 Windows 10，有选项来安装软件的预览版本。  Windows Phone 8 用户可以转到下载"Windows Insider"应用程序的 Microsoft Store 应用-使用此应用，用户可以选择接收作为更新的 Windows 10 Technical Preview。  按照提示和打开应用时的说明操作并继续您的电话已成功运行 Windows 10 后。

### <a name="software"></a>软件

有两个选项可用于在 Windows Phone 上安装 arduino 开发 UWP 应用的 Windows 虚拟防护。  下载应用程序是更轻松、 更快的选择。

* 从 Microsoft Store 下载应用
* 旁加载应用使用 PC 和 Visual Studio

*选项 1：从 Microsoft Store 下载应用*

按照这[链接](https://www.microsoft.com/store/apps/9nblgggz0mld)到 Windows 虚拟 arduino Shields 的 Microsoft Store 页上，下载该应用程序，并安装。 然后，打开应用程序以确保它可以正常运行。  你的设备现在已设置为用作 Arduino"虚拟盾牌"！  你可以转到下一页。

*选项 2：旁加载应用使用 PC 和 Visual Studio*
_所需内容_
* 旁加载 Windows 虚拟 Shields 的 Arduino 应用程序应用到开发人员解锁手机的 visual Studio 2017。
* 这[存储库](https://github.com/ms-iot/virtual-shields-universal)的 Windows 虚拟 Shields Arduino 应用程序中包含的代码。  克隆存储库，或者以本地磁盘上的 zip 格式下载它。  如果您不熟悉 git，并想要执行的正确克隆，按照的说明[此处](https://help.github.com/articles/cloning-a-repository)。

_设置 Visual Studio 2017_
1. 使用 Windows 10 开发人员预览版工具从安装 Visual Studio 2017 [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads)。  我们建议免费社区版本的 Visual Studio 中，但也可以 Enterprise 和 Professional。  如果已安装 Visual Studio，请跳到下一步。
2. 在 Visual Studio 中，负载 Shield.sln 从存储库下载在"你需要什么"一节。
3. 请确保 Windows 10 设备 （在本例中为 Windows Phone） 是开发人员解锁。 [此页](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx)介绍了如何解锁 Windows Phone 8.1、 8 和 7.1; 但是，步骤是相同的适用于 Windows 10 手机。
4. 在 Windows 10 设备插入计算机并将 Shield.sln 程序部署到你的设备。  若要执行此操作，将部署到"本地计算机"并确保设置"ARM"作为设备的体系结构。
5. 运行新安装 Arduino 应用程序在手机上，以确保部署的 Windows 虚拟防护已成功完成。  在 Windows 10 设备现在已设置要用作虚拟防护罩 ！

## <a name="2-set-up-your-arduino-to-use-the-windows-virtual-shields-for-arduino-library"></a>2.设置在 Arduino，Arduino 库要使用的 Windows 虚拟 Shields 
与我们的 Windows 10 伴侣设备正确设置，让我们开始我们 Arduino Arduino 库要使用的 Windows 虚拟 Shields。 您可以通过 USB、 蓝牙或 Wi-fi 在 arduino 开发和 Windows 10"虚拟盾牌"之间建立连接。 本特定教程将介绍如何完成安装程序使用蓝牙连接，但随意尝试其他选项。

### <a name="hardware"></a>硬件
*需要具备的条件*
* Arduino Uno 或兼容的设备
* 连线
* 用于上传 Arduino 草图 PC
* 与标准 B USB-将草图上传到你的 Arduino 设备所需的标准 A
* 可选：蓝牙模块-如果选择通过蓝牙连接，才需要。
* 可选：Wi-fi 模块-如果你选择的 wi-fi 连接，才需要。

* 设置 Arduino
* 如有必要，请准备好蓝牙模块（蓝牙模块可能需要在其上附加标题）。
* 除不同如下所示，连接到每个 Arduino 蓝牙模块[线图表](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup)。

  * 差异：使用而不是 2 和 3 引脚 0 和 1:
    * 蓝牙 TX 应连接到 pin 0 （Arduino RX 或 RX0）。
    * 蓝牙 RX 应连接到 1 （Arduino TX 或 TX1） 的 pin。

### <a name="software"></a>软件
*需要具备的条件*
* Arduino IDE 版本 1.6 或更高
* ArduinoJSON 库
* [此存储库](https://github.com/ms-iot/virtual-shields-arduino)，其中包含将在 Arduino 上运行该示例草图。

*设置 Arduino IDE*
* 下载并安装 Arduino IDE 中，然后启动程序。
* 验证是否具有正确的 arduino 开发板下选择*工具 > 板*。
* 请确保您有下选择了正确的 COM 端口*工具 > 端口*。 每个选项，使其更易于选择正确的选项旁边应显示的看板的名称。

*设置 ArduinoJSON 库*
* 从 [ArduinoJson 存储库](https://github.com/bblanchon/ArduinoJson)中，克隆存储库或下载压缩文件。
* 将整个存储库放入您的库文件夹 (即`Documents\Arduino\libraries\ArduinoJson\`)。

*为 Windows 虚拟 Shields 设置 Arduino 库*
* 克隆[此存储库](https://github.com/ms-iot/virtual-shields-arduino)或下载 zip 文件。 如果您不熟悉 git，并想要执行的正确克隆，按照的说明[此处](https://help.github.com/articles/cloning-a-repository/)。
* 复制"VirtualShield"文件夹，你只需下载，请到 Arduino 库文件夹的存储库的"Arduino\Libraries"文件夹中找到 (即`Documents\Arduino\libraries\VirtualShield\`)。

*测试设置*
* 从 Arduino IDE 中，转到菜单项*文件-> 示例-> 虚拟盾牌-> 事件处理语音 HelloWorld*。 这应加载的语音识别基于 Hello World 示例，我们使用在本教程。
* 上载到你 Arduino 草图之前, 暂时移除蓝牙 TX 和 RX 电线的 Arduino （只有一个 USB 和蓝牙-蓝牙之间共享的串行端口会影响上传没有）。
* 通过在 IDE 中按"上传"按钮上, 传草图。
* 替换为蓝牙 TX 和 RX 电线到 arduino 开发插针 (蓝牙 TX 到 arduino 开发 RX （或 RX0） 和蓝牙到 arduino 开发 TX RX 或 (TX1))。
* 在手机 （或其他 Windows 设备） 上你准备在上一页上，在 arduino 开发中的蓝牙设置上的蓝牙设备配对。 如果使用的 BlueSMiRF，默认 pin 代码是 1234年。 

> [!NOTE]
> 配对成功后，BlueSMiRF 上的红色闪烁灯会继续闪烁红色。 这是预期情况。 它仅将变为绿色后使用 Windows 虚拟 Shields Arduino 应用程序进行连接。


## <a name="3-write-your-first-app-hello-blinky"></a>3.编写第一个应用：Hello，灾难从天而降 ！ 

### <a name="hello-world-speech-enabled-led-example"></a>Hello World 支持语音的 LED 示例
将你的 Windows Phone（或任何可能的 Windows 10 设备！）和 Arduino 按本教程的上述步骤准备就绪后，你现在便可以试用我们的示例。

1. 通过将带有电阻器的 LED 连接到引脚 8 来准备你的 Arduino 开发板。
2. 确保你的 Arduino 仍然上载有 HelloWorld-Speech-Eventing 示例，然后将 Arduinos 插入电源。
3. 在你以前准备的 Windows Phone 上运行 Windows Virtual Shields for Arduino 应用。
4. 如果正确完成所有设置，你的手机应连接到 Arduino 草图并使用音频提示欢迎你。 你现在可以通过向 Windows 10 设备说出“打开”或“关闭”来打开和关闭 Arduino 上的 LED！

### <a name="arduino-wiring-sketch-hello-world-example"></a>Arduino 草图绑定：Hello World 示例

```C++
#include <ArduinoJson.h>

#include <VirtualShield.h>
#include <Text.h>
#include <Speech.h>
#include <Recognition.h>

VirtualShield shield;             // identify the shield
Text screen = Text(shield);       // connect the screen
Speech speech = Speech(shield);   // connect text to speech
Recognition recognition = Recognition(shield);    // connect speech to text

int LED_PIN = 8;

void recognitionEvent(ShieldEvent* event)
{
  if (event->resultId > 0) {
    digitalWrite(LED_PIN, recognition.recognizedIndex == 1 ? HIGH : LOW);
    screen.printAt(4, "Heard " + String(recognition.recognizedIndex == 1 ? "on" : "off"));
    recognition.listenFor("on,off", false);     // reset up the recognition after each event
  }
}

// when Bluetooth connects, or the 'Refresh' button is pressed
void refresh(ShieldEvent* event)
{
  String message = "Hello Virtual Shields. Say the word 'on' or 'off' to affect the LED";

  screen.clear();
  screen.print(message);
  speech.speak(message);

  recognition.listenFor("on,off", false);   // NON-blocking instruction to recognize speech
}

void setup()
{
  pinMode(LED_PIN, OUTPUT);
  pinMode(LED_PIN, LOW);

  recognition.setOnEvent(recognitionEvent); // set up a function to handle recognition events (turns auto-blocking off)
  shield.setOnRefresh(refresh);

  // begin() communication - you may specify a baud rate here, default is 115200
  shield.begin();
}

void loop()
{
  shield.checkSensors();            // handles Virtual Shield events.
}
```


