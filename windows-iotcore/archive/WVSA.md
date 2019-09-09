---
title: 适用于 Arduino 的 Windows 虚拟屏蔽概述
author: saraclay
ms.author: saclayt
ms.date: 09/13/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解如何为 Arduino 设置 Windows 虚拟防护，并构建你的第一个 Windows 10 IoT Core 应用。
keywords: windows iot，WVSA，Windows 虚拟防护，Arduino，应用
ms.openlocfilehash: bd1dccd59fbc99de9076260f6e21b0ac1403660a
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168995"
---
> [!NOTE]
> 你正在查看存档的文档。 Windows 10 IoT 不再支持 AllJoyn。 如有问题，请在 GitHub 上提出问题，或在下面的评论中留下反馈。

# <a name="set-up-windows-virtual-shields-for-arduino"></a>为 Arduino 设置 Windows 虚拟屏蔽

## <a name="overview"></a>概述
如果使用了[Arduino](https://www.arduino.cc)，则很熟悉盾牌的概念。 每个盾牌都具有专门用途（例如温度盾牌、加速感应防护板），构建具有多个屏蔽的设备可能会很复杂、成本高且节省空间。 现在假设你可以使用低成本的 Windows Lumia Phone 作为一组精简的防护。 你的 Arduino 草图可以通过易于使用的库调用，在 Windows Phone 中访问数百美元的传感器和功能。

这正是用于开发人员的适用于 Arduino 库的 Windows 虚拟屏蔽。 这并不是最佳做法-这项技术在所有 Windows 10 设备上都有效，因此，您也可以在您的 PC 或表面上使用传感器和功能。 此外，Arduino 还可以将计算成本高昂的任务（例如语音识别和 web 分析）卸载到 Windows 10 配套设备上！

让我们了解如何设置硬件和软件，使其适用于 Arduino 的 Windows 虚拟防护板。


## <a name="1-get-your-windows-10-device-ready-for-developing-projects-using-windows-virtual-shields-for-arduino"></a>1.使用适用于 Arduino 的 Windows 虚拟防护板，让 Windows 10 设备准备好开发项目。

在本教程的此部分中，你将使用 Windows 虚拟 Arduino 应用程序加载它来准备你选择的 Windows 10 设备-此通用 Windows 应用程序允许你将设备用作 Arduino 板的 "虚拟盾牌"。  这会为制造商提供一些强大的功能，从而使他们能够利用语音识别、触摸屏和 Windows 的计算能力相对容易。

### <a name="hardware"></a>硬件
适用于 Arduino 应用程序的 Windows 虚拟防护板可在任何 Windows 10 设备上运行，但本教程将使用 Windows Phone 说明安装程序。

*所需内容*Windows Phone 运行 Windows 10-建议[Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520)或[Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635)。

*设置 Windows Phone*

如果你的电话还没有运行 Windows 10，则可以选择安装软件的预览版本。  Windows Phone 8 用户可以访问 Microsoft Store 应用下载 "Windows 预览体验" 应用程序-此应用允许用户选择接收 Windows 10 Technical preview 作为更新。  打开应用后，请按照提示和说明操作，并在手机成功运行 Windows 10 后继续操作。

### <a name="software"></a>软件

有两个选项可用于在 Windows Phone 上安装适用于 Arduino UWP 应用的 Windows 虚拟屏蔽。  下载应用程序是更简单、更快速的选择。

* 从 Microsoft Store 下载应用
* 使用电脑和 Visual Studio 旁加载应用

*选项 1：从 Microsoft Store 下载应用*

单击此[链接](https://www.microsoft.com/store/apps/9nblgggz0mld)可访问 Arduino 的 Windows 虚拟防护板的 "Microsoft Store" 页，下载应用程序，然后安装。 然后，打开应用程序以确保它可以正常运行。  现在，你的设备将被设置为用于 Arduino 的 "虚拟盾牌"！  你可以进入下一页。

*选项 2：使用电脑和 Visual Studio*
旁加载应用程序所需的_内容_
* Visual Studio 2017 将适用于 Arduino 应用程序的 Windows 虚拟防护旁加载到开发人员解锁的手机上。
* 此[存储库](https://github.com/ms-iot/virtual-shields-universal)包含适用于 Arduino 应用程序的 Windows 虚拟防护板的代码。  在本地磁盘上克隆存储库或将其下载为 ZIP。  如果你不熟悉 git 并想要执行适当的克隆，请按照[此处](https://help.github.com/articles/cloning-a-repository)的说明进行操作。

_设置 Visual Studio 2017_
1. 通过[dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads)中的 Windows 10 开发人员预览版工具安装 Visual Studio 2017。  建议使用免费的适用于 Visual Studio 的社区版本，但 Enterprise 和 Professional 都适用。  如果已安装 Visual Studio，请跳到下一步。
2. 在 Visual Studio 中，从上面 "需要的内容" 部分下载的存储库中加载一个盾牌。
3. 确保 Windows 10 设备（在这种情况下为 Windows Phone）由开发人员解除锁定。 [本页说明如何](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx)解锁8.1、8和 7.1 Windows Phone;但对于 Windows 10 手机，步骤是相同的。
4. 将 Windows 10 设备插入到计算机中，并将盾牌程序部署到设备。  为此，请部署到 "本地计算机"，并确保将设备体系结构设置为 "ARM"。
5. 在手机上运行用于 Arduino 应用程序的新安装的 Windows 虚拟防护，以确保部署成功。  现在，你的 Windows 10 设备将设置为用作虚拟盾牌！

## <a name="2-set-up-your-arduino-to-use-the-windows-virtual-shields-for-arduino-library"></a>2.将 Arduino 设置为使用 Windows 虚拟防护 Arduino 库 
在正确设置 Windows 10 配套设备后，让我们的 Arduino 准备好使用 Windows 虚拟防护 Arduino 库。 可以通过 USB、Bluetooth 或 Wi-fi 在 Arduino 和 Windows 10 "虚拟盾牌" 之间建立连接。 本特定教程将介绍如何使用蓝牙连接完成安装程序，但可随意试用其他选项。

### <a name="hardware"></a>硬件
*所需内容*
* Arduino Uno 或兼容设备
* 线路连接
* 用于上传 Arduino 草图的电脑
* 标准 A 到标准 B USB-需要将草图上传到 Arduino 设备
* 可选：仅当你选择通过蓝牙进行连接时，才需要使用蓝牙模块。
* 可选：仅当你选择通过 wi-fi 进行连接时，才需要使用 wi-fi 模块。

* 设置 Arduino
* 如有必要，请准备好蓝牙模块（蓝牙模块可能需要在其上附加标题）。
* 除了下面所述的不同之外，每个[接线图](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup)将蓝牙模块连接到 Arduino。

  * 效果使用0和1，而不是2和3：
    * 蓝牙 TX 应连接到 pin 0 （Arduino RX 或 RX0）。
    * 蓝牙 RX 应连接到 pin 1 （Arduino TX 或 TX1）。

### <a name="software"></a>软件
*所需内容*
* Arduino IDE 1.6 或更高
* ArduinoJSON 库
* [此存储库](https://github.com/ms-iot/virtual-shields-arduino)，其中包含将在 Arduino 上运行的示例草图。

*设置 Arduino IDE*
* 下载并安装 Arduino IDE，然后启动程序。
* 验证是否在 "*工具 > 板*" 下选择了正确的 Arduino 板。
* 验证是否在 "*工具 > 端口*" 下选择了正确的 COM 端口。 该板的名称应显示在每个选项旁边，使选择正确的选项变得更加容易。

*设置 ArduinoJSON 库*
* 从 [ArduinoJson 存储库](https://github.com/bblanchon/ArduinoJson)中，克隆存储库或下载压缩文件。
* 将整个存储库放入库文件夹（即`Documents\Arduino\libraries\ArduinoJson\`）。

*为 Arduino 库设置 Windows 虚拟屏蔽*
* 克隆[此存储库](https://github.com/ms-iot/virtual-shields-arduino)或下载 ZIP。 如果你不熟悉 git 并想要执行适当的克隆，请按照[此处](https://help.github.com/articles/cloning-a-repository/)的说明进行操作。
* 将位于刚下载的存储库的 "Arduino\Libraries" 文件夹中的 "VirtualShield" 文件夹复制到 Arduino 库文件夹（即`Documents\Arduino\libraries\VirtualShield\`）。

*测试您的设置*
* 在 Arduino IDE 中，转到菜单项*文件-> 示例-> 虚拟盾牌 > HelloWorld*。 这应该会根据我们在本教程中使用的 Hello World 示例来加载语音识别。
* 将该草绘上传到 Arduino 之前，请暂时从 Arduino 中删除蓝牙 TX 和 RX 线路（USB 和蓝牙之间仅共享一个串行端口，蓝牙与上传干扰）。
* 按 IDE 中的 "上传" 按钮上载该草绘。
* 将蓝牙 TX 和 RX 线路替换为 Arduino 的 pin （蓝牙 TX to Arduino RX （或 RX0），并将蓝牙 RX 替换为 Arduino TX 或（TX1））。
* 在之前的页面（或其他 Windows 设备）上，在 "蓝牙" 设置中与 Arduino 上的蓝牙设备配对。 如果使用的是 BlueSMiRF，则默认 pin 代码为1234。 

> [!NOTE]
> 配对成功后，BlueSMiRF 上的红色闪烁灯会继续闪烁红色。 这是预期情况。 在连接到 Arduino 应用程序的 Windows 虚拟屏蔽后，它只会关闭绿色。


## <a name="3-write-your-first-app-hello-blinky"></a>3.编写第一个应用：你好，Blinky！ 

### <a name="hello-world-speech-enabled-led-example"></a>Hello World 支持语音的 LED 示例
将你的 Windows Phone（或任何可能的 Windows 10 设备！）和 Arduino 按本教程的上述步骤准备就绪后，你现在便可以试用我们的示例。

1. 通过将带有电阻器的 LED 连接到引脚 8 来准备你的 Arduino 开发板。
2. 确保你的 Arduino 仍然上载有 HelloWorld-Speech-Eventing 示例，然后将 Arduinos 插入电源。
3. 在你以前准备的 Windows Phone 上运行 Windows Virtual Shields for Arduino 应用。
4. 如果正确完成所有设置，你的手机应连接到 Arduino 草图并使用音频提示欢迎你。 你现在可以通过向 Windows 10 设备说出“打开”或“关闭”来打开和关闭 Arduino 上的 LED！

### <a name="arduino-wiring-sketch-hello-world-example"></a>Arduino 接线图素描：Hello World 示例

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


