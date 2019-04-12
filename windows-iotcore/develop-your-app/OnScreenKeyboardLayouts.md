---
title: 指定可用屏幕键盘语言布局
author: johntasler
ms.author: jtasler
ms.date: 09/12/2018
ms.topic: article
description: 了解如何指定该屏幕键盘语言布局可供 Windows IoT 设备的用户。
keywords: windows 10 IoT 核心版、 商业化，osk 屏幕键盘语言布局
ms.openlocfilehash: 003f280236733763b33f096f6574aad04921841f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510800"
---
# <a name="on-screen-keyboard-language-layouts"></a>屏幕键盘语言布局

> [!IMPORTANT]
> Windows 10 IoT 核心版 1809，截至本文不再适用。 请参阅[主设备的屏幕键盘](./OnScreenKeyboard.md)当前文档的页。

屏幕键盘 (OSK) 在 Windows 10 IoT Core，版本 1703年、 1709 和 1803，支持的语言版本如下布局：

| 语言标记  | 描述             | 布局代码 |
| :------------ | :---------------------- | -----------:|
| en-US         | 英语(美国) |    00000409 |
| en-AU         | 英语（澳大利亚）     |    00000C09 |
| en-CA         | 英语（加拿大）        |    00001009 |
| en-GB         | 英语 （英国） |    00000809 |
| es-ES         | 西班牙语(西班牙)         |    0000040A |
| es-MX         | 西班牙语(墨西哥)        |    0000080A |
| de-DE         | 德语                  |    00000407 |
| fr-CA         | 法语(加拿大)         |    00000C0C |
| fr-FR         | 法语(法国)         |    0000040C |
| it-IT         | 意大利语                 |    00000410 |
| pt-BR         | 葡萄牙语（巴西）     |    00000416 |

通过按住 OSK"& 123"按钮，用户可以选择他们想要使用哪种的布局：

![所有语言](../media/OnScreenKeyboard/AllLanguages.png)
 
但是，作为 OEM，可以限制哪些布局选项显示给用户。 若要限制向用户显示的布局，请首先引用的指导原则[TechNet 上的键盘布局 doucmentation](https://technet.microsoft.com/library/cc978687.aspx)。
 
有关具体示例，如果你想要仅允许北美语言布局 (EN-US、 EN-CA、 es-MX，fr CA)，可向 OEMCustomization.cmd 脚本中添加以下：

```console
call "%~dp0\setKeyboardLanguages.cmd"
```

其中 setKeyboardLanguages.cmd 是包含此相同的目录中的脚本：
 
```console
@echo off

set getDefaultAccountSID="wmic.exe useraccount where name='DefaultAccount' get sid"

for /F "tokens=2 usebackq delims== " %%s in (`%getDefaultAccountSID%`) do (
    set registryKey="HKEY_USERS\%%~s\Keyboard Layout\Preload"
    goto :setRegistry
  )
)
echo Unable to determine SID for DefaultAccount
goto :eof

:setRegistry
  echo on
  REG ADD %registryKey% /v "1" /d "00000409" /f
  REG ADD %registryKey% /v "2" /d "00001009" /f
  REG ADD %registryKey% /v "3" /d "0000080A" /f
  REG ADD %registryKey% /v "4" /d "00000C0C" /f
  @echo off
goto :eof
```

将上述命令脚本产生的效果：

![北美的语言](../media/OnScreenKeyboard/NorthAmericanLanguages.png)

### <a name="some-things-to-note"></a>需要注意一些事项：
*  值名称表示十进制序列。
*  值为字符串值 (REG_SZ)。
*  当然，无法直接到 OEMCustomization.cmd 脚本添加上面的脚本文本。
*  **不这样做**删除"预加载"注册表项，因为它具有对其设置为允许的权限屏幕键盘应用程序读取它的值。
*  适用，这些说明的一个先决条件是，你的映像必须包括以下功能 *:
   * IOT_SHELL_ONSCREEN_KEYBOARD
   * IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS

有关 IoT 功能的详细信息，请参阅[IoT Core 功能列表](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-feature-list)。
