---
title: 通过 Windows 10 IoT Core 屏幕键盘配置头设备
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
description: 了解新的屏幕键盘，以及如何在 Windows 10 IoT Core，版本1809中对其进行配置。
keywords: Windows 10 IoT Core，touch，键盘，osk，屏幕，屏幕，sip，输入，ime，头，听写，语音，语音
ms.custom: RS5
ms.openlocfilehash: 6ff5c75ee46f4e13542d26e8d58669a3ff27db1a
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782909"
---
# <a name="on-screen-keyboard-for-headed-devices"></a><span data-ttu-id="ca409-104">用于头设备的屏幕键盘</span><span class="sxs-lookup"><span data-stu-id="ca409-104">On-screen keyboard for headed devices</span></span>

<span data-ttu-id="ca409-105">在 Windows 10 IoT Core 版本1809中，屏幕键盘组件发生了重大变化，更好！</span><span class="sxs-lookup"><span data-stu-id="ca409-105">In Windows 10 IoT Core, version 1809, the on-screen keyboard component has changed significantly, and for the better!</span></span> <span data-ttu-id="ca409-106">IoT Core 现在使用与桌面版 Windows 相同的触摸键盘组件。</span><span class="sxs-lookup"><span data-stu-id="ca409-106">IoT Core now uses the same touch keyboard components as the desktop edition of Windows.</span></span>

## <a name="new-features"></a><span data-ttu-id="ca409-107">新增功能</span><span class="sxs-lookup"><span data-stu-id="ca409-107">New features</span></span>
<span data-ttu-id="ca409-108">新的键盘实现为你的设备开发提供以下好处：</span><span class="sxs-lookup"><span data-stu-id="ca409-108">The new keyboard implementation provides the following benefits to your headed device development:</span></span>

* [<span data-ttu-id="ca409-109">整个 Windows 键盘语言布局集</span><span class="sxs-lookup"><span data-stu-id="ca409-109">The entire set of Windows keyboard language layouts</span></span>](#windows-keyboard-language-layouts)
* [<span data-ttu-id="ca409-110">支持输入范围 (例如，电子邮件地址、数字 PIN、搜索字段等） ) </span><span class="sxs-lookup"><span data-stu-id="ca409-110">Support for input scopes (e.g., Email Address, Numeric PIN, Search Field, etc.)</span></span>](#support-for-input-scopes)
* [<span data-ttu-id="ca409-111">输入法编辑器 (IME)</span><span class="sxs-lookup"><span data-stu-id="ca409-111">Input Method Editor (IME)</span></span>](#input-method-editor-ime)
* [<span data-ttu-id="ca409-112">不隐藏的文本输入字段</span><span class="sxs-lookup"><span data-stu-id="ca409-112">Non-obscured text input fields</span></span>](#non-obscured-text-input-fields)
* [<span data-ttu-id="ca409-113">听写模式</span><span class="sxs-lookup"><span data-stu-id="ca409-113">Dictation mode</span></span>](#dictation-mode)
* [<span data-ttu-id="ca409-114">用户界面首选项的选择</span><span class="sxs-lookup"><span data-stu-id="ca409-114">A selection of user interface preferences</span></span>](#user-interface-configuration)

## <a name="feature-packages"></a><span data-ttu-id="ca409-115">功能包</span><span class="sxs-lookup"><span data-stu-id="ca409-115">Feature packages</span></span>

<span data-ttu-id="ca409-116">为了 (开发) 映像构建原型，已包括屏幕键盘功能，但需要在 [Windows 设备门户](../manage-your-device/deviceportal.md#iot-specific-features)中从设备设置启用该功能。</span><span class="sxs-lookup"><span data-stu-id="ca409-116">For prototyping (development) images, the on-screen keyboard feature is already included, but you will need to enable it from Device Settings in the [Windows Device Portal](../manage-your-device/deviceportal.md#iot-specific-features).</span></span>

<span data-ttu-id="ca409-117">对于商业化，以下可选功能包会将屏幕键盘添加到映像：</span><span class="sxs-lookup"><span data-stu-id="ca409-117">For commercialization, the following optional feature packages will add the on-screen keyboard to your image:</span></span>
* <span data-ttu-id="ca409-118">IOT_SHELL_ONSCREEN_KEYBOARD</span><span class="sxs-lookup"><span data-stu-id="ca409-118">IOT_SHELL_ONSCREEN_KEYBOARD</span></span>
* <span data-ttu-id="ca409-119">IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS</span><span class="sxs-lookup"><span data-stu-id="ca409-119">IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS</span></span>

> [!TIP]
> <span data-ttu-id="ca409-120">有关 IoT 核心功能的详细信息，请参阅 [Iot 核心功能列表](/windows-hardware/manufacture/iot/iot-core-feature-list) 和 [iot 核心制造指南](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="ca409-120">For more information about IoT Core Features, see [IoT Core Feature List](/windows-hardware/manufacture/iot/iot-core-feature-list) and [IoT Core manufacturing guide](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

## <a name="windows-keyboard-language-layouts"></a><span data-ttu-id="ca409-121">Windows 键盘语言布局</span><span class="sxs-lookup"><span data-stu-id="ca409-121">Windows keyboard language layouts</span></span>

<span data-ttu-id="ca409-122">在此版本中，支持的语言布局已扩展为包括桌面 Windows 版本中可用的完整集。</span><span class="sxs-lookup"><span data-stu-id="ca409-122">With this release, the supported language layouts have expanded to include the full set of those available in the desktop Windows edition.</span></span> <span data-ttu-id="ca409-123">若要允许用户在不同的语言布局之间进行选择，通常应在应用程序的 "设置" 区域中包括选择 UI。</span><span class="sxs-lookup"><span data-stu-id="ca409-123">To allow your users to select between different language layouts, you would typically include selection UI in your application's Settings area.</span></span> <span data-ttu-id="ca409-124">提供以下 API 是为了使应用程序能够设置屏幕键盘将使用的语言：</span><span class="sxs-lookup"><span data-stu-id="ca409-124">The following API is provided to enable your application to set the language that the on-screen keyboard will use:</span></span>

[<span data-ttu-id="ca409-125">Windows TrySetInputMethodLanguageTag</span><span class="sxs-lookup"><span data-stu-id="ca409-125">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span></span>](/uwp/api/windows.globalization.language.trysetinputmethodlanguagetag)

<span data-ttu-id="ca409-126">可在[LanguageManager.cs](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/IoTCoreDefaultApp/CS/IoTCoreDefaultApp/Presenters/LanguageManager.cs)文件中的[IoTCoreDefaultApp 示例应用程序](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp)中查看此 API 的示例。</span><span class="sxs-lookup"><span data-stu-id="ca409-126">An example of this API can be seen in the [IoTCoreDefaultApp sample application](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp), in the [LanguageManager.cs](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/IoTCoreDefaultApp/CS/IoTCoreDefaultApp/Presenters/LanguageManager.cs) file.</span></span>

## <a name="support-for-input-scopes"></a><span data-ttu-id="ca409-127">支持输入范围</span><span class="sxs-lookup"><span data-stu-id="ca409-127">Support for input scopes</span></span>

<span data-ttu-id="ca409-128">在以前的版本中，只有 EmailSmtpAddress 输入范围可用。</span><span class="sxs-lookup"><span data-stu-id="ca409-128">In previous releases, only the EmailSmtpAddress input scope was available.</span></span> <span data-ttu-id="ca409-129">在此版本中，提供了一组完整的输入范围。</span><span class="sxs-lookup"><span data-stu-id="ca409-129">In this release, the full set of input scopes is available.</span></span> <span data-ttu-id="ca409-130">以下主题介绍输入范围以及如何在你的应用程序中使用它们：</span><span class="sxs-lookup"><span data-stu-id="ca409-130">The following topic explains input scopes and how to use them in your applications:</span></span>

[<span data-ttu-id="ca409-131">使用输入范围更改触摸键盘</span><span class="sxs-lookup"><span data-stu-id="ca409-131">Use input scope to change the touch keyboard</span></span>](/windows/uwp/design/input/use-input-scope-to-change-the-touch-keyboard)

## <a name="input-method-editor-ime"></a><span data-ttu-id="ca409-132">输入法编辑器 (IME)</span><span class="sxs-lookup"><span data-stu-id="ca409-132">Input Method Editor (IME)</span></span>

<span data-ttu-id="ca409-133">此版本提供了一个输入法编辑器，该编辑器对于比键盘上的键（例如中文、日语和韩语）具有更多 graphemes 的任何语言都是必需的。</span><span class="sxs-lookup"><span data-stu-id="ca409-133">This release provides an Input Method Editor, which is required for any language that has more graphemes than there are keys on the keyboard, such as Chinese, Japanese, and Korean.</span></span>

## <a name="non-obscured-text-input-fields"></a><span data-ttu-id="ca409-134">不隐藏的文本输入字段</span><span class="sxs-lookup"><span data-stu-id="ca409-134">Non-obscured text input fields</span></span>

<span data-ttu-id="ca409-135">在以前的版本中，触摸键盘可能会掩盖重点文本字段，使用户无法看到他们所键入的内容。</span><span class="sxs-lookup"><span data-stu-id="ca409-135">In previous releases, the touch keyboard might obscure the focused text field so that the user was unable to see what they were typing.</span></span> <span data-ttu-id="ca409-136">此版本通过自动将文本字段滚动到视图中来解决此问题，因此它不再被触摸键盘遮盖。</span><span class="sxs-lookup"><span data-stu-id="ca409-136">This release fixes this problem by automatically scrolling the text field into view so that it's no longer obscured by the touch keyboard.</span></span>

## <a name="dictation-mode"></a><span data-ttu-id="ca409-137">听写模式</span><span class="sxs-lookup"><span data-stu-id="ca409-137">Dictation mode</span></span>

<span data-ttu-id="ca409-138">如果输入语言设置为 OS 语言（默认值），则语音识别输入功能可用。</span><span class="sxs-lookup"><span data-stu-id="ca409-138">When the input language is set to the OS language, which is the default, the voice recognition input feature is available.</span></span>
<span data-ttu-id="ca409-139">若要在键盘中显示听写按钮，请参阅以下有关 [用户界面配置](#user-interface-configuration)的部分。</span><span class="sxs-lookup"><span data-stu-id="ca409-139">To show the dictation button in the keyboard, refer to the following section on [User Interface configuration](#user-interface-configuration).</span></span>

## <a name="user-interface-configuration"></a><span data-ttu-id="ca409-140">用户界面配置</span><span class="sxs-lookup"><span data-stu-id="ca409-140">User Interface configuration</span></span>

<span data-ttu-id="ca409-141">屏幕键盘为其用户界面提供了多个可配置选项。</span><span class="sxs-lookup"><span data-stu-id="ca409-141">The on-screen keyboard provides several configurable options for its user interface.</span></span> <span data-ttu-id="ca409-142">这些配置通过注册表进行配置。</span><span class="sxs-lookup"><span data-stu-id="ca409-142">These are configured via the registry.</span></span>
<span data-ttu-id="ca409-143">在开发过程中，可以使用 [PowerShell](/windows/iot-core/connect-your-device/powershell) 或 [安全外壳 (SSH) ](/windows/iot-core/connect-your-device/ssh)。</span><span class="sxs-lookup"><span data-stu-id="ca409-143">During development, you can use [PowerShell](/windows/iot-core/connect-your-device/powershell) or [Secure Shell (SSH)](/windows/iot-core/connect-your-device/ssh).</span></span> <span data-ttu-id="ca409-144">对于创建 OEM 映像，用于设置注册表值的首选机制是 `OEMInput.xml` 此处讨论的文件：</span><span class="sxs-lookup"><span data-stu-id="ca409-144">For creating an OEM image, the preferred mechanism for setting registry values is the `OEMInput.xml` file discussed here:</span></span>

[<span data-ttu-id="ca409-145">运行时自定义</span><span class="sxs-lookup"><span data-stu-id="ca409-145">Runtime customizations</span></span>](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)

> [!NOTE]
> <span data-ttu-id="ca409-146">此处所述的大部分注册表设置将在屏幕键盘可见时生效。</span><span class="sxs-lookup"><span data-stu-id="ca409-146">Most of the registry settings documented here will take effect while the on-screen keyboard is visible.</span></span>
> <span data-ttu-id="ca409-147">这使你可以在开发过程中轻松尝试不同的设置值 combinatations，并立即实时查看所产生的更改。</span><span class="sxs-lookup"><span data-stu-id="ca409-147">This allows you during development to easily try different combinatations of settings values, immediately seeing the resulting changes in real time.</span></span> <span data-ttu-id="ca409-148">如果某个设置不会立即生效，你将需要重新启动设备，才能查看对键盘 UI 所做的更改。</span><span class="sxs-lookup"><span data-stu-id="ca409-148">If a setting does not take effect immediately, you will need to reboot the device in order to see the changes to the keyboard UI.</span></span>

### <a name="keyboard-height"></a><span data-ttu-id="ca409-149">键盘高度</span><span class="sxs-lookup"><span data-stu-id="ca409-149">Keyboard Height</span></span>

<span data-ttu-id="ca409-150">默认情况下，触摸键盘将使用屏幕高度的45%。</span><span class="sxs-lookup"><span data-stu-id="ca409-150">By default, the touch keyboard will use the lower 45% of the screen's height.</span></span> <span data-ttu-id="ca409-151">这可能会在设备上显得太大或太小，具体取决于其大小和分辨率。</span><span class="sxs-lookup"><span data-stu-id="ca409-151">This may appear too large or small on your device, depending on its size and resolution.</span></span> <span data-ttu-id="ca409-152">最大可将高度调整到屏幕高度的三分之二。</span><span class="sxs-lookup"><span data-stu-id="ca409-152">You can adjust the height up to a maximum of two-thirds the height of the screen.</span></span> <span data-ttu-id="ca409-153">不在范围内的任何值都将限制为范围。</span><span class="sxs-lookup"><span data-stu-id="ca409-153">Any value not in range will be clamped into range.</span></span> <span data-ttu-id="ca409-154">因为这被指定为浮点值，所以它允许像素级别的精度。</span><span class="sxs-lookup"><span data-stu-id="ca409-154">Because this is specified as a floating point value, it allows for pixel-level precision.</span></span> <span data-ttu-id="ca409-155">只需应用以下公式即可计算百分比：</span><span class="sxs-lookup"><span data-stu-id="ca409-155">Simply apply the following formula to calculate the percentage:</span></span>

`percentage = (100 * <desired_pixel_height>) / <screen_height>`

<span data-ttu-id="ca409-156">例如，要将高度更改为56.783%，请设置以下注册表值：</span><span class="sxs-lookup"><span data-stu-id="ca409-156">As an example, to change the height to 56.783%, you would set the following registry value:</span></span>
```console
set OskRootKey=HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK
reg.exe ADD "%OskRootKey%" /v MaxHeightPercentage /t REG_SZ /d "56.783" /f
```
<span data-ttu-id="ca409-157">或从 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="ca409-157">or from PowerShell:</span></span>
```powershell
set OskRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK"
cd $OskRootKey
Set-ItemProperty -Path . -Name MaxHeightPercentage -Type String -Value 56.783
```

> [!NOTE]
> <span data-ttu-id="ca409-158">注册表值类型必须是 () 的字符串 `REG_SZ` ，以便用来表示小数值。</span><span class="sxs-lookup"><span data-stu-id="ca409-158">The registry value type must be a String (`REG_SZ`), so that the fractional values can be represented with.</span></span>
> <span data-ttu-id="ca409-159">小数点。</span><span class="sxs-lookup"><span data-stu-id="ca409-159">a decimal point.</span></span> <span data-ttu-id="ca409-160">`REG_DWORD`即使对于整数百分比，使用 DWord () 也_不_起作用。</span><span class="sxs-lookup"><span data-stu-id="ca409-160">Using DWord (`REG_DWORD`) will _not_ work, even for whole number percentages.</span></span>

### <a name="additional-preferences"></a><span data-ttu-id="ca409-161">其他首选项</span><span class="sxs-lookup"><span data-stu-id="ca409-161">Additional preferences</span></span>

<span data-ttu-id="ca409-162">其他首选项集是首选项子项中的字符串值：</span><span class="sxs-lookup"><span data-stu-id="ca409-162">The remaining set of preferences is String values in the Preferences subkey:</span></span>
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK\Preferences
```

| <span data-ttu-id="ca409-163">注册表值</span><span class="sxs-lookup"><span data-stu-id="ca409-163">Registry Value</span></span>               | <span data-ttu-id="ca409-164">默认值</span><span class="sxs-lookup"><span data-stu-id="ca409-164">Default Value</span></span>      | <span data-ttu-id="ca409-165">说明</span><span class="sxs-lookup"><span data-stu-id="ca409-165">Description</span></span>                                                                                         |
| ---------------------------- | ------------------ | --------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="ca409-166">AudioFeedback_Disabled</span><span class="sxs-lookup"><span data-stu-id="ca409-166">AudioFeedback_Disabled</span></span>       | <span data-ttu-id="ca409-167">"0"</span><span class="sxs-lookup"><span data-stu-id="ca409-167">"0"</span></span>                | <span data-ttu-id="ca409-168">"0" 启用密钥单击音频反馈;"1" 禁用该方法。</span><span class="sxs-lookup"><span data-stu-id="ca409-168">"0" enables the key click audio feedback; "1" disables it.</span></span>                                          |
| <span data-ttu-id="ca409-169">Dictation_Disabled</span><span class="sxs-lookup"><span data-stu-id="ca409-169">Dictation_Disabled</span></span>           | <span data-ttu-id="ca409-170">"1"</span><span class="sxs-lookup"><span data-stu-id="ca409-170">"1"</span></span>                | <span data-ttu-id="ca409-171">"0" 显示听写 (语音识别) 按钮;"1" 隐藏它。</span><span class="sxs-lookup"><span data-stu-id="ca409-171">"0" shows the dictation (voice recognition) button; "1" hides it.</span></span><br/> <span data-ttu-id="ca409-172">（参阅以下说明）</span><span class="sxs-lookup"><span data-stu-id="ca409-172">(see note below)</span></span>             |
| <span data-ttu-id="ca409-173">KeyboardModeEnabled_full</span><span class="sxs-lookup"><span data-stu-id="ca409-173">KeyboardModeEnabled_full</span></span>     | <span data-ttu-id="ca409-174">"0"</span><span class="sxs-lookup"><span data-stu-id="ca409-174">"0"</span></span>                | <span data-ttu-id="ca409-175">"0" 禁用全键盘模式;"1" 启用它。</span><span class="sxs-lookup"><span data-stu-id="ca409-175">"0" disables the full keyboard mode; "1" enables it.</span></span>                                                |
| <span data-ttu-id="ca409-176">KeyboardModeEnabled_narrow</span><span class="sxs-lookup"><span data-stu-id="ca409-176">KeyboardModeEnabled_narrow</span></span>   | <span data-ttu-id="ca409-177">"1"</span><span class="sxs-lookup"><span data-stu-id="ca409-177">"1"</span></span>                | <span data-ttu-id="ca409-178">"0" 禁用窄幅键盘模式;"1" 启用它。</span><span class="sxs-lookup"><span data-stu-id="ca409-178">"0" disables the narrow keyboard mode; "1" enables it.</span></span>                                              |
| <span data-ttu-id="ca409-179">KeyboardModeEnabled_wide</span><span class="sxs-lookup"><span data-stu-id="ca409-179">KeyboardModeEnabled_wide</span></span>     | <span data-ttu-id="ca409-180">"1"</span><span class="sxs-lookup"><span data-stu-id="ca409-180">"1"</span></span>                | <span data-ttu-id="ca409-181">"0" 禁用宽键盘模式;"1" 启用它。</span><span class="sxs-lookup"><span data-stu-id="ca409-181">"0" disables the wide keyboard mode; "1" enables it.</span></span>                                                |
| <span data-ttu-id="ca409-182">ModeOrder</span><span class="sxs-lookup"><span data-stu-id="ca409-182">ModeOrder</span></span>                    | <span data-ttu-id="ca409-183">"宽; 窄; 完全"</span><span class="sxs-lookup"><span data-stu-id="ca409-183">"wide;narrow;full"</span></span> | <span data-ttu-id="ca409-184">顺序 (从左到右) ，其中模式在 "模式" 下拉菜单中列出（如果已启用）</span><span class="sxs-lookup"><span data-stu-id="ca409-184">The order (from left to right) in which the modes are listed in the mode drop-down menu, if enabled</span></span> |
| <span data-ttu-id="ca409-185">SettingsMenuKey_Collapsed</span><span class="sxs-lookup"><span data-stu-id="ca409-185">SettingsMenuKey_Collapsed</span></span>    | <span data-ttu-id="ca409-186">"0"</span><span class="sxs-lookup"><span data-stu-id="ca409-186">"0"</span></span>                | <span data-ttu-id="ca409-187">隐藏模式下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="ca409-187">Hides the mode drop-down menu.</span></span> <span data-ttu-id="ca409-188">如果只启用了一种模式，则将此项设置为 "1"。</span><span class="sxs-lookup"><span data-stu-id="ca409-188">Set this to "1" if only one mode is enabled.</span></span>                         |
| <span data-ttu-id="ca409-189">Paste_Disabled</span><span class="sxs-lookup"><span data-stu-id="ca409-189">Paste_Disabled</span></span>               | <span data-ttu-id="ca409-190">"0"</span><span class="sxs-lookup"><span data-stu-id="ca409-190">"0"</span></span>                | <span data-ttu-id="ca409-191">"0" 显示 "粘贴" 按钮;"1" 隐藏它。</span><span class="sxs-lookup"><span data-stu-id="ca409-191">"0" shows the Paste button; "1" hides it.</span></span><br/> <span data-ttu-id="ca409-192">更改将在重新启动后生效。</span><span class="sxs-lookup"><span data-stu-id="ca409-192">Change takes effect after reboot.</span></span>                    |
| <span data-ttu-id="ca409-193">CloseButton_Disabled</span><span class="sxs-lookup"><span data-stu-id="ca409-193">CloseButton_Disabled</span></span>         | <span data-ttu-id="ca409-194">"0"</span><span class="sxs-lookup"><span data-stu-id="ca409-194">"0"</span></span>                | <span data-ttu-id="ca409-195">"0" 显示 "关闭" 按钮;"1" 隐藏 "关闭" 按钮</span><span class="sxs-lookup"><span data-stu-id="ca409-195">"0" shows the Close button; "1" hides the Close button</span></span><br/> <span data-ttu-id="ca409-196">更改将在重新启动后生效。</span><span class="sxs-lookup"><span data-stu-id="ca409-196">Change takes effect after reboot.</span></span>       |
| <span data-ttu-id="ca409-197">EmojiKeyEnabled</span><span class="sxs-lookup"><span data-stu-id="ca409-197">EmojiKeyEnabled</span></span>              | <span data-ttu-id="ca409-198">"0"</span><span class="sxs-lookup"><span data-stu-id="ca409-198">"0"</span></span>                | <span data-ttu-id="ca409-199">"0" 隐藏表情符号键;"1" 显示，允许用户输入表情符号字符。</span><span class="sxs-lookup"><span data-stu-id="ca409-199">"0" hides the Emoji key; "1" shows it, allowing the user to enter Emoji characters.</span></span>                 |

> [!NOTE]
> <span data-ttu-id="ca409-200">听写模式需要为所选输入语言以及音频输入设备安装语音包。</span><span class="sxs-lookup"><span data-stu-id="ca409-200">Dictation mode requires a speech package to be installed for the selected input language, as well as an audio input device.</span></span> <span data-ttu-id="ca409-201">如果未安装匹配的语音包，则不会显示 "听写" 按钮。</span><span class="sxs-lookup"><span data-stu-id="ca409-201">If a matching speech packages is not installed, the dictation button will not be shown.</span></span>
> 
> <span data-ttu-id="ca409-202">所有映像都包含 en-us 语音语言。</span><span class="sxs-lookup"><span data-stu-id="ca409-202">All images include the en-US speech language.</span></span> <span data-ttu-id="ca409-203">其他语音包作为可选功能安装。</span><span class="sxs-lookup"><span data-stu-id="ca409-203">Other speech packages are installed as optional features.</span></span>
> <span data-ttu-id="ca409-204">有关 IoT 功能的详细信息，请参阅 [Iot 核心功能列表](/windows-hardware/manufacture/iot/iot-core-feature-list) 和 [iot 核心制造指南](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="ca409-204">For more information about IoT Features, see [IoT Core Feature List](/windows-hardware/manufacture/iot/iot-core-feature-list) and [IoT Core manufacturing guide](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

<span data-ttu-id="ca409-205">例如，若要仅启用 `wide` 键盘模式，请在 PowerShell 中执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ca409-205">As an example, to enable only `wide` keyboard mode, in PowerShell you could do the following:</span></span>
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
