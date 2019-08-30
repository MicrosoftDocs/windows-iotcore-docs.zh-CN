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
# <a name="on-screen-keyboard-language-layouts"></a><span data-ttu-id="9a7b5-104">屏幕键盘语言布局</span><span class="sxs-lookup"><span data-stu-id="9a7b5-104">On-Screen Keyboard Language Layouts</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a7b5-105">从 Windows 10 IoT Core 版本 1809, 本文不再适用。</span><span class="sxs-lookup"><span data-stu-id="9a7b5-105">As of Windows 10 IoT Core, version 1809, this article is no longer applicable.</span></span> <span data-ttu-id="9a7b5-106">请参阅当前文档的 "[用于头设备的屏幕键盘](./OnScreenKeyboard.md)" 页。</span><span class="sxs-lookup"><span data-stu-id="9a7b5-106">Please see the [On-screen keyboard for headed devices](./OnScreenKeyboard.md) page for the current documentation.</span></span>

<span data-ttu-id="9a7b5-107">Windows 10 IoT Core (版本1703、1709和 1803) 中的屏幕键盘 (OSK) 支持以下语言的布局:</span><span class="sxs-lookup"><span data-stu-id="9a7b5-107">The on-screen keyboard (OSK) in Windows 10 IoT Core, versions 1703, 1709, and 1803, supports layouts for the following languages:</span></span>

| <span data-ttu-id="9a7b5-108">语言标记</span><span class="sxs-lookup"><span data-stu-id="9a7b5-108">Language Tag</span></span>  | <span data-ttu-id="9a7b5-109">描述</span><span class="sxs-lookup"><span data-stu-id="9a7b5-109">Description</span></span>             | <span data-ttu-id="9a7b5-110">布局代码</span><span class="sxs-lookup"><span data-stu-id="9a7b5-110">Layout Code</span></span> |
| :------------ | :---------------------- | -----------:|
| <span data-ttu-id="9a7b5-111">en-US</span><span class="sxs-lookup"><span data-stu-id="9a7b5-111">en-US</span></span>         | <span data-ttu-id="9a7b5-112">英语(美国)</span><span class="sxs-lookup"><span data-stu-id="9a7b5-112">English (United States)</span></span> |    <span data-ttu-id="9a7b5-113">00000409</span><span class="sxs-lookup"><span data-stu-id="9a7b5-113">00000409</span></span> |
| <span data-ttu-id="9a7b5-114">en-AU</span><span class="sxs-lookup"><span data-stu-id="9a7b5-114">en-AU</span></span>         | <span data-ttu-id="9a7b5-115">英语（澳大利亚）</span><span class="sxs-lookup"><span data-stu-id="9a7b5-115">English (Australia)</span></span>     |    <span data-ttu-id="9a7b5-116">00000C09</span><span class="sxs-lookup"><span data-stu-id="9a7b5-116">00000C09</span></span> |
| <span data-ttu-id="9a7b5-117">en-CA</span><span class="sxs-lookup"><span data-stu-id="9a7b5-117">en-CA</span></span>         | <span data-ttu-id="9a7b5-118">英语（加拿大）</span><span class="sxs-lookup"><span data-stu-id="9a7b5-118">English (Canada)</span></span>        |    <span data-ttu-id="9a7b5-119">00001009</span><span class="sxs-lookup"><span data-stu-id="9a7b5-119">00001009</span></span> |
| <span data-ttu-id="9a7b5-120">en-GB</span><span class="sxs-lookup"><span data-stu-id="9a7b5-120">en-GB</span></span>         | <span data-ttu-id="9a7b5-121">英语 (英国)</span><span class="sxs-lookup"><span data-stu-id="9a7b5-121">English (Great Britain)</span></span> |    <span data-ttu-id="9a7b5-122">00000809</span><span class="sxs-lookup"><span data-stu-id="9a7b5-122">00000809</span></span> |
| <span data-ttu-id="9a7b5-123">es-ES</span><span class="sxs-lookup"><span data-stu-id="9a7b5-123">es-ES</span></span>         | <span data-ttu-id="9a7b5-124">西班牙语(西班牙)</span><span class="sxs-lookup"><span data-stu-id="9a7b5-124">Spanish (Spain)</span></span>         |    <span data-ttu-id="9a7b5-125">0000040A</span><span class="sxs-lookup"><span data-stu-id="9a7b5-125">0000040A</span></span> |
| <span data-ttu-id="9a7b5-126">es-MX</span><span class="sxs-lookup"><span data-stu-id="9a7b5-126">es-MX</span></span>         | <span data-ttu-id="9a7b5-127">西班牙语(墨西哥)</span><span class="sxs-lookup"><span data-stu-id="9a7b5-127">Spanish (Mexico)</span></span>        |    <span data-ttu-id="9a7b5-128">0000080A</span><span class="sxs-lookup"><span data-stu-id="9a7b5-128">0000080A</span></span> |
| <span data-ttu-id="9a7b5-129">de-DE</span><span class="sxs-lookup"><span data-stu-id="9a7b5-129">de-DE</span></span>         | <span data-ttu-id="9a7b5-130">德语</span><span class="sxs-lookup"><span data-stu-id="9a7b5-130">German</span></span>                  |    <span data-ttu-id="9a7b5-131">00000407</span><span class="sxs-lookup"><span data-stu-id="9a7b5-131">00000407</span></span> |
| <span data-ttu-id="9a7b5-132">fr-CA</span><span class="sxs-lookup"><span data-stu-id="9a7b5-132">fr-CA</span></span>         | <span data-ttu-id="9a7b5-133">法语(加拿大)</span><span class="sxs-lookup"><span data-stu-id="9a7b5-133">French (Canada)</span></span>         |    <span data-ttu-id="9a7b5-134">00000C0C</span><span class="sxs-lookup"><span data-stu-id="9a7b5-134">00000C0C</span></span> |
| <span data-ttu-id="9a7b5-135">fr-FR</span><span class="sxs-lookup"><span data-stu-id="9a7b5-135">fr-FR</span></span>         | <span data-ttu-id="9a7b5-136">法语(法国)</span><span class="sxs-lookup"><span data-stu-id="9a7b5-136">French (France)</span></span>         |    <span data-ttu-id="9a7b5-137">0000040C</span><span class="sxs-lookup"><span data-stu-id="9a7b5-137">0000040C</span></span> |
| <span data-ttu-id="9a7b5-138">it-IT</span><span class="sxs-lookup"><span data-stu-id="9a7b5-138">it-IT</span></span>         | <span data-ttu-id="9a7b5-139">意大利语</span><span class="sxs-lookup"><span data-stu-id="9a7b5-139">Italian</span></span>                 |    <span data-ttu-id="9a7b5-140">00000410</span><span class="sxs-lookup"><span data-stu-id="9a7b5-140">00000410</span></span> |
| <span data-ttu-id="9a7b5-141">pt-BR</span><span class="sxs-lookup"><span data-stu-id="9a7b5-141">pt-BR</span></span>         | <span data-ttu-id="9a7b5-142">葡萄牙语（巴西）</span><span class="sxs-lookup"><span data-stu-id="9a7b5-142">Portuguese (Brazil)</span></span>     |    <span data-ttu-id="9a7b5-143">00000416</span><span class="sxs-lookup"><span data-stu-id="9a7b5-143">00000416</span></span> |

<span data-ttu-id="9a7b5-144">按住 OSK 的 "& 123" 按钮, 用户可以选择要使用的布局:</span><span class="sxs-lookup"><span data-stu-id="9a7b5-144">By pressing and holding the OSK's "&123" button, the user can select which layout they want to use:</span></span>

![所有语言](../media/OnScreenKeyboard/AllLanguages.png)
 
<span data-ttu-id="9a7b5-146">但作为 OEM, 你可以限制向用户显示哪些布局选项。</span><span class="sxs-lookup"><span data-stu-id="9a7b5-146">As an OEM, however, you can limit which layout choices are displayed to the user.</span></span> <span data-ttu-id="9a7b5-147">若要限制显示用户的布局, 请首先参考[TechNet 上的键盘布局 doucmentation](https://technet.microsoft.com/library/cc978687.aspx)中的指南。</span><span class="sxs-lookup"><span data-stu-id="9a7b5-147">To limit which layouts to show the user, first reference the guidance from the [Keyboard Layout doucmentation on TechNet](https://technet.microsoft.com/library/cc978687.aspx).</span></span>
 
<span data-ttu-id="9a7b5-148">对于具体的示例, 如果只想允许北美语言布局 (en-us、en CA、es MX、fr-CA), 则可以将以下内容添加到 OEMCustomization 脚本:</span><span class="sxs-lookup"><span data-stu-id="9a7b5-148">For a concrete example, if you want to only allow North America language layouts (en-US, en-CA, es-MX, fr-CA), you could add the following to your OEMCustomization.cmd script:</span></span>

```console
call "%~dp0\setKeyboardLanguages.cmd"
```

<span data-ttu-id="9a7b5-149">其中, setKeyboardLanguages 是包含以下内容的同一目录中的脚本:</span><span class="sxs-lookup"><span data-stu-id="9a7b5-149">Where setKeyboardLanguages.cmd is a script in the same directory containing this:</span></span>
 
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

<span data-ttu-id="9a7b5-150">上述命令脚本生成的结果将为:</span><span class="sxs-lookup"><span data-stu-id="9a7b5-150">The resulting effect of the above command script will be:</span></span>

![北美语言](../media/OnScreenKeyboard/NorthAmericanLanguages.png)

### <a name="some-things-to-note"></a><span data-ttu-id="9a7b5-152">需要注意的一些事项:</span><span class="sxs-lookup"><span data-stu-id="9a7b5-152">Some things to note:</span></span>
*  <span data-ttu-id="9a7b5-153">值名称指示小数序列。</span><span class="sxs-lookup"><span data-stu-id="9a7b5-153">The value names indicate a decimal sequence.</span></span>
*  <span data-ttu-id="9a7b5-154">值为字符串值 (REG_SZ)。</span><span class="sxs-lookup"><span data-stu-id="9a7b5-154">The values are string values (REG_SZ).</span></span>
*  <span data-ttu-id="9a7b5-155">当然, 上述脚本文本可以直接添加到 OEMCustomization 脚本。</span><span class="sxs-lookup"><span data-stu-id="9a7b5-155">The script text above, of course, could be added directly into the OEMCustomization.cmd script.</span></span>
*  <span data-ttu-id="9a7b5-156">**请勿**删除 "预加载" 注册表项, 因为它对其设置了权限, 以允许屏幕键盘应用程序读取其值。</span><span class="sxs-lookup"><span data-stu-id="9a7b5-156">**Do not** delete the "Preload" registry key since it has permissions set on it specifically to allow the on-screen keyboard application to read its values.</span></span>
*  <span data-ttu-id="9a7b5-157">要使这些说明适用, 您的映像必须包含以下功能 \*:</span><span class="sxs-lookup"><span data-stu-id="9a7b5-157">A prerequisite for these instructions to be applicable, is that your image must include the following features\*:</span></span>
   * <span data-ttu-id="9a7b5-158">IOT_SHELL_ONSCREEN_KEYBOARD</span><span class="sxs-lookup"><span data-stu-id="9a7b5-158">IOT_SHELL_ONSCREEN_KEYBOARD</span></span>
   * <span data-ttu-id="9a7b5-159">IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS</span><span class="sxs-lookup"><span data-stu-id="9a7b5-159">IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS</span></span>

<span data-ttu-id="9a7b5-160">有关 IoT 功能的详细信息, 请参阅[Iot 核心功能列表](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-feature-list)。</span><span class="sxs-lookup"><span data-stu-id="9a7b5-160">For more information about IoT Features, see [IoT Core Feature List](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-feature-list).</span></span>
