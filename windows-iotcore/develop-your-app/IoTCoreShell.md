---
title: IoT 外壳概述
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何利用 IoT Shell 在设备上的导航之间导航。
keywords: windows iot, IoT core shell, 应用程序, 前台应用程序, 后台应用程序
ms.openlocfilehash: 74d8406036aa18dc5f8dcaa871e116eb7f8ec29b
ms.sourcegitcommit: beed912a2266d6dbc06a8a26b85ff49f1feffd69
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/21/2019
ms.locfileid: "67316632"
---
# <a name="iot-shell-overview"></a>IoT 外壳概述

本文档介绍 IoT Shell、前台和后台应用程序, 以及如何在设备上的这些应用程序之间导航。

## <a name="iot-shell-foreground-and-background-apps"></a>IoT Shell、前台和后台应用

IoT 核心设备运行 IoT Shell。 它具有许多责任, 但其主要任务是确保已启动注册的启动应用程序。 它有两种模式:头和无外设。 在头模式下, IoT Shell 将启动一个已注册的启动应用程序, 该应用程序将以全屏 (也称为应用) 显示其 UI。 向模式假设已连接屏幕并显示 UI。 在无外设模式下 (在[此处](../learn-about-hardware/HeadlessMode.md)有详细说明), 没有 UI;IoT Shell 仅启动后台应用程序。

前台和后台应用程序的主要区别如下:

- **前台应用程序**有一个 UI。 当设备处于头部模式时, 将在启动时启动其中的一个。 所有前台应用都注册到设备上, 用户可以在设备操作过程中在前台应用之间切换。

- **后台应用程序**没有 ui, 因此可以通过关闭 UI 堆栈来保存设备资源。 后台应用程序通常在启动时连续运行, 并经常用于监视设备。

## <a name="switching-between-apps-with-a-home-app"></a>使用 Home 应用在应用之间切换

目前, 启动应用允许你创建适用于 Windows 10 IoT Core 的家庭应用, 使你能够在不同的前台应用程序之间切换。 

**IoT 启动应用**([示例](https://github.com/microsoft/Windows-iotcore-samples/tree/master/Samples/IoTStartApp)代表一个简单的启动应用程序, 该应用程序在设备上列出已安装的应用, 然后使用 PackageManager api 启动一个应用。

## <a name="switching-between-apps-with-hid-injection-keys"></a>在具有 HID 注入密钥的应用之间切换

以下说明介绍了如何通过注册表项打开热键支持。 如果要构建自己的映像并想要支持以下热键 (Home、previous 应用和下一个应用) 而不需要访问注册表, 则可以包含一个可选功能包来处理这些步骤。

要查找的功能包称为:**Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package**和该功能称为**IOT_SHELL_HOTKEY_SUPPORT**。 有关示例, 请参阅[设置。热键示例包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml)。

本文档的其余部分介绍了如何手动实现此功能。

### <a name="return-home"></a>返回主页

使用 Windows 10 IoT 周年更新 (1607), 当另一个应用程序正在运行时, IoT Shell 支持将默认的应用程序窗口置于前台, 这会被设置为键盘上的 Windows 按钮的版本。 如果 IoT 设备上没有键盘, 并且需要通过[HID 注入](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection)注入低级键盘事件, 或者只是想要在应用程序中将 "中转 HOME" 功能重新映射到其他密钥, 则可以在注册表中调整密钥值。 例如, 若要启用 "转到主页", 请在注册表中输入以下命令:

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys” “HOME” QWORD    0x0000000 0000001B  
``

作为 REG 文件, 如下所示:

``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Home"=hex(b):1B,00,00,00,00,00,00,00
``

### <a name="switch-between-apps"></a>在应用之间切换

或者, 如果你想要在前台应用之间切换, 则可以通过在注册表中输入以下命令, 在映像中设置 Alt 选项卡 (下一个应用) 和 Shift-Alt-Tab (上一个应用) 功能:

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys”
“PREV” QWORD 0x00010000 00010009 
“NEXT” QWORD 0x00020000 00050009 
``

作为 REG 文件, 如下所示:``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``

### <a name="bit-translation"></a>位转换

上述 REG 文件项从左向右解码, 如下所示:

- Bits 0-15:虚拟键代码 (如1B、00用于转义)。 有关关键代码值的完整列表, 请参阅[虚拟键代码](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx)
- Bits 16-19:修改键。 0x0 = No 修饰符, 0x1 = ALT, 0x2 = CTRL, 0x4 = SHIFT。 组合键将值相加 (即 ALT + SHIFT 为 0x5)
- Bits 20-47:保留以供将来使用;必须为0
- Bits 48-62:操作
    - 0 = Home
    - 1 = 上一个视图 (在未来版本中可能不起作用)
    - 2 = 下一个视图 (在未来版本中可能不起作用)
- 位 63:保护必须为0

