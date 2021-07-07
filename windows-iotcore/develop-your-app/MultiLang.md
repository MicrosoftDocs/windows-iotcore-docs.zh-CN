---
title: Windows 10 IoT 核心版语言支持
author: msalehmsft
ms.author: msaleh
ms.date: 09/12/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解 UWP 应用程序和 IoT Core 上的 OS 中的多种语言支持。
keywords: windows iot， 语言， 应用类型， UWP， OS
ms.openlocfilehash: c2f631d0c59190e392c622b3b5c899f7aafd1566
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228993"
---
# <a name="language-support"></a><span data-ttu-id="69aef-104">语言支持</span><span class="sxs-lookup"><span data-stu-id="69aef-104">Language Support</span></span>

<span data-ttu-id="69aef-105">语言支持可以在两个级别启用：应用程序级别和 OS 级别，具体取决于在映像上提供的语言资源。</span><span class="sxs-lookup"><span data-stu-id="69aef-105">Language support can be enabled at two levels, Application level and OS level, depending on the language resources made available on the image.</span></span>

## <a name="languages-in-uwp-applications"></a><span data-ttu-id="69aef-106">UWP 应用程序中的语言</span><span class="sxs-lookup"><span data-stu-id="69aef-106">Languages in UWP Applications</span></span>
<span data-ttu-id="69aef-107">UWP 应用程序语言不限于 OS 中包含的语言。</span><span class="sxs-lookup"><span data-stu-id="69aef-107">UWP application languages are not limited to the languages included in the OS.</span></span>  <span data-ttu-id="69aef-108">事实上，不触发 shell UI 或利用语音资源的 IoT 设备可以通过其 UWP 应用程序以许多不同的语言提供设备体验，即使基础 Windows 10 IoT 核心版 OS 是在 en-US 默认模式下构建的。</span><span class="sxs-lookup"><span data-stu-id="69aef-108">In fact, an IoT device that does not trigger shell UI or utilize speech resources can provide a device experience in many different languages through its UWP applications even though the underlying Windows 10 IoT Core OS is built simply in the en-US default mode.</span></span> 

<span data-ttu-id="69aef-109">UWP 应用程序必须为需要支持的语言提供资源。</span><span class="sxs-lookup"><span data-stu-id="69aef-109">UWP applications must provide the resources for the languages that are required to be supported.</span></span> <span data-ttu-id="69aef-110">[Windows。Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) API 可用于指定与语言相关的首选项。</span><span class="sxs-lookup"><span data-stu-id="69aef-110">[Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) APIs can be used to specify the language-related preferences.</span></span>

<span data-ttu-id="69aef-111">请参阅下面的示例应用程序：</span><span class="sxs-lookup"><span data-stu-id="69aef-111">See the below sample applications:</span></span>

* [<span data-ttu-id="69aef-112">IoTDefaultApp 示例</span><span class="sxs-lookup"><span data-stu-id="69aef-112">IoTDefaultApp sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [<span data-ttu-id="69aef-113">ApplicationResources 示例</span><span class="sxs-lookup"><span data-stu-id="69aef-113">ApplicationResources sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a><span data-ttu-id="69aef-114">OS 中的语言</span><span class="sxs-lookup"><span data-stu-id="69aef-114">Languages in OS</span></span>

<span data-ttu-id="69aef-115">Windows 10IoTCore 工具包现在包括以下语言的语言资源：</span><span class="sxs-lookup"><span data-stu-id="69aef-115">Windows 10 IoTCore kits now include the language resources for the following languages:</span></span>

> | <span data-ttu-id="69aef-116">语言</span><span class="sxs-lookup"><span data-stu-id="69aef-116">Language</span></span>  | <span data-ttu-id="69aef-117">代码</span><span class="sxs-lookup"><span data-stu-id="69aef-117">Code</span></span> | <span data-ttu-id="69aef-118">区域</span><span class="sxs-lookup"><span data-stu-id="69aef-118">Region</span></span> |
> |-------------|-----|-----|
> | <span data-ttu-id="69aef-119">英语（美国）</span><span class="sxs-lookup"><span data-stu-id="69aef-119">English (United States)</span></span> | <span data-ttu-id="69aef-120">zh-CN</span><span class="sxs-lookup"><span data-stu-id="69aef-120">en-US</span></span> | <span data-ttu-id="69aef-121">北美</span><span class="sxs-lookup"><span data-stu-id="69aef-121">North America</span></span> | 
> | <span data-ttu-id="69aef-122">英语(英国)</span><span class="sxs-lookup"><span data-stu-id="69aef-122">English (UK)</span></span> | <span data-ttu-id="69aef-123">en-GB</span><span class="sxs-lookup"><span data-stu-id="69aef-123">en-GB</span></span> | <span data-ttu-id="69aef-124">欧洲</span><span class="sxs-lookup"><span data-stu-id="69aef-124">Europe</span></span> |
> | <span data-ttu-id="69aef-125">法语（法国）</span><span class="sxs-lookup"><span data-stu-id="69aef-125">French (France)</span></span> | <span data-ttu-id="69aef-126">fr-FR</span><span class="sxs-lookup"><span data-stu-id="69aef-126">fr-FR</span></span> | <span data-ttu-id="69aef-127">欧洲</span><span class="sxs-lookup"><span data-stu-id="69aef-127">Europe</span></span> |
> | <span data-ttu-id="69aef-128">法语（加拿大）</span><span class="sxs-lookup"><span data-stu-id="69aef-128">French (Canada)</span></span> | <span data-ttu-id="69aef-129">fr-CA</span><span class="sxs-lookup"><span data-stu-id="69aef-129">fr-CA</span></span> | <span data-ttu-id="69aef-130">北美</span><span class="sxs-lookup"><span data-stu-id="69aef-130">North America</span></span> |
> | <span data-ttu-id="69aef-131">西班牙语(西班牙)</span><span class="sxs-lookup"><span data-stu-id="69aef-131">Spanish (Spain)</span></span> | <span data-ttu-id="69aef-132">es-ES</span><span class="sxs-lookup"><span data-stu-id="69aef-132">es-ES</span></span> | <span data-ttu-id="69aef-133">欧洲</span><span class="sxs-lookup"><span data-stu-id="69aef-133">Europe</span></span> |
> | <span data-ttu-id="69aef-134">西班牙语(墨西哥)</span><span class="sxs-lookup"><span data-stu-id="69aef-134">Spanish (Mexico)</span></span> | <span data-ttu-id="69aef-135">es-MX</span><span class="sxs-lookup"><span data-stu-id="69aef-135">es-MX</span></span> | <span data-ttu-id="69aef-136">北美</span><span class="sxs-lookup"><span data-stu-id="69aef-136">North America</span></span> |
> | <span data-ttu-id="69aef-137">中文</span><span class="sxs-lookup"><span data-stu-id="69aef-137">Chinese</span></span> | <span data-ttu-id="69aef-138">zh-CN</span><span class="sxs-lookup"><span data-stu-id="69aef-138">zh-CN</span></span> | <span data-ttu-id="69aef-139">亚洲</span><span class="sxs-lookup"><span data-stu-id="69aef-139">Asia</span></span> | 
> | <span data-ttu-id="69aef-140">阿拉伯语</span><span class="sxs-lookup"><span data-stu-id="69aef-140">Arabic</span></span> | <span data-ttu-id="69aef-141">ar-SA</span><span class="sxs-lookup"><span data-stu-id="69aef-141">ar-SA</span></span> | <span data-ttu-id="69aef-142">亚洲</span><span class="sxs-lookup"><span data-stu-id="69aef-142">Asia</span></span> |
> | <span data-ttu-id="69aef-143">德语</span><span class="sxs-lookup"><span data-stu-id="69aef-143">German</span></span> | <span data-ttu-id="69aef-144">de-DE</span><span class="sxs-lookup"><span data-stu-id="69aef-144">de-DE</span></span> | <span data-ttu-id="69aef-145">欧洲</span><span class="sxs-lookup"><span data-stu-id="69aef-145">Europe</span></span> |
> | <span data-ttu-id="69aef-146">意大利语</span><span class="sxs-lookup"><span data-stu-id="69aef-146">Italian</span></span> | <span data-ttu-id="69aef-147">it-IT</span><span class="sxs-lookup"><span data-stu-id="69aef-147">it-IT</span></span> | <span data-ttu-id="69aef-148">欧洲</span><span class="sxs-lookup"><span data-stu-id="69aef-148">Europe</span></span> | 
> | <span data-ttu-id="69aef-149">日语</span><span class="sxs-lookup"><span data-stu-id="69aef-149">Japanese</span></span> | <span data-ttu-id="69aef-150">ja-JP</span><span class="sxs-lookup"><span data-stu-id="69aef-150">ja-JP</span></span> | <span data-ttu-id="69aef-151">亚洲</span><span class="sxs-lookup"><span data-stu-id="69aef-151">Asia</span></span> |
> | <span data-ttu-id="69aef-152">韩语</span><span class="sxs-lookup"><span data-stu-id="69aef-152">Korean</span></span> | <span data-ttu-id="69aef-153">ko-KR</span><span class="sxs-lookup"><span data-stu-id="69aef-153">ko-KR</span></span> | <span data-ttu-id="69aef-154">亚洲</span><span class="sxs-lookup"><span data-stu-id="69aef-154">Asia</span></span> |
> | <span data-ttu-id="69aef-155">荷兰语</span><span class="sxs-lookup"><span data-stu-id="69aef-155">Dutch</span></span> | <span data-ttu-id="69aef-156">nl-NL</span><span class="sxs-lookup"><span data-stu-id="69aef-156">nl-NL</span></span> | <span data-ttu-id="69aef-157">欧洲</span><span class="sxs-lookup"><span data-stu-id="69aef-157">Europe</span></span> |
> | <span data-ttu-id="69aef-158">波兰语</span><span class="sxs-lookup"><span data-stu-id="69aef-158">Polish</span></span> | <span data-ttu-id="69aef-159">pl-PL</span><span class="sxs-lookup"><span data-stu-id="69aef-159">pl-PL</span></span> | <span data-ttu-id="69aef-160">欧洲</span><span class="sxs-lookup"><span data-stu-id="69aef-160">Europe</span></span> | 
> | <span data-ttu-id="69aef-161">罗马尼亚语</span><span class="sxs-lookup"><span data-stu-id="69aef-161">Romanian</span></span> | <span data-ttu-id="69aef-162">ro-RO</span><span class="sxs-lookup"><span data-stu-id="69aef-162">ro-RO</span></span> | <span data-ttu-id="69aef-163">欧洲</span><span class="sxs-lookup"><span data-stu-id="69aef-163">Europe</span></span> |
> | <span data-ttu-id="69aef-164">俄语</span><span class="sxs-lookup"><span data-stu-id="69aef-164">Russian</span></span> | <span data-ttu-id="69aef-165">ru-RU</span><span class="sxs-lookup"><span data-stu-id="69aef-165">ru-RU</span></span> | <span data-ttu-id="69aef-166">欧洲</span><span class="sxs-lookup"><span data-stu-id="69aef-166">Europe</span></span> |
> | <span data-ttu-id="69aef-167">希腊语</span><span class="sxs-lookup"><span data-stu-id="69aef-167">Greek</span></span> | <span data-ttu-id="69aef-168">el-GR</span><span class="sxs-lookup"><span data-stu-id="69aef-168">el-GR</span></span> | <span data-ttu-id="69aef-169">欧洲</span><span class="sxs-lookup"><span data-stu-id="69aef-169">Europe</span></span> |
> | <span data-ttu-id="69aef-170">巴西 (语) </span><span class="sxs-lookup"><span data-stu-id="69aef-170">Portugese (Brazil)</span></span> | <span data-ttu-id="69aef-171">pt-BR</span><span class="sxs-lookup"><span data-stu-id="69aef-171">pt-BR</span></span> | <span data-ttu-id="69aef-172">南美洲/欧洲</span><span class="sxs-lookup"><span data-stu-id="69aef-172">South America/Europe</span></span> |
> | <span data-ttu-id="69aef-173">葡萄牙 (语) </span><span class="sxs-lookup"><span data-stu-id="69aef-173">Portuese (Portugal)</span></span> | <span data-ttu-id="69aef-174">pt-PT</span><span class="sxs-lookup"><span data-stu-id="69aef-174">pt-PT</span></span> | <span data-ttu-id="69aef-175">南美洲/欧洲</span><span class="sxs-lookup"><span data-stu-id="69aef-175">South America/Europe</span></span> |

<span data-ttu-id="69aef-176">这些语言资源包含 UI 字符串、语音语言和语音 (语音合成) 。</span><span class="sxs-lookup"><span data-stu-id="69aef-176">These language resources contain UI strings, speech language, and voices (speech synthesis).</span></span> <span data-ttu-id="69aef-177">WindowsIoT 映像可以使用其中一个或多个资源生成，必须在映像期间指定，以后不能修改。</span><span class="sxs-lookup"><span data-stu-id="69aef-177">Windows IoT images can be built with one or more of these resources and they must be specified during the image time and cannot be modified later.</span></span> <span data-ttu-id="69aef-178">请注意，与 UI 语言相关的资源独立于语音语言和语音资源。</span><span class="sxs-lookup"><span data-stu-id="69aef-178">Note that UI language-related resources are independent than speech language and voice resources.</span></span>

### <a name="specifying-ui-and-speech-resources"></a><span data-ttu-id="69aef-179">指定 UI 和语音资源</span><span class="sxs-lookup"><span data-stu-id="69aef-179">Specifying UI and Speech resources</span></span> 
<span data-ttu-id="69aef-180">在 OEM 输入 xml 文件中，指定所需的 UI 和语音语言，如下所示</span><span class="sxs-lookup"><span data-stu-id="69aef-180">In the OEM Input xml file, the required UI and speech languages are specified as shown below</span></span>

``` xml
  <SupportedLanguages>
    <UserInterface>
      <Language>en-US</Language>
      <Language>en-GB</Language> 
      <Language>fr-CA</Language> 
      <Language>es-MX</Language> 
      <Language>es-ES</Language> 
      <Language>fr-FR</Language>
    </UserInterface>
    <Keyboard>
      <Language>en-US</Language>
      <Language>en-GB</Language> 
      <Language>fr-CA</Language> 
      <Language>es-MX</Language> 
      <Language>es-ES</Language> 
      <Language>fr-FR</Language>
    </Keyboard>
    <Speech>
      <Language>en-US</Language>
      <Language>en-GB</Language> 
      <Language>fr-CA</Language> 
      <Language>es-MX</Language> 
      <Language>es-ES</Language> 
      <Language>fr-FR</Language>
    </Speech>
  </SupportedLanguages>
  <BootUILanguage>en-us</BootUILanguage>
  <BootLocale>en-us</BootLocale>
```


### <a name="specifying-speech-data-resources"></a><span data-ttu-id="69aef-181">指定语音数据资源</span><span class="sxs-lookup"><span data-stu-id="69aef-181">Specifying Speech Data resources</span></span>
<span data-ttu-id="69aef-182">在 OEM 输入 xml 文件中，指定所需的语音数据资源，如下所示，</span><span class="sxs-lookup"><span data-stu-id="69aef-182">In the OEM Input xml file, the required speech data resources are specified as shown below,</span></span>

``` xml
    <Microsoft>
       ...
      <Feature>IOT_SPEECHDATA_EN_CA</Feature>
      <Feature>IOT_SPEECHDATA_ES_MX</Feature> 
      <Feature>IOT_SPEECHDATA_FR_CA</Feature> 
      <Feature>IOT_SPEECHDATA_EN_GB</Feature>
      <Feature>IOT_SPEECHDATA_ES_ES</Feature>  
      <Feature>IOT_SPEECHDATA_FR_FR</Feature> 
    </Microsoft>
```

> [!NOTE]
> <span data-ttu-id="69aef-183">默认情况下，en-US 语音数据包含在图像中。</span><span class="sxs-lookup"><span data-stu-id="69aef-183">By default, en-US speech data is included in the image.</span></span>

### <a name="samples"></a><span data-ttu-id="69aef-184">示例</span><span class="sxs-lookup"><span data-stu-id="69aef-184">Samples</span></span>
* <span data-ttu-id="69aef-185">有关[多种语言支持，请参阅 MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample)</span><span class="sxs-lookup"><span data-stu-id="69aef-185">See [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) for multiple languages support</span></span>
* <span data-ttu-id="69aef-186">请参阅 [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) 了解 fr-FR 语言，将 en-US 用作回退语言。</span><span class="sxs-lookup"><span data-stu-id="69aef-186">See [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) for fr-FR language with en-US as fallback language.</span></span>
    * <span data-ttu-id="69aef-187">请注意，当更改启动 UI 语言时，帐户名称 `administrator` 也会以启动 UI 语言翻译。</span><span class="sxs-lookup"><span data-stu-id="69aef-187">Note that when the boot UI language is changed, the `administrator` account name is also translated in the boot UI language.</span></span> <span data-ttu-id="69aef-188">因此，在 fr-FR 中，它是 `administrateur` 。</span><span class="sxs-lookup"><span data-stu-id="69aef-188">So, in fr-FR it is `administrateur`.</span></span> <span data-ttu-id="69aef-189">请参阅 [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span><span class="sxs-lookup"><span data-stu-id="69aef-189">See [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span></span>

## <a name="changing-user-preferences-language-region-speech-and-voice"></a><span data-ttu-id="69aef-190">更改用户首选项 (语言、区域、语音和语音) </span><span class="sxs-lookup"><span data-stu-id="69aef-190">Changing user preferences (language, region, speech and voice)</span></span>

<span data-ttu-id="69aef-191">UWP 应用程序可以使用 WinRT API 来设置默认应该使用的区域、首选 UI 语言列表、语音语言和语音。</span><span class="sxs-lookup"><span data-stu-id="69aef-191">UWP application can use WinRT APIs to set the region, preferred UI language list, speech language and voice that should be by default used.</span></span> <span data-ttu-id="69aef-192">设置首选 UI 语言列表后，UWP 应用程序将尝试加载相应的 (，除非应用程序以编程方式阻止) 。</span><span class="sxs-lookup"><span data-stu-id="69aef-192">Once preferred UI language list set, UWP application will try to load the corresponding resources (unless application programmatically prevents that).</span></span>
 
<span data-ttu-id="69aef-193">如果应用程序没有相应的资源，则加载回退资源。</span><span class="sxs-lookup"><span data-stu-id="69aef-193">If the application doesn’t have the corresponding resources, then fallback resources will be loaded.</span></span> <span data-ttu-id="69aef-194">同样，如果首选语言的 OS 资源不是 Windows IoT 映像的一部分，Windows IoT 将使用其回退资源（可能是英语 (en-US) ）。</span><span class="sxs-lookup"><span data-stu-id="69aef-194">Similarly, if the OS resources for the preferred languages aren’t part of the Windows IoT image, Windows IoT will use its fallback ones likely English (en-US).</span></span>

* <span data-ttu-id="69aef-195">在 `TrySetHomeGeographicRegion` tem 中Windows.Sys[ 区域。UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span><span class="sxs-lookup"><span data-stu-id="69aef-195">Set region using `TrySetHomeGeographicRegion` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="69aef-196">在 tem 中Windows.Sys`TrySetLanguages` [ UI 语言。UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span><span class="sxs-lookup"><span data-stu-id="69aef-196">Set UI language using `TrySetLanguages` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="69aef-197">使用 中的 设置 `TrySetSystemSpeechLanguageAsync` 语音[Windows。Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span><span class="sxs-lookup"><span data-stu-id="69aef-197">Set speech language using `TrySetSystemSpeechLanguageAsync` in [Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span></span>
* <span data-ttu-id="69aef-198">在 Windows `TrySetDefaultVoiceAsync` [中设置语音。Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span><span class="sxs-lookup"><span data-stu-id="69aef-198">Set voice using `TrySetDefaultVoiceAsync` in [Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span></span>

> [!NOTE]
> <span data-ttu-id="69aef-199">若要正常运行，Cortana区域、UI 语言和语音语言保持一致，例如：区域 FR、UI 和语音语言 fr-FR 或区域 ES、UI 和语音语言 es-ES。</span><span class="sxs-lookup"><span data-stu-id="69aef-199">For proper functioning, Cortana requires the region, UI language and speech language to be consistent, e.g.: region FR, UI and speech languages fr-FR or region ES, UI and speech languages es-ES.</span></span> <span data-ttu-id="69aef-200">Cortana使用自己的语音，UWP 应用程序无法更改它。</span><span class="sxs-lookup"><span data-stu-id="69aef-200">Cortana uses its own voice, UWP application cannot change it.</span></span>

## <a name="iotsettingsexe"></a><span data-ttu-id="69aef-201">IoTSettings.exe</span><span class="sxs-lookup"><span data-stu-id="69aef-201">IoTSettings.exe</span></span>

<span data-ttu-id="69aef-202">若要详细了解如何更改区域和用户或语音语言的设置以构建 Cortana 启用的产品，请阅读我们的[命令行 Utils](../manage-your-device/CommandLineUtils.md)文档。</span><span class="sxs-lookup"><span data-stu-id="69aef-202">To learn more about changing settings for region and user or speech language to build Cortana enabled products, please read our [Command Line Utils](../manage-your-device/CommandLineUtils.md) documentation.</span></span>
