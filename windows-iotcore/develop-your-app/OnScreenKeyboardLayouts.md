---
title: 指定可用的屏幕键盘语言布局
author: johntasler
ms.author: jtasler
ms.date: 09/12/2018
ms.topic: article
description: 了解如何指定可供 Windows IoT 设备的用户使用的屏幕键盘语言布局。
keywords: windows 10 IoT Core、商业化、osk 屏幕键盘语言布局
ms.openlocfilehash: 003f280236733763b33f096f6574aad04921841f
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169598"
---
# <a name="on-screen-keyboard-language-layouts"></a>屏幕键盘语言布局

> [!IMPORTANT]
> 从 Windows 10 IoT Core 版本 1809, 本文不再适用。 请参阅当前文档的 "[用于头设备的屏幕键盘](./OnScreenKeyboard.md)" 页。

Windows 10 IoT Core (版本1703、1709和 1803) 中的屏幕键盘 (OSK) 支持以下语言的布局:

| 语言标记  | 描述             | 布局代码 |
| :------------ | :---------------------- | -----------:|
| en-US         | 英语(美国) |    00000409 |
| en-AU         | 英语（澳大利亚）     |    00000C09 |
| en-CA         | 英语（加拿大）        |    00001009 |
| en-GB         | 英语 (英国) |    00000809 |
| es-ES         | 西班牙语(西班牙)         |    0000040A |
| es-MX         | 西班牙语(墨西哥)        |    0000080A |
| de-DE         | 德语                  |    00000407 |
| fr-CA         | 法语(加拿大)         |    00000C0C |
| fr-FR         | 法语(法国)         |    0000040C |
| it-IT         | 意大利语                 |    00000410 |
| pt-BR         | 葡萄牙语（巴西）     |    00000416 |

按住 OSK 的 "& 123" 按钮, 用户可以选择要使用的布局:

![所有语言](../media/OnScreenKeyboard/AllLanguages.png)
 
但作为 OEM, 你可以限制向用户显示哪些布局选项。 若要限制显示用户的布局, 请首先参考[TechNet 上的键盘布局 doucmentation](https://technet.microsoft.com/library/cc978687.aspx)中的指南。
 
对于具体的示例, 如果只想允许北美语言布局 (en-us、en CA、es MX、fr-CA), 则可以将以下内容添加到 OEMCustomization 脚本:

```console
call "%~dp0\setKeyboardLanguages.cmd"
```

其中, setKeyboardLanguages 是包含以下内容的同一目录中的脚本:
 
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

上述命令脚本生成的结果将为:

![北美语言](../media/OnScreenKeyboard/NorthAmericanLanguages.png)

### <a name="some-things-to-note"></a>需要注意的一些事项:
*  值名称指示小数序列。
*  值为字符串值 (REG_SZ)。
*  当然, 上述脚本文本可以直接添加到 OEMCustomization 脚本。
*  **请勿**删除 "预加载" 注册表项, 因为它对其设置了权限, 以允许屏幕键盘应用程序读取其值。
*  要使这些说明适用, 您的映像必须包含以下功能 *:
   * IOT_SHELL_ONSCREEN_KEYBOARD
   * IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS

有关 IoT 功能的详细信息, 请参阅[Iot 核心功能列表](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-feature-list)。
