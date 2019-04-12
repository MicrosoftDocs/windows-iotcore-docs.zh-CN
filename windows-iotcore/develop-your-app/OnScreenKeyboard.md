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
# <a name="on-screen-keyboard-for-headed-devices"></a><span data-ttu-id="ea24c-104">适用于设备主屏幕键盘</span><span class="sxs-lookup"><span data-stu-id="ea24c-104">On-screen keyboard for headed devices</span></span>

<span data-ttu-id="ea24c-105">在 Windows 10 IoT 核心版 1809，屏幕键盘组件已更改大的差异，并改善了 ！</span><span class="sxs-lookup"><span data-stu-id="ea24c-105">In Windows 10 IoT Core, version 1809, the on-screen keyboard component has changed significantly, and for the better!</span></span> <span data-ttu-id="ea24c-106">IoT 核心版现在为 Windows 桌面版使用相同的触摸键盘组件。</span><span class="sxs-lookup"><span data-stu-id="ea24c-106">IoT Core now uses the same touch keyboard components as the desktop edition of Windows.</span></span>

## <a name="new-features"></a><span data-ttu-id="ea24c-107">新增功能</span><span class="sxs-lookup"><span data-stu-id="ea24c-107">New features</span></span>
<span data-ttu-id="ea24c-108">新的键盘实现提供了到进行主的设备开发的以下优势：</span><span class="sxs-lookup"><span data-stu-id="ea24c-108">The new keyboard implementation provides the following benefits to your headed device development:</span></span>

* [<span data-ttu-id="ea24c-109">一组完整的 Windows 键盘语言布局</span><span class="sxs-lookup"><span data-stu-id="ea24c-109">The entire set of Windows keyboard language layouts</span></span>](#windows-keyboard-language-layouts)
* [<span data-ttu-id="ea24c-110">对输入作用域 （例如，电子邮件地址、 数字 PIN、 搜索字段等） 的支持</span><span class="sxs-lookup"><span data-stu-id="ea24c-110">Support for input scopes (e.g., Email Address, Numeric PIN, Search Field, etc.)</span></span>](#support-for-input-scopes)
* [<span data-ttu-id="ea24c-111">输入法编辑器 (IME)</span><span class="sxs-lookup"><span data-stu-id="ea24c-111">Input Method Editor (IME)</span></span>](#input-method-editor-ime)
* [<span data-ttu-id="ea24c-112">非遮盖文本输入的字段</span><span class="sxs-lookup"><span data-stu-id="ea24c-112">Non-obscured text input fields</span></span>](#non-obscured-text-input-fields)
* [<span data-ttu-id="ea24c-113">听写模式</span><span class="sxs-lookup"><span data-stu-id="ea24c-113">Dictation mode</span></span>](#dictation-mode)
* [<span data-ttu-id="ea24c-114">所选的用户界面首选项</span><span class="sxs-lookup"><span data-stu-id="ea24c-114">A selection of user interface preferences</span></span>](#user-interface-configuration)

## <a name="feature-packages"></a><span data-ttu-id="ea24c-115">功能包</span><span class="sxs-lookup"><span data-stu-id="ea24c-115">Feature packages</span></span>

<span data-ttu-id="ea24c-116">对于原型制作 （开发） 映像，屏幕键盘功能已包括在内，但将需要从设备设置中启用[Windows Device Portal](../manage-your-device/deviceportal.md#iot-specific-features)。</span><span class="sxs-lookup"><span data-stu-id="ea24c-116">For prototyping (development) images, the on-screen keyboard feature is already included, but you will need to enable it from Device Settings in the [Windows Device Portal](../manage-your-device/deviceportal.md#iot-specific-features).</span></span>

<span data-ttu-id="ea24c-117">对于商业化，添加以下可选功能包将屏幕键盘到你的映像：</span><span class="sxs-lookup"><span data-stu-id="ea24c-117">For commercialization, the following optional feature packages will add the on-screen keyboard to your image:</span></span>
* <span data-ttu-id="ea24c-118">IOT_SHELL_ONSCREEN_KEYBOARD</span><span class="sxs-lookup"><span data-stu-id="ea24c-118">IOT_SHELL_ONSCREEN_KEYBOARD</span></span>
* <span data-ttu-id="ea24c-119">IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS</span><span class="sxs-lookup"><span data-stu-id="ea24c-119">IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS</span></span>

> [!TIP]
> <span data-ttu-id="ea24c-120">有关 IoT 核心功能的详细信息，请参阅[IoT Core 功能列表](/windows-hardware/manufacture/iot/iot-core-feature-list)并[IoT 核心版制造指南](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="ea24c-120">For more information about IoT Core Features, see [IoT Core Feature List](/windows-hardware/manufacture/iot/iot-core-feature-list) and [IoT Core manufacturing guide](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

## <a name="windows-keyboard-language-layouts"></a><span data-ttu-id="ea24c-121">Windows 键盘语言布局</span><span class="sxs-lookup"><span data-stu-id="ea24c-121">Windows keyboard language layouts</span></span>

<span data-ttu-id="ea24c-122">此版本中，受支持的语言布局已扩大到包括这些桌面的 Windows 版本中可用的完整集。</span><span class="sxs-lookup"><span data-stu-id="ea24c-122">With this release, the supported language layouts has expanded to include the full set of those available in the desktop Windows edition.</span></span> <span data-ttu-id="ea24c-123">若要允许用户选择不同的语言布局之间，应在应用程序的设置区域中通常包括选择 UI。</span><span class="sxs-lookup"><span data-stu-id="ea24c-123">To allow your users to select between different language layouts, you would typically include selection UI in your application's Settings area.</span></span> <span data-ttu-id="ea24c-124">以下 API 用于启用应用程序设置的语言键盘就可以使用屏幕上：</span><span class="sxs-lookup"><span data-stu-id="ea24c-124">The following API is provided to enable your application to set the language that the on-screen keyboard will use:</span></span>

[<span data-ttu-id="ea24c-125">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span><span class="sxs-lookup"><span data-stu-id="ea24c-125">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span></span>](/uwp/api/windows.globalization.language.trysetinputmethodlanguagetag)

<span data-ttu-id="ea24c-126">此 API 的示例所示[IoTCoreDefaultApp 示例应用程序](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp)，在[LanguageManager.cs](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/IoTCoreDefaultApp/CS/IoTCoreDefaultApp/Presenters/LanguageManager.cs)文件。</span><span class="sxs-lookup"><span data-stu-id="ea24c-126">An example of this API can be seen in the [IoTCoreDefaultApp sample application](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp), in the [LanguageManager.cs](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/IoTCoreDefaultApp/CS/IoTCoreDefaultApp/Presenters/LanguageManager.cs) file.</span></span>

## <a name="support-for-input-scopes"></a><span data-ttu-id="ea24c-127">对输入作用域的支持</span><span class="sxs-lookup"><span data-stu-id="ea24c-127">Support for input scopes</span></span>

<span data-ttu-id="ea24c-128">在上一版本中，仅 EmailSmtpAddress 输入的范围不可用。</span><span class="sxs-lookup"><span data-stu-id="ea24c-128">In previous releases, only the EmailSmtpAddress input scope was available.</span></span> <span data-ttu-id="ea24c-129">在此版本中，输入作用域的完整集都可用。</span><span class="sxs-lookup"><span data-stu-id="ea24c-129">In this release, the full set of input scopes are available.</span></span> <span data-ttu-id="ea24c-130">以下主题介绍了输入作用域以及如何在您的应用程序中使用它们：</span><span class="sxs-lookup"><span data-stu-id="ea24c-130">The following topic explains input scopes and how to use them in your applications:</span></span>

[<span data-ttu-id="ea24c-131">使用输入范围更改触摸键盘</span><span class="sxs-lookup"><span data-stu-id="ea24c-131">Use input scope to change the touch keyboard</span></span>](/windows/uwp/design/input/use-input-scope-to-change-the-touch-keyboard)

## <a name="input-method-editor-ime"></a><span data-ttu-id="ea24c-132">输入法编辑器 (IME)</span><span class="sxs-lookup"><span data-stu-id="ea24c-132">Input Method Editor (IME)</span></span>

<span data-ttu-id="ea24c-133">此版本提供了输入法编辑器，所需的任何语言都具有多个 graphemes 不是键盘，例如中文、 日语和朝鲜语上有密钥。</span><span class="sxs-lookup"><span data-stu-id="ea24c-133">This release provides an Input Method Editor, which is required for any language that has more graphemes than there are keys on the keyboard, such as Chinese, Japanese, and Korean.</span></span>

## <a name="non-obscured-text-input-fields"></a><span data-ttu-id="ea24c-134">非遮盖文本输入的字段</span><span class="sxs-lookup"><span data-stu-id="ea24c-134">Non-obscured text input fields</span></span>

<span data-ttu-id="ea24c-135">在上一版本中，触摸键盘可能掩盖已设定焦点的文本字段，以便用户无法看到它们已键入的内容。</span><span class="sxs-lookup"><span data-stu-id="ea24c-135">In previous releases, the touch keyboard might obscure the focused text field so that the user was unable to see what they were typing.</span></span> <span data-ttu-id="ea24c-136">此版本的自动滚动到视图的文本字段，以便不再遮盖触摸键盘修复此问题。</span><span class="sxs-lookup"><span data-stu-id="ea24c-136">This release fixes this problem by automatically scrolling the text field into view so that it's no longer obscured by the touch keyboard.</span></span>

## <a name="dictation-mode"></a><span data-ttu-id="ea24c-137">听写模式</span><span class="sxs-lookup"><span data-stu-id="ea24c-137">Dictation mode</span></span>

<span data-ttu-id="ea24c-138">当输入的语言设置为 OS 的语言，这是默认设置，语音识别输入的功能才可用。</span><span class="sxs-lookup"><span data-stu-id="ea24c-138">When the input language is set to the OS language, which is the default, the voice recognition input feature is available.</span></span>
<span data-ttu-id="ea24c-139">若要显示在键盘听写按钮，请参阅以下部分上[用户界面配置](#user-interface-configuration)。</span><span class="sxs-lookup"><span data-stu-id="ea24c-139">To show the dictation button in the keyboard, refer to the following section on [User Interface configuration](#user-interface-configuration).</span></span>

## <a name="user-interface-configuration"></a><span data-ttu-id="ea24c-140">用户界面配置</span><span class="sxs-lookup"><span data-stu-id="ea24c-140">User Interface configuration</span></span>

<span data-ttu-id="ea24c-141">屏幕键盘提供若干可配置选项，其用户界面。</span><span class="sxs-lookup"><span data-stu-id="ea24c-141">The on-screen keyboard provides several configurable options for its user interface.</span></span> <span data-ttu-id="ea24c-142">通过注册表配置这些。</span><span class="sxs-lookup"><span data-stu-id="ea24c-142">These are configured via the registry.</span></span>
<span data-ttu-id="ea24c-143">在开发过程中可以使用[PowerShell](/windows/iot-core/connect-your-device/powershell)或[安全外壳 (SSH)](/windows/iot-core/connect-your-device/ssh)。</span><span class="sxs-lookup"><span data-stu-id="ea24c-143">During development you can use [PowerShell](/windows/iot-core/connect-your-device/powershell) or [Secure Shell (SSH)](/windows/iot-core/connect-your-device/ssh).</span></span> <span data-ttu-id="ea24c-144">有关如何创建 OEM 图像，设置注册表值的首选的机制是`OEMInput.xml`文件此处所述：</span><span class="sxs-lookup"><span data-stu-id="ea24c-144">For creating an OEM image, the preferred mechanism for setting registry values is the `OEMInput.xml` file discussed here:</span></span>

[<span data-ttu-id="ea24c-145">运行时自定义</span><span class="sxs-lookup"><span data-stu-id="ea24c-145">Runtime customizations</span></span>](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)

> [!NOTE]
> <span data-ttu-id="ea24c-146">大部分此处所述的注册表设置将生效时屏幕键盘是可见。</span><span class="sxs-lookup"><span data-stu-id="ea24c-146">Most of the registry settings documented here will take effect while the on-screen keyboard is visible.</span></span>
> <span data-ttu-id="ea24c-147">这允许您在开发轻松尝试不同 combinatations 设置值，立即看到更改，在真实时间中的过程。</span><span class="sxs-lookup"><span data-stu-id="ea24c-147">This allows you during development to easily try different combinatations of settings values, immediately seeing the resulting changes in real time.</span></span> <span data-ttu-id="ea24c-148">如果设置不会不会立即生效，您需要重新启动设备，才能查看对键盘用户界面的更改。</span><span class="sxs-lookup"><span data-stu-id="ea24c-148">If a setting does not take effect immediately, you will need to reboot the device in order to see the changes to the keyboard UI.</span></span>

### <a name="keyboard-height"></a><span data-ttu-id="ea24c-149">键盘高度</span><span class="sxs-lookup"><span data-stu-id="ea24c-149">Keyboard Height</span></span>

<span data-ttu-id="ea24c-150">默认情况下，触摸键盘将使用较低的 45%的屏幕的高度。</span><span class="sxs-lookup"><span data-stu-id="ea24c-150">By default, the touch keyboard will use the lower 45% of the screen's height.</span></span> <span data-ttu-id="ea24c-151">这可能显示太大或太小上你的设备，具体取决于其大小和分辨率。</span><span class="sxs-lookup"><span data-stu-id="ea24c-151">This may appear too large or small on your device, depending on its size and resolution.</span></span> <span data-ttu-id="ea24c-152">您可以调整最大为 2 / 3 高度屏幕的高度。</span><span class="sxs-lookup"><span data-stu-id="ea24c-152">You can adjust the height up to a maximum of two-thirds the height of the screen.</span></span> <span data-ttu-id="ea24c-153">不在范围内的任何值将被限制到范围。</span><span class="sxs-lookup"><span data-stu-id="ea24c-153">Any value not in range will be clamped into range.</span></span> <span data-ttu-id="ea24c-154">因为这被指定为浮点值，它允许像素级精度。</span><span class="sxs-lookup"><span data-stu-id="ea24c-154">Because this is specified as a floating point value, it allows for pixel-level precision.</span></span> <span data-ttu-id="ea24c-155">只需将应用以下公式来计算百分比：</span><span class="sxs-lookup"><span data-stu-id="ea24c-155">Simply apply the following formula to calculate the percentage:</span></span>

`percentage = (100 * <desired_pixel_height>) / <screen_height>`

<span data-ttu-id="ea24c-156">例如，要更改高度为 56.783%，您将设置以下注册表值：</span><span class="sxs-lookup"><span data-stu-id="ea24c-156">As an example, to change the height to 56.783%, you would set the following registry value:</span></span>
```console
set OskRootKey=HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK
reg.exe ADD "%OskRootKey%" /v MaxHeightPercentage /t REG_SZ /d "56.783" /f
```
<span data-ttu-id="ea24c-157">或从 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ea24c-157">or from PowerShell:</span></span>
```powershell
set OskRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK"
cd $OskRootKey
Set-ItemProperty -Path . -Name MaxHeightPercentage -Type String -Value 56.783
```

> [!NOTE]
> <span data-ttu-id="ea24c-158">注册表值类型必须是字符串 (`REG_SZ`)，以便可以用来表示小数部分值。</span><span class="sxs-lookup"><span data-stu-id="ea24c-158">The registry value type must be a String (`REG_SZ`), so that the fractional values can be represented with.</span></span>
> <span data-ttu-id="ea24c-159">小数点。</span><span class="sxs-lookup"><span data-stu-id="ea24c-159">a decimal point.</span></span> <span data-ttu-id="ea24c-160">使用双字节 (`REG_DWORD`) 将_不_工作，即使对于整数百分比。</span><span class="sxs-lookup"><span data-stu-id="ea24c-160">Using DWord (`REG_DWORD`) will _not_ work, even for whole number percentages.</span></span>

### <a name="additional-preferences"></a><span data-ttu-id="ea24c-161">其他首选项</span><span class="sxs-lookup"><span data-stu-id="ea24c-161">Additional preferences</span></span>

<span data-ttu-id="ea24c-162">剩余首选项集是在首选项的子项中的字符串值：</span><span class="sxs-lookup"><span data-stu-id="ea24c-162">The remaining set of preferences are String values in the Preferences subkey:</span></span>
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK\Preferences
```

| <span data-ttu-id="ea24c-163">注册表值</span><span class="sxs-lookup"><span data-stu-id="ea24c-163">Registry Value</span></span>               | <span data-ttu-id="ea24c-164">默认值</span><span class="sxs-lookup"><span data-stu-id="ea24c-164">Default Value</span></span>      | <span data-ttu-id="ea24c-165">描述</span><span class="sxs-lookup"><span data-stu-id="ea24c-165">Description</span></span>                                                                                         |
| ---------------------------- | ------------------ | --------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="ea24c-166">AudioFeedback_Disabled</span><span class="sxs-lookup"><span data-stu-id="ea24c-166">AudioFeedback_Disabled</span></span>       | <span data-ttu-id="ea24c-167">"0"</span><span class="sxs-lookup"><span data-stu-id="ea24c-167">"0"</span></span>                | <span data-ttu-id="ea24c-168">"0"启用项单击音频反馈;"1"会禁用它。</span><span class="sxs-lookup"><span data-stu-id="ea24c-168">"0" enables the key click audio feedback; "1" disables it.</span></span>                                          |
| <span data-ttu-id="ea24c-169">Dictation_Disabled</span><span class="sxs-lookup"><span data-stu-id="ea24c-169">Dictation_Disabled</span></span>           | <span data-ttu-id="ea24c-170">"1"</span><span class="sxs-lookup"><span data-stu-id="ea24c-170">"1"</span></span>                | <span data-ttu-id="ea24c-171">"0"显示听写 （语音识别） 按钮;"1"将隐藏它。</span><span class="sxs-lookup"><span data-stu-id="ea24c-171">"0" shows the dictation (voice recognition) button; "1" hides it.</span></span><br/> <span data-ttu-id="ea24c-172">（请参阅下面的备注）</span><span class="sxs-lookup"><span data-stu-id="ea24c-172">(see note below)</span></span>             |
| <span data-ttu-id="ea24c-173">KeyboardModeEnabled_full</span><span class="sxs-lookup"><span data-stu-id="ea24c-173">KeyboardModeEnabled_full</span></span>     | <span data-ttu-id="ea24c-174">"0"</span><span class="sxs-lookup"><span data-stu-id="ea24c-174">"0"</span></span>                | <span data-ttu-id="ea24c-175">"0"禁用完整键盘模式;"1"启用它。</span><span class="sxs-lookup"><span data-stu-id="ea24c-175">"0" disables the full keyboard mode; "1" enables it.</span></span>                                                |
| <span data-ttu-id="ea24c-176">KeyboardModeEnabled_narrow</span><span class="sxs-lookup"><span data-stu-id="ea24c-176">KeyboardModeEnabled_narrow</span></span>   | <span data-ttu-id="ea24c-177">"1"</span><span class="sxs-lookup"><span data-stu-id="ea24c-177">"1"</span></span>                | <span data-ttu-id="ea24c-178">"0"禁用的窄键盘模式;"1"启用它。</span><span class="sxs-lookup"><span data-stu-id="ea24c-178">"0" disables the narrow keyboard mode; "1" enables it.</span></span>                                              |
| <span data-ttu-id="ea24c-179">KeyboardModeEnabled_wide</span><span class="sxs-lookup"><span data-stu-id="ea24c-179">KeyboardModeEnabled_wide</span></span>     | <span data-ttu-id="ea24c-180">"1"</span><span class="sxs-lookup"><span data-stu-id="ea24c-180">"1"</span></span>                | <span data-ttu-id="ea24c-181">"0"禁用宽键盘模式;"1"启用它。</span><span class="sxs-lookup"><span data-stu-id="ea24c-181">"0" disables the wide keyboard mode; "1" enables it.</span></span>                                                |
| <span data-ttu-id="ea24c-182">ModeOrder</span><span class="sxs-lookup"><span data-stu-id="ea24c-182">ModeOrder</span></span>                    | <span data-ttu-id="ea24c-183">"wide;narrow;full"</span><span class="sxs-lookup"><span data-stu-id="ea24c-183">"wide;narrow;full"</span></span> | <span data-ttu-id="ea24c-184">在其中法都列在模式下拉列表菜单，如果启用了顺序 （从左到右）</span><span class="sxs-lookup"><span data-stu-id="ea24c-184">The order (from left to right) in which the modes are listed in the mode drop-down menu, if enabled</span></span> |
| <span data-ttu-id="ea24c-185">SettingsMenuKey_Collapsed</span><span class="sxs-lookup"><span data-stu-id="ea24c-185">SettingsMenuKey_Collapsed</span></span>    | <span data-ttu-id="ea24c-186">"0"</span><span class="sxs-lookup"><span data-stu-id="ea24c-186">"0"</span></span>                | <span data-ttu-id="ea24c-187">将隐藏模式下拉列表菜单。</span><span class="sxs-lookup"><span data-stu-id="ea24c-187">Hides the mode drop-down menu.</span></span> <span data-ttu-id="ea24c-188">将此设置为"1"，如果只有一种模式已启用。</span><span class="sxs-lookup"><span data-stu-id="ea24c-188">Set this to "1" if only one mode is enabled.</span></span>                         |
| <span data-ttu-id="ea24c-189">Paste_Disabled</span><span class="sxs-lookup"><span data-stu-id="ea24c-189">Paste_Disabled</span></span>               | <span data-ttu-id="ea24c-190">"0"</span><span class="sxs-lookup"><span data-stu-id="ea24c-190">"0"</span></span>                | <span data-ttu-id="ea24c-191">"0"显示粘贴按钮;"1"将隐藏它。</span><span class="sxs-lookup"><span data-stu-id="ea24c-191">"0" shows the Paste button; "1" hides it.</span></span><br/> <span data-ttu-id="ea24c-192">重新启动后，更改将生效。</span><span class="sxs-lookup"><span data-stu-id="ea24c-192">Change takes effect after reboot.</span></span>                    |
| <span data-ttu-id="ea24c-193">CloseButton_Disabled</span><span class="sxs-lookup"><span data-stu-id="ea24c-193">CloseButton_Disabled</span></span>         | <span data-ttu-id="ea24c-194">"0"</span><span class="sxs-lookup"><span data-stu-id="ea24c-194">"0"</span></span>                | <span data-ttu-id="ea24c-195">"0"显示关闭按钮;"1"隐藏关闭按钮</span><span class="sxs-lookup"><span data-stu-id="ea24c-195">"0" shows the Close button; "1" hides the Close button</span></span><br/> <span data-ttu-id="ea24c-196">重新启动后，更改将生效。</span><span class="sxs-lookup"><span data-stu-id="ea24c-196">Change takes effect after reboot.</span></span>       |
| <span data-ttu-id="ea24c-197">EmojiKeyEnabled</span><span class="sxs-lookup"><span data-stu-id="ea24c-197">EmojiKeyEnabled</span></span>              | <span data-ttu-id="ea24c-198">"0"</span><span class="sxs-lookup"><span data-stu-id="ea24c-198">"0"</span></span>                | <span data-ttu-id="ea24c-199">"0"隐藏的表情符号密钥;"1"显示它，这样就允许用户输入表情符号字符。</span><span class="sxs-lookup"><span data-stu-id="ea24c-199">"0" hides the Emoji key; "1" shows it, allowing the user to enter Emoji characters.</span></span>                 |

> [!NOTE]
> <span data-ttu-id="ea24c-200">听写模式需要为所选的输入的语言，以及将音频输入的设备安装的语音包。</span><span class="sxs-lookup"><span data-stu-id="ea24c-200">Dictation mode requires a speech package to be installed for the selected input language, as well as an audio input device.</span></span> <span data-ttu-id="ea24c-201">如果未安装匹配的语音包，将不会显示听写按钮。</span><span class="sxs-lookup"><span data-stu-id="ea24c-201">If a matching speech packages is not installed, the dictation button will not be shown.</span></span>
> 
> <span data-ttu-id="ea24c-202">所有映像都包括 EN-US 语音语言。</span><span class="sxs-lookup"><span data-stu-id="ea24c-202">All images include the en-US speech language.</span></span> <span data-ttu-id="ea24c-203">作为可选功能安装其他语音包。</span><span class="sxs-lookup"><span data-stu-id="ea24c-203">Other speech packages are installed as optional features.</span></span>
> <span data-ttu-id="ea24c-204">有关 IoT 功能的详细信息，请参阅[IoT Core 功能列表](/windows-hardware/manufacture/iot/iot-core-feature-list)并[IoT 核心版制造指南](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="ea24c-204">For more information about IoT Features, see [IoT Core Feature List](/windows-hardware/manufacture/iot/iot-core-feature-list) and [IoT Core manufacturing guide](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

<span data-ttu-id="ea24c-205">例如，若要仅启用`wide`键盘模式下，可以在 PowerShell 中执行以下：</span><span class="sxs-lookup"><span data-stu-id="ea24c-205">As an example, to enable only `wide` keyboard mode, in PowerShell you could do the following:</span></span>
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
