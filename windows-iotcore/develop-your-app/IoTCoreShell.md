---
title: IoT Shell 概述
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何利用 IoT 外壳程序，以在设备上的导航之间导航。
keywords: windows iot，IoT core 命令行程序、 应用程序、 前台应用程序、 后台应用程序
ms.openlocfilehash: be72fabc91fc5748a029b61ebd9a306deb23f726
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510875"
---
# <a name="iot-shell-overview"></a>IoT Shell 概述

本文档介绍 IoT Shell、 前景色和背景的应用程序，以及如何在设备上这些应用程序之间浏览。

## <a name="iot-shell-foreground-and-background-apps"></a>IoT Shell、 前景和背景应用

IoT Core 设备运行 IoT Shell。 它有许多职责，但它主要工作是确保已注册的启动应用的启动。 它有两种模式：主和无外设。 在 Headed 模式下，IoT 命令行程序将启动一个单个已注册的启动应用，它将显示其 UI 在全屏幕模式 （也称为 Headed 应用）。 主的模式假定你已连接的屏幕，并显示 UI。 在无外设模式下 (详细信息中所述[此处](../learn-about-hardware/HeadlessMode.md))，没有用户界面; IoT Shell 启动后台应用程序。

下面是前景色和背景的应用程序之间的主要区别：

- **前台应用程序**具有用户界面。 其中一种在启动时在设备处于主模式启动。 在设备上注册所有前台应用程序和用户可以在设备操作期间的前台应用程序之间进行切换。

- **后台应用程序**不具有 UI，并关闭 UI 堆栈，因此将保存设备资源。 后台应用程序通常从启动连续运行，并通常用于监视设备。

## <a name="switching-between-apps-with-a-home-app"></a>与主应用程序的应用之间切换

目前，启动应用，可创建适用于 Windows 10 IoT Core，可用于不同前台应用程序间切换主应用。 

**IoT 启动应用程序**([示例](https://developer.microsoft.com/en-us/windows/iot/samples/iotstartapp)表示一个简单的启动应用，它列出在设备上已安装的应用，然后启动一个使用 PackageManager Api。

## <a name="switching-between-apps-with-hid-injection-keys"></a>应用与 HID 注入密钥之间切换

以下说明介绍如何打开热键支持通过对注册表项。 如果你要构建自己的映像，并想要支持如下而无需访问注册表的热键 （主页、 以前的应用和下一个应用程序），则可以为你处理这些步骤的可选功能包。

调用要查找的功能包：**Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab**和功能被称为**IOT_SHELL_HOTKEY_SUPPORT**。 请参阅[Settings.HotKey 示例包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml)有关的示例。

此文档的其余部分介绍如何手动实现此功能。

### <a name="return-home"></a>返回主页

借助 Windows 10 IoT 周年更新 (1607)，IoT Shell 支持到前台，将默认应用程序窗口，运行时，另一个应用程序是通过按"主页转"键，它设置为版本的键盘上的 Windows 按钮。 如果没有 IoT 设备上有键盘并需要将注入通过低级别的键盘事件[HID 注入](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection)，或者如果只是想要重新映射到不同的密钥应用程序中的"转到主页"功能，您可以调整中的密钥值注册表。 例如，若要启用按转义符键 (0x1B) 到"主页转"，请在注册表中输入以下命令：

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys” “HOME” QWORD    0x0000000 0000001B  
``

为 REG 文件，这种情况，如下所示：

``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Home"=hex(b):1B,00,00,00,00,00,00,00
``

### <a name="switch-between-apps"></a>应用程序之间切换

或者，如果你想要在前台应用之间切换，您可以将设置 Alt Tab （下一步应用） 和 Shift Alt Tab （以前的应用） 功能通过在注册表中输入以下命令在映像中：

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys”
“PREV” QWORD 0x00010000 00010009 
“NEXT” QWORD 0x00020000 00050009 
``

为 REG 文件，这种情况，如下所示：
``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``

### <a name="bit-translation"></a>位转换

上面的 REG 文件条目解码从左到右，如下所示：

- 位 0 到 15:虚拟键代码 (即 1B，00 转义)。 请参阅[虚拟键代码](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx)键代码的值的完整列表
- Bits 16-19:修改键。 0x0 = 无修饰符 0x1 = ALT，0x2 = CTRL 和 0x4 = SHIFT。 组合密钥相加值 （即 ALT + SHIFT 是 0x5）
- Bits 20-47:保留供将来使用;必须为 0
- Bits 48 62:操作
    - 0 = 主页
    - 1 = 上一个视图 （可能无法在未来版本中）
    - 2 = 下一个视图 （可能无法在未来版本中）
- 第 63 位：保留;必须为 0

