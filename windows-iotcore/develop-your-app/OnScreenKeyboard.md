---
title: 通过 Windows 10 IoT Core 屏幕键盘配置头设备
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
description: 了解新的屏幕键盘, 以及如何在 Windows 10 IoT Core, 版本1809中对其进行配置。
keywords: Windows 10 IoT Core, touch, 键盘, osk, 屏幕, 屏幕, sip, 输入, ime, 头, 听写, 语音, 语音
ms.custom: RS5
ms.openlocfilehash: 100aeb484690c462deac56dcadf7d17667487ae2
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169205"
---
# <a name="on-screen-keyboard-for-headed-devices"></a>用于头设备的屏幕键盘

在 Windows 10 IoT Core 版本1809中, 屏幕键盘组件发生了重大变化, 更好! IoT Core 现在使用与桌面版 Windows 相同的触摸键盘组件。

## <a name="new-features"></a>新增功能
新的键盘实现为你的设备开发提供以下好处:

* [整个 Windows 键盘语言布局集](#windows-keyboard-language-layouts)
* [支持输入范围 (例如, 电子邮件地址、数字 PIN、搜索字段等)](#support-for-input-scopes)
* [输入法编辑器 (IME)](#input-method-editor-ime)
* [不隐藏的文本输入字段](#non-obscured-text-input-fields)
* [听写模式](#dictation-mode)
* [用户界面首选项的选择](#user-interface-configuration)

## <a name="feature-packages"></a>功能包

对于原型设计 (开发) 映像, 已包括屏幕键盘功能, 但需要在[Windows 设备门户](../manage-your-device/deviceportal.md#iot-specific-features)中从设备设置启用该功能。

对于商业化, 以下可选功能包会将屏幕键盘添加到映像:
* IOT_SHELL_ONSCREEN_KEYBOARD
* IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS

> [!TIP]
> 有关 IoT 核心功能的详细信息, 请参阅[Iot 核心功能列表](/windows-hardware/manufacture/iot/iot-core-feature-list)和[iot 核心制造指南](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。

## <a name="windows-keyboard-language-layouts"></a>Windows 键盘语言布局

在此版本中, 支持的语言布局已扩展为包括桌面 Windows 版本中可用的完整集。 若要允许用户在不同的语言布局之间进行选择, 通常应在应用程序的 "设置" 区域中包括选择 UI。 提供以下 API 是为了使应用程序能够设置屏幕键盘将使用的语言:

[Windows TrySetInputMethodLanguageTag](/uwp/api/windows.globalization.language.trysetinputmethodlanguagetag)

可在[LanguageManager.cs](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/IoTCoreDefaultApp/CS/IoTCoreDefaultApp/Presenters/LanguageManager.cs)文件中的[IoTCoreDefaultApp 示例应用程序](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp)中查看此 API 的示例。

## <a name="support-for-input-scopes"></a>支持输入范围

在以前的版本中, 只有 EmailSmtpAddress 输入范围可用。 在此版本中, 提供了一组完整的输入范围。 以下主题介绍输入范围以及如何在你的应用程序中使用它们:

[使用输入范围更改触摸键盘](/windows/uwp/design/input/use-input-scope-to-change-the-touch-keyboard)

## <a name="input-method-editor-ime"></a>输入法编辑器 (IME)

此版本提供了一个输入法编辑器, 该编辑器对于比键盘上的键 (例如中文、日语和韩语) 具有更多 graphemes 的任何语言都是必需的。

## <a name="non-obscured-text-input-fields"></a>不隐藏的文本输入字段

在以前的版本中, 触摸键盘可能会掩盖重点文本字段, 使用户无法看到他们所键入的内容。 此版本通过自动将文本字段滚动到视图中来解决此问题, 因此它不再被触摸键盘遮盖。

## <a name="dictation-mode"></a>听写模式

如果输入语言设置为 OS 语言 (默认值), 则语音识别输入功能可用。
若要在键盘中显示听写按钮, 请参阅以下有关[用户界面配置](#user-interface-configuration)的部分。

## <a name="user-interface-configuration"></a>用户界面配置

屏幕键盘为其用户界面提供了多个可配置选项。 这些配置通过注册表进行配置。
在开发过程中, 可以使用[PowerShell](/windows/iot-core/connect-your-device/powershell)或[安全外壳 (SSH)](/windows/iot-core/connect-your-device/ssh)。 对于创建 OEM 映像, 用于设置注册表值的首选机制是此处讨论`OEMInput.xml`的文件:

[运行时自定义](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)

> [!NOTE]
> 此处所述的大部分注册表设置将在屏幕键盘可见时生效。
> 这使你可以在开发过程中轻松尝试不同的设置值 combinatations, 并立即实时查看所产生的更改。 如果某个设置不会立即生效, 你将需要重新启动设备, 才能查看对键盘 UI 所做的更改。

### <a name="keyboard-height"></a>键盘高度

默认情况下, 触摸键盘将使用屏幕高度的 45%。 这可能会在设备上显得太大或太小, 具体取决于其大小和分辨率。 最大可将高度调整到屏幕高度的三分之二。 不在范围内的任何值都将限制为范围。 因为这被指定为浮点值, 所以它允许像素级别的精度。 只需应用以下公式即可计算百分比:

`percentage = (100 * <desired_pixel_height>) / <screen_height>`

例如, 要将高度更改为 56.783%, 请设置以下注册表值:
```console
set OskRootKey=HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK
reg.exe ADD "%OskRootKey%" /v MaxHeightPercentage /t REG_SZ /d "56.783" /f
```
或从 PowerShell:
```powershell
set OskRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK"
cd $OskRootKey
Set-ItemProperty -Path . -Name MaxHeightPercentage -Type String -Value 56.783
```

> [!NOTE]
> 注册表值类型必须是字符串 (`REG_SZ`), 以便用来表示小数值。
> 小数点。 即使对于整数`REG_DWORD`百分比, 使用 DWord () 也_不_起作用。

### <a name="additional-preferences"></a>其他首选项

其他首选项集是首选项子项中的字符串值:
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK\Preferences
```

| 注册表值               | Default Value      | 描述                                                                                         |
| ---------------------------- | ------------------ | --------------------------------------------------------------------------------------------------- |
| AudioFeedback_Disabled       | 0                | "0" 启用密钥单击音频反馈;"1" 禁用该方法。                                          |
| Dictation_Disabled           | "1"                | "0" 显示听写 (语音识别) 按钮;"1" 隐藏它。<br/> (请参阅下面的注释)             |
| KeyboardModeEnabled_full     | 0                | "0" 禁用全键盘模式;"1" 启用它。                                                |
| KeyboardModeEnabled_narrow   | "1"                | "0" 禁用窄幅键盘模式;"1" 启用它。                                              |
| KeyboardModeEnabled_wide     | "1"                | "0" 禁用宽键盘模式;"1" 启用它。                                                |
| ModeOrder                    | "宽; 窄; 完全" | 模式在 "模式" 下拉菜单中的显示顺序 (从左到右) (如果已启用) |
| SettingsMenuKey_Collapsed    | 0                | 隐藏模式下拉菜单。 如果只启用了一种模式, 则将此项设置为 "1"。                         |
| Paste_Disabled               | 0                | "0" 显示 "粘贴" 按钮;"1" 隐藏它。<br/> 更改将在重新启动后生效。                    |
| CloseButton_Disabled         | 0                | "0" 显示 "关闭" 按钮;"1" 隐藏 "关闭" 按钮<br/> 更改将在重新启动后生效。       |
| EmojiKeyEnabled              | 0                | "0" 隐藏表情符号键;"1" 显示, 允许用户输入表情符号字符。                 |

> [!NOTE]
> 听写模式需要为所选输入语言以及音频输入设备安装语音包。 如果未安装匹配的语音包, 则不会显示 "听写" 按钮。
> 
> 所有映像都包含 en-us 语音语言。 其他语音包作为可选功能安装。
> 有关 IoT 功能的详细信息, 请参阅[Iot 核心功能列表](/windows-hardware/manufacture/iot/iot-core-feature-list)和[iot 核心制造指南](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。

例如, 若要仅`wide`启用键盘模式, 请在 PowerShell 中执行以下操作:
```powershell
set OskRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK"
cd $OskRootKey
mkdir Preferences
cd Preferences
Set-ItemProperty . -Name KeyboardModeEnabled_full -Value "0"      # Optional, since the default is "0"
Set-ItemProperty . -Name KeyboardModeEnabled_narrow -Value "0"
Set-ItemProperty . -Name KeyboardModeEnabled_wide -Value "1"      # Optional, since the default is "1"
Set-ItemProperty . -Name SettingsMenuKey_Collapsed -Value "1"
```
