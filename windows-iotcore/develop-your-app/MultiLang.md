---
title: Windows 10 IoT 核心语言支持
author: msalehmsft
ms.author: msaleh
ms.date: 09/12/2017
ms.topic: article
description: 了解 UWP Core 上的 UWP 应用程序和 OS 中的多语言支持。
keywords: windows iot，语言，应用类型，UWP，OS
ms.openlocfilehash: 5bc44fb090e6e198525e95d6aee6815afd0095da
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918228"
---
# <a name="language-support"></a><span data-ttu-id="d28e4-104">语言支持</span><span class="sxs-lookup"><span data-stu-id="d28e4-104">Language Support</span></span>

<span data-ttu-id="d28e4-105">可以在两个级别上启用语言支持：应用程序级别和操作系统级别，具体取决于映像中提供的语言资源。</span><span class="sxs-lookup"><span data-stu-id="d28e4-105">Language support can be enabled at two levels, Application level and OS level, depending on the language resources made available on the image.</span></span>

## <a name="languages-in-uwp-applications"></a><span data-ttu-id="d28e4-106">UWP 应用程序中的语言</span><span class="sxs-lookup"><span data-stu-id="d28e4-106">Languages in UWP Applications</span></span>
<span data-ttu-id="d28e4-107">UWP 应用程序语言并不局限于操作系统中包含的语言。</span><span class="sxs-lookup"><span data-stu-id="d28e4-107">UWP application languages are not limited to the languages included in the OS.</span></span>  <span data-ttu-id="d28e4-108">事实上，不触发 shell UI 或利用语音资源的 IoT 设备可以通过其 UWP 应用程序提供多种不同语言的设备体验，即使基础 Windows 10 IoT 核心操作系统只是以 en-us 默认模式生成的。</span><span class="sxs-lookup"><span data-stu-id="d28e4-108">In fact, an IoT device that does not trigger shell UI or utilize speech resources can provide a device experience in many different languages through its UWP applications even though the underlying Windows 10 IoT Core OS is built simply in the en-US default mode.</span></span> 

<span data-ttu-id="d28e4-109">UWP 应用程序必须提供需要支持的语言的资源。</span><span class="sxs-lookup"><span data-stu-id="d28e4-109">UWP applications must provide the resources for the languages that are required to be supported.</span></span> <span data-ttu-id="d28e4-110">[ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) api 可用于指定与语言相关的首选项。</span><span class="sxs-lookup"><span data-stu-id="d28e4-110">[Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) APIs can be used to specify the language-related preferences.</span></span>

<span data-ttu-id="d28e4-111">请参阅下面的示例应用程序：</span><span class="sxs-lookup"><span data-stu-id="d28e4-111">See the below sample applications:</span></span>

* [<span data-ttu-id="d28e4-112">IoTDefaultApp 示例</span><span class="sxs-lookup"><span data-stu-id="d28e4-112">IoTDefaultApp sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [<span data-ttu-id="d28e4-113">ApplicationResources 示例</span><span class="sxs-lookup"><span data-stu-id="d28e4-113">ApplicationResources sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a><span data-ttu-id="d28e4-114">操作系统中的语言</span><span class="sxs-lookup"><span data-stu-id="d28e4-114">Languages in OS</span></span>

<span data-ttu-id="d28e4-115">Windows 10 IoTCore 工具包现在包含适用于以下语言的语言资源：</span><span class="sxs-lookup"><span data-stu-id="d28e4-115">Windows 10 IoTCore kits now include the language resources for the following languages:</span></span>

> | <span data-ttu-id="d28e4-116">“语言”</span><span class="sxs-lookup"><span data-stu-id="d28e4-116">Language</span></span>  | <span data-ttu-id="d28e4-117">代码</span><span class="sxs-lookup"><span data-stu-id="d28e4-117">Code</span></span> | <span data-ttu-id="d28e4-118">Region</span><span class="sxs-lookup"><span data-stu-id="d28e4-118">Region</span></span> |
> |-------------|-----|-----|
> | <span data-ttu-id="d28e4-119">英语（美国）</span><span class="sxs-lookup"><span data-stu-id="d28e4-119">English (United States)</span></span> | <span data-ttu-id="d28e4-120">zh-CN</span><span class="sxs-lookup"><span data-stu-id="d28e4-120">en-US</span></span> | <span data-ttu-id="d28e4-121">北美</span><span class="sxs-lookup"><span data-stu-id="d28e4-121">North America</span></span> | 
> | <span data-ttu-id="d28e4-122">英语（英国）</span><span class="sxs-lookup"><span data-stu-id="d28e4-122">English (UK)</span></span> | <span data-ttu-id="d28e4-123">en-GB</span><span class="sxs-lookup"><span data-stu-id="d28e4-123">en-GB</span></span> | <span data-ttu-id="d28e4-124">欧洲</span><span class="sxs-lookup"><span data-stu-id="d28e4-124">Europe</span></span> |
> | <span data-ttu-id="d28e4-125">法语(法国)</span><span class="sxs-lookup"><span data-stu-id="d28e4-125">French (France)</span></span> | <span data-ttu-id="d28e4-126">fr-FR</span><span class="sxs-lookup"><span data-stu-id="d28e4-126">fr-FR</span></span> | <span data-ttu-id="d28e4-127">欧洲</span><span class="sxs-lookup"><span data-stu-id="d28e4-127">Europe</span></span> |
> | <span data-ttu-id="d28e4-128">法语（加拿大）</span><span class="sxs-lookup"><span data-stu-id="d28e4-128">French (Canada)</span></span> | <span data-ttu-id="d28e4-129">fr-CA</span><span class="sxs-lookup"><span data-stu-id="d28e4-129">fr-CA</span></span> | <span data-ttu-id="d28e4-130">北美</span><span class="sxs-lookup"><span data-stu-id="d28e4-130">North America</span></span> |
> | <span data-ttu-id="d28e4-131">西班牙语(西班牙)</span><span class="sxs-lookup"><span data-stu-id="d28e4-131">Spanish (Spain)</span></span> | <span data-ttu-id="d28e4-132">es-ES</span><span class="sxs-lookup"><span data-stu-id="d28e4-132">es-ES</span></span> | <span data-ttu-id="d28e4-133">欧洲</span><span class="sxs-lookup"><span data-stu-id="d28e4-133">Europe</span></span> |
> | <span data-ttu-id="d28e4-134">西班牙语（墨西哥）</span><span class="sxs-lookup"><span data-stu-id="d28e4-134">Spanish (Mexico)</span></span> | <span data-ttu-id="d28e4-135">es-MX</span><span class="sxs-lookup"><span data-stu-id="d28e4-135">es-MX</span></span> | <span data-ttu-id="d28e4-136">北美</span><span class="sxs-lookup"><span data-stu-id="d28e4-136">North America</span></span> |
> | <span data-ttu-id="d28e4-137">中文</span><span class="sxs-lookup"><span data-stu-id="d28e4-137">Chinese</span></span> | <span data-ttu-id="d28e4-138">zh-CN</span><span class="sxs-lookup"><span data-stu-id="d28e4-138">zh-CN</span></span> | <span data-ttu-id="d28e4-139">东亚</span><span class="sxs-lookup"><span data-stu-id="d28e4-139">Asia</span></span> | 
> | <span data-ttu-id="d28e4-140">阿拉伯语</span><span class="sxs-lookup"><span data-stu-id="d28e4-140">Arabic</span></span> | <span data-ttu-id="d28e4-141">ar-SA</span><span class="sxs-lookup"><span data-stu-id="d28e4-141">ar-SA</span></span> | <span data-ttu-id="d28e4-142">东亚</span><span class="sxs-lookup"><span data-stu-id="d28e4-142">Asia</span></span> |
> | <span data-ttu-id="d28e4-143">德语</span><span class="sxs-lookup"><span data-stu-id="d28e4-143">German</span></span> | <span data-ttu-id="d28e4-144">de-DE</span><span class="sxs-lookup"><span data-stu-id="d28e4-144">de-DE</span></span> | <span data-ttu-id="d28e4-145">欧洲</span><span class="sxs-lookup"><span data-stu-id="d28e4-145">Europe</span></span> |
> | <span data-ttu-id="d28e4-146">意大利语</span><span class="sxs-lookup"><span data-stu-id="d28e4-146">Italian</span></span> | <span data-ttu-id="d28e4-147">it-IT</span><span class="sxs-lookup"><span data-stu-id="d28e4-147">it-IT</span></span> | <span data-ttu-id="d28e4-148">欧洲</span><span class="sxs-lookup"><span data-stu-id="d28e4-148">Europe</span></span> | 
> | <span data-ttu-id="d28e4-149">日语</span><span class="sxs-lookup"><span data-stu-id="d28e4-149">Japanese</span></span> | <span data-ttu-id="d28e4-150">ja-JP</span><span class="sxs-lookup"><span data-stu-id="d28e4-150">ja-JP</span></span> | <span data-ttu-id="d28e4-151">东亚</span><span class="sxs-lookup"><span data-stu-id="d28e4-151">Asia</span></span> |
> | <span data-ttu-id="d28e4-152">朝鲜语</span><span class="sxs-lookup"><span data-stu-id="d28e4-152">Korean</span></span> | <span data-ttu-id="d28e4-153">ko-KR</span><span class="sxs-lookup"><span data-stu-id="d28e4-153">ko-KR</span></span> | <span data-ttu-id="d28e4-154">东亚</span><span class="sxs-lookup"><span data-stu-id="d28e4-154">Asia</span></span> |
> | <span data-ttu-id="d28e4-155">荷兰语</span><span class="sxs-lookup"><span data-stu-id="d28e4-155">Dutch</span></span> | <span data-ttu-id="d28e4-156">nl-NL</span><span class="sxs-lookup"><span data-stu-id="d28e4-156">nl-NL</span></span> | <span data-ttu-id="d28e4-157">欧洲</span><span class="sxs-lookup"><span data-stu-id="d28e4-157">Europe</span></span> |
> | <span data-ttu-id="d28e4-158">波兰语</span><span class="sxs-lookup"><span data-stu-id="d28e4-158">Polish</span></span> | <span data-ttu-id="d28e4-159">pl-PL</span><span class="sxs-lookup"><span data-stu-id="d28e4-159">pl-PL</span></span> | <span data-ttu-id="d28e4-160">欧洲</span><span class="sxs-lookup"><span data-stu-id="d28e4-160">Europe</span></span> | 
> | <span data-ttu-id="d28e4-161">罗马尼亚语</span><span class="sxs-lookup"><span data-stu-id="d28e4-161">Romanian</span></span> | <span data-ttu-id="d28e4-162">ro-RO</span><span class="sxs-lookup"><span data-stu-id="d28e4-162">ro-RO</span></span> | <span data-ttu-id="d28e4-163">欧洲</span><span class="sxs-lookup"><span data-stu-id="d28e4-163">Europe</span></span> |
> | <span data-ttu-id="d28e4-164">俄语</span><span class="sxs-lookup"><span data-stu-id="d28e4-164">Russian</span></span> | <span data-ttu-id="d28e4-165">ru-RU</span><span class="sxs-lookup"><span data-stu-id="d28e4-165">ru-RU</span></span> | <span data-ttu-id="d28e4-166">欧洲</span><span class="sxs-lookup"><span data-stu-id="d28e4-166">Europe</span></span> |
> | <span data-ttu-id="d28e4-167">希腊语</span><span class="sxs-lookup"><span data-stu-id="d28e4-167">Greek</span></span> | <span data-ttu-id="d28e4-168">el-GR</span><span class="sxs-lookup"><span data-stu-id="d28e4-168">el-GR</span></span> | <span data-ttu-id="d28e4-169">欧洲</span><span class="sxs-lookup"><span data-stu-id="d28e4-169">Europe</span></span> |
> | <span data-ttu-id="d28e4-170">葡萄牙语（巴西）</span><span class="sxs-lookup"><span data-stu-id="d28e4-170">Portugese (Brazil)</span></span> | <span data-ttu-id="d28e4-171">pt-BR</span><span class="sxs-lookup"><span data-stu-id="d28e4-171">pt-BR</span></span> | <span data-ttu-id="d28e4-172">南美/欧洲</span><span class="sxs-lookup"><span data-stu-id="d28e4-172">South America/Europe</span></span> |
> | <span data-ttu-id="d28e4-173">Portuese （葡萄牙）</span><span class="sxs-lookup"><span data-stu-id="d28e4-173">Portuese (Portugal)</span></span> | <span data-ttu-id="d28e4-174">pt-PT</span><span class="sxs-lookup"><span data-stu-id="d28e4-174">pt-PT</span></span> | <span data-ttu-id="d28e4-175">南美/欧洲</span><span class="sxs-lookup"><span data-stu-id="d28e4-175">South America/Europe</span></span> |

<span data-ttu-id="d28e4-176">这些语言资源包含 UI 字符串、语音语言和语音（语音合成）。</span><span class="sxs-lookup"><span data-stu-id="d28e4-176">These language resources contain UI strings, speech language and voices (speech synthesis).</span></span> <span data-ttu-id="d28e4-177">Windows IoT 映像可以用一个或多个这些资源生成，并且必须在映像时间内指定，以后不能修改。</span><span class="sxs-lookup"><span data-stu-id="d28e4-177">Windows IoT images can be built with one or more of these resources and they must be specified during the image time and cannot be modified later.</span></span> <span data-ttu-id="d28e4-178">请注意，与语音和语音资源无关的 UI 语言相关资源。</span><span class="sxs-lookup"><span data-stu-id="d28e4-178">Note that UI language related resources are independent than speech language and voice resources.</span></span>

### <a name="specifying-ui-and-speech-resources"></a><span data-ttu-id="d28e4-179">指定 UI 和语音资源</span><span class="sxs-lookup"><span data-stu-id="d28e4-179">Specifying UI and Speech resources</span></span> 
<span data-ttu-id="d28e4-180">在 OEM 输入 xml 文件中，指定了所需的 UI 和语音语言，如下所示</span><span class="sxs-lookup"><span data-stu-id="d28e4-180">In the OEM Input xml file, the required UI and speech languages are specified as shown below</span></span>

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


### <a name="specifying-speech-data-resources"></a><span data-ttu-id="d28e4-181">指定语音数据资源</span><span class="sxs-lookup"><span data-stu-id="d28e4-181">Specifying Speech Data resources</span></span>
<span data-ttu-id="d28e4-182">在 OEM 输入 xml 文件中，按如下所示指定所需的语音数据资源。</span><span class="sxs-lookup"><span data-stu-id="d28e4-182">In the OEM Input xml file, the required speech data resources are specified as shown below,</span></span>

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
> <span data-ttu-id="d28e4-183">默认情况下，en-us 语音数据包括在映像中。</span><span class="sxs-lookup"><span data-stu-id="d28e4-183">By default, en-US speech data is included in the image.</span></span>

### <a name="samples"></a><span data-ttu-id="d28e4-184">示例</span><span class="sxs-lookup"><span data-stu-id="d28e4-184">Samples</span></span>
* <span data-ttu-id="d28e4-185">有关多语言支持，请参阅[MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample)</span><span class="sxs-lookup"><span data-stu-id="d28e4-185">See [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) for multiple languages support</span></span>
* <span data-ttu-id="d28e4-186">请参阅[SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) for fr-fr，并以 en-us 作为备用语言。</span><span class="sxs-lookup"><span data-stu-id="d28e4-186">See [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) for fr-FR language with en-US as fallback language.</span></span>
    * <span data-ttu-id="d28e4-187">请注意，当更改启动 UI 语言时，还会以启动 UI 语言转换 `administrator` 帐户名称。</span><span class="sxs-lookup"><span data-stu-id="d28e4-187">Note that when the boot UI language is changed, the `administrator` account name is also translated in the boot UI language.</span></span> <span data-ttu-id="d28e4-188">因此，在 fr-fr 中 `administrateur`。</span><span class="sxs-lookup"><span data-stu-id="d28e4-188">So, in fr-FR it is `administrateur`.</span></span> <span data-ttu-id="d28e4-189">请参阅[OEMCustomization。](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span><span class="sxs-lookup"><span data-stu-id="d28e4-189">See [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span></span>

## <a name="changing-user-preferences-language-region-speech-and-voice"></a><span data-ttu-id="d28e4-190">更改用户首选项（语言、区域、语音和语音）</span><span class="sxs-lookup"><span data-stu-id="d28e4-190">Changing user preferences (language, region, speech and voice)</span></span>

<span data-ttu-id="d28e4-191">UWP 应用程序可以使用 WinRT Api 来设置默认情况下应使用的区域、首选的 UI 语言列表、语音语言和语音。</span><span class="sxs-lookup"><span data-stu-id="d28e4-191">UWP application can use WinRT APIs to set the region, preferred UI language list, speech language and voice that should be by default used.</span></span> <span data-ttu-id="d28e4-192">在首选的 UI 语言列表集之后，UWP 应用程序将尝试加载相应的资源（除非应用程序以编程方式禁止）。</span><span class="sxs-lookup"><span data-stu-id="d28e4-192">Once preferred UI language list set, UWP application will try to load the corresponding resources (unless application programmatically prevents that).</span></span>
 
<span data-ttu-id="d28e4-193">如果应用程序没有相应的资源，则会加载回退资源。</span><span class="sxs-lookup"><span data-stu-id="d28e4-193">If the application doesn’t have the corresponding resources, then fallback resources will be loaded.</span></span> <span data-ttu-id="d28e4-194">同样，如果首选语言的操作系统资源不是 Windows IoT 映像的一部分，则 Windows IoT 将使用它的回退，这可能是英语（en-us）。</span><span class="sxs-lookup"><span data-stu-id="d28e4-194">Similarly, if the OS resources for the preferred languages aren’t part of the Windows IoT image, Windows IoT will use its fallback ones likely English (en-US).</span></span>

* <span data-ttu-id="d28e4-195">使用[GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)中的 `TrySetHomeGeographicRegion` 设置区域</span><span class="sxs-lookup"><span data-stu-id="d28e4-195">Set region using `TrySetHomeGeographicRegion` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="d28e4-196">使用[GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)中的 `TrySetLanguages` 设置 UI 语言</span><span class="sxs-lookup"><span data-stu-id="d28e4-196">Set UI language using `TrySetLanguages` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="d28e4-197">使用 SpeechRecognition 中的 `TrySetSystemSpeechLanguageAsync` 设置语音语言。 [SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span><span class="sxs-lookup"><span data-stu-id="d28e4-197">Set speech language using `TrySetSystemSpeechLanguageAsync` in [Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span></span>
* <span data-ttu-id="d28e4-198">使用 SpeechSynthesis 中的 `TrySetDefaultVoiceAsync` 设置语音。 [SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span><span class="sxs-lookup"><span data-stu-id="d28e4-198">Set voice using `TrySetDefaultVoiceAsync` in [Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span></span>

> [!NOTE]
> <span data-ttu-id="d28e4-199">为了正常工作，Cortana 要求区域、UI 语言和语音语言保持一致，例如：区域 FR、UI 和语音语言 fr-fr 或地区 ES、UI 和语音语言 es。</span><span class="sxs-lookup"><span data-stu-id="d28e4-199">For proper functioning, Cortana requires the region, UI language and speech language to be consistent, e.g.: region FR, UI and speech languages fr-FR or region ES, UI and speech languages es-ES.</span></span> <span data-ttu-id="d28e4-200">Cortana 使用自己的语音，UWP 应用程序无法更改它。</span><span class="sxs-lookup"><span data-stu-id="d28e4-200">Cortana uses its own voice, UWP application cannot change it.</span></span>

## <a name="iotsettingsexe"></a><span data-ttu-id="d28e4-201">IoTSettings</span><span class="sxs-lookup"><span data-stu-id="d28e4-201">IoTSettings.exe</span></span>

<span data-ttu-id="d28e4-202">若要了解有关更改区域和用户或语音语言设置以构建启用 Cortana 的产品的详细信息，请阅读我们的[命令行 Utils](../manage-your-device/CommandLineUtils.md)文档。</span><span class="sxs-lookup"><span data-stu-id="d28e4-202">To learn more about changing settings for region and user or speech language to build Cortana enabled products, please read our [Command Line Utils](../manage-your-device/CommandLineUtils.md) documentation.</span></span>
