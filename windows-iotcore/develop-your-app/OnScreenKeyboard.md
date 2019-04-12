---
title: 配置主的设备使用 Windows 10 IoT Core 屏幕键盘
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
description: 了解有关新屏幕键盘以及如何在 Windows 10 IoT 核心版 1809年中配置它。
keywords: Windows 10 IoT Core，触控、 键盘、 osk，屏幕上，屏幕上，sip，输入、 输入法，讨论的问题，听写、 语音、 语音
ms.custom: RS5
ms.openlocfilehash: 100aeb484690c462deac56dcadf7d17667487ae2
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510630"
---
# <a name="on-screen-keyboard-for-headed-devices"></a>适用于设备主屏幕键盘

在 Windows 10 IoT 核心版 1809，屏幕键盘组件已更改大的差异，并改善了 ！ IoT 核心版现在为 Windows 桌面版使用相同的触摸键盘组件。

## <a name="new-features"></a>新增功能
新的键盘实现提供了到进行主的设备开发的以下优势：

* [一组完整的 Windows 键盘语言布局](#windows-keyboard-language-layouts)
* [对输入作用域 （例如，电子邮件地址、 数字 PIN、 搜索字段等） 的支持](#support-for-input-scopes)
* [输入法编辑器 (IME)](#input-method-editor-ime)
* [非遮盖文本输入的字段](#non-obscured-text-input-fields)
* [听写模式](#dictation-mode)
* [所选的用户界面首选项](#user-interface-configuration)

## <a name="feature-packages"></a>功能包

对于原型制作 （开发） 映像，屏幕键盘功能已包括在内，但将需要从设备设置中启用[Windows Device Portal](../manage-your-device/deviceportal.md#iot-specific-features)。

对于商业化，添加以下可选功能包将屏幕键盘到你的映像：
* IOT_SHELL_ONSCREEN_KEYBOARD
* IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS

> [!TIP]
> 有关 IoT 核心功能的详细信息，请参阅[IoT Core 功能列表](/windows-hardware/manufacture/iot/iot-core-feature-list)并[IoT 核心版制造指南](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。

## <a name="windows-keyboard-language-layouts"></a>Windows 键盘语言布局

此版本中，受支持的语言布局已扩大到包括这些桌面的 Windows 版本中可用的完整集。 若要允许用户选择不同的语言布局之间，应在应用程序的设置区域中通常包括选择 UI。 以下 API 用于启用应用程序设置的语言键盘就可以使用屏幕上：

[Windows.Globalization.Language.TrySetInputMethodLanguageTag](/uwp/api/windows.globalization.language.trysetinputmethodlanguagetag)

此 API 的示例所示[IoTCoreDefaultApp 示例应用程序](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp)，在[LanguageManager.cs](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/IoTCoreDefaultApp/CS/IoTCoreDefaultApp/Presenters/LanguageManager.cs)文件。

## <a name="support-for-input-scopes"></a>对输入作用域的支持

在上一版本中，仅 EmailSmtpAddress 输入的范围不可用。 在此版本中，输入作用域的完整集都可用。 以下主题介绍了输入作用域以及如何在您的应用程序中使用它们：

[使用输入范围更改触摸键盘](/windows/uwp/design/input/use-input-scope-to-change-the-touch-keyboard)

## <a name="input-method-editor-ime"></a>输入法编辑器 (IME)

此版本提供了输入法编辑器，所需的任何语言都具有多个 graphemes 不是键盘，例如中文、 日语和朝鲜语上有密钥。

## <a name="non-obscured-text-input-fields"></a>非遮盖文本输入的字段

在上一版本中，触摸键盘可能掩盖已设定焦点的文本字段，以便用户无法看到它们已键入的内容。 此版本的自动滚动到视图的文本字段，以便不再遮盖触摸键盘修复此问题。

## <a name="dictation-mode"></a>听写模式

当输入的语言设置为 OS 的语言，这是默认设置，语音识别输入的功能才可用。
若要显示在键盘听写按钮，请参阅以下部分上[用户界面配置](#user-interface-configuration)。

## <a name="user-interface-configuration"></a>用户界面配置

屏幕键盘提供若干可配置选项，其用户界面。 通过注册表配置这些。
在开发过程中可以使用[PowerShell](/windows/iot-core/connect-your-device/powershell)或[安全外壳 (SSH)](/windows/iot-core/connect-your-device/ssh)。 有关如何创建 OEM 图像，设置注册表值的首选的机制是`OEMInput.xml`文件此处所述：

[运行时自定义](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)

> [!NOTE]
> 大部分此处所述的注册表设置将生效时屏幕键盘是可见。
> 这允许您在开发轻松尝试不同 combinatations 设置值，立即看到更改，在真实时间中的过程。 如果设置不会不会立即生效，您需要重新启动设备，才能查看对键盘用户界面的更改。

### <a name="keyboard-height"></a>键盘高度

默认情况下，触摸键盘将使用较低的 45%的屏幕的高度。 这可能显示太大或太小上你的设备，具体取决于其大小和分辨率。 您可以调整最大为 2 / 3 高度屏幕的高度。 不在范围内的任何值将被限制到范围。 因为这被指定为浮点值，它允许像素级精度。 只需将应用以下公式来计算百分比：

`percentage = (100 * <desired_pixel_height>) / <screen_height>`

例如，要更改高度为 56.783%，您将设置以下注册表值：
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
> 注册表值类型必须是字符串 (`REG_SZ`)，以便可以用来表示小数部分值。
> 小数点。 使用双字节 (`REG_DWORD`) 将_不_工作，即使对于整数百分比。

### <a name="additional-preferences"></a>其他首选项

剩余首选项集是在首选项的子项中的字符串值：
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK\Preferences
```

| 注册表值               | 默认值      | 描述                                                                                         |
| ---------------------------- | ------------------ | --------------------------------------------------------------------------------------------------- |
| AudioFeedback_Disabled       | "0"                | "0"启用项单击音频反馈;"1"会禁用它。                                          |
| Dictation_Disabled           | "1"                | "0"显示听写 （语音识别） 按钮;"1"将隐藏它。<br/> （请参阅下面的备注）             |
| KeyboardModeEnabled_full     | "0"                | "0"禁用完整键盘模式;"1"启用它。                                                |
| KeyboardModeEnabled_narrow   | "1"                | "0"禁用的窄键盘模式;"1"启用它。                                              |
| KeyboardModeEnabled_wide     | "1"                | "0"禁用宽键盘模式;"1"启用它。                                                |
| ModeOrder                    | "wide;narrow;full" | 在其中法都列在模式下拉列表菜单，如果启用了顺序 （从左到右） |
| SettingsMenuKey_Collapsed    | "0"                | 将隐藏模式下拉列表菜单。 将此设置为"1"，如果只有一种模式已启用。                         |
| Paste_Disabled               | "0"                | "0"显示粘贴按钮;"1"将隐藏它。<br/> 重新启动后，更改将生效。                    |
| CloseButton_Disabled         | "0"                | "0"显示关闭按钮;"1"隐藏关闭按钮<br/> 重新启动后，更改将生效。       |
| EmojiKeyEnabled              | "0"                | "0"隐藏的表情符号密钥;"1"显示它，这样就允许用户输入表情符号字符。                 |

> [!NOTE]
> 听写模式需要为所选的输入的语言，以及将音频输入的设备安装的语音包。 如果未安装匹配的语音包，将不会显示听写按钮。
> 
> 所有映像都包括 EN-US 语音语言。 作为可选功能安装其他语音包。
> 有关 IoT 功能的详细信息，请参阅[IoT Core 功能列表](/windows-hardware/manufacture/iot/iot-core-feature-list)并[IoT 核心版制造指南](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。

例如，若要仅启用`wide`键盘模式下，可以在 PowerShell 中执行以下：
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
