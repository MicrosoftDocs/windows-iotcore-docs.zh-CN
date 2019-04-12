---
title: Windows 10 IoT 核心版的语言支持
author: msalehmsft
ms.author: msaleh
ms.date: 09/12/17
ms.topic: article
description: 了解如何在 UWP 应用程序和 IoT Core 上的操作系统中的多语言支持。
keywords: windows iot、 语言、 UWP、 OS 的应用类型
ms.openlocfilehash: 211ed2ee8350d8c92d6f959f8d9e7b5d6f567af7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510640"
---
# <a name="language-support"></a><span data-ttu-id="a5187-104">语言支持</span><span class="sxs-lookup"><span data-stu-id="a5187-104">Language Support</span></span>

<span data-ttu-id="a5187-105">可以在两个级别、 应用程序级别和 OS 级别，具体取决于可在映像上的语言资源启用语言支持。</span><span class="sxs-lookup"><span data-stu-id="a5187-105">Language support can be enabled at two levels, Application level and OS level, depending on the language resources made available on the image.</span></span>

## <a name="languages-in-uwp-applications"></a><span data-ttu-id="a5187-106">在 UWP 应用程序中的语言</span><span class="sxs-lookup"><span data-stu-id="a5187-106">Languages in UWP Applications</span></span>
<span data-ttu-id="a5187-107">UWP 应用程序语言并不局限于操作系统中包含的语言。</span><span class="sxs-lookup"><span data-stu-id="a5187-107">UWP application languages are not limited to the languages included in the OS.</span></span>  <span data-ttu-id="a5187-108">事实上，不会触发命令行程序 UI 或利用语音资源的 IoT 设备可以提供通过其 UWP 应用程序的许多不同语言中的设备体验，即使只是在 EN-US 默认模式下构建基础的 Windows 10 IoT Core OS。</span><span class="sxs-lookup"><span data-stu-id="a5187-108">In fact, an IoT device that does not trigger shell UI or utilize speech resources can provide a device experience in many different languages through its UWP applications even though the underlying Windows 10 IoT Core OS is built simply in the en-US default mode.</span></span> 

<span data-ttu-id="a5187-109">UWP 应用程序必须提供所需受支持的语言资源。</span><span class="sxs-lookup"><span data-stu-id="a5187-109">UWP applications must provide the resources for the languages that are required to be supported.</span></span> <span data-ttu-id="a5187-110">[Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) Api 可用于指定与语言相关首选项。</span><span class="sxs-lookup"><span data-stu-id="a5187-110">[Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) APIs can be used to specify the language-related preferences.</span></span>

<span data-ttu-id="a5187-111">请参阅下面的示例应用程序：</span><span class="sxs-lookup"><span data-stu-id="a5187-111">See the below sample applications:</span></span>

* [<span data-ttu-id="a5187-112">IoTDefaultApp 示例</span><span class="sxs-lookup"><span data-stu-id="a5187-112">IoTDefaultApp sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [<span data-ttu-id="a5187-113">应用程序资源使用示例</span><span class="sxs-lookup"><span data-stu-id="a5187-113">ApplicationResources sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a><span data-ttu-id="a5187-114">在 OS 中的语言</span><span class="sxs-lookup"><span data-stu-id="a5187-114">Languages in OS</span></span>

<span data-ttu-id="a5187-115">Windows 10 IoTCore 工具包现在包括了以下语言版本的语言资源：</span><span class="sxs-lookup"><span data-stu-id="a5187-115">Windows 10 IoTCore kits now include the language resources for the following languages:</span></span>

> | <span data-ttu-id="a5187-116">语言</span><span class="sxs-lookup"><span data-stu-id="a5187-116">Language</span></span>  | <span data-ttu-id="a5187-117">代码</span><span class="sxs-lookup"><span data-stu-id="a5187-117">Code</span></span> | <span data-ttu-id="a5187-118">Region</span><span class="sxs-lookup"><span data-stu-id="a5187-118">Region</span></span> |
> |-------------|-----|-----|
> | <span data-ttu-id="a5187-119">英语(美国)</span><span class="sxs-lookup"><span data-stu-id="a5187-119">English (United States)</span></span> | <span data-ttu-id="a5187-120">en-US</span><span class="sxs-lookup"><span data-stu-id="a5187-120">en-US</span></span> | <span data-ttu-id="a5187-121">北美</span><span class="sxs-lookup"><span data-stu-id="a5187-121">North America</span></span> | 
> | <span data-ttu-id="a5187-122">英语 （英国）</span><span class="sxs-lookup"><span data-stu-id="a5187-122">English (UK)</span></span> | <span data-ttu-id="a5187-123">en-GB</span><span class="sxs-lookup"><span data-stu-id="a5187-123">en-GB</span></span> | <span data-ttu-id="a5187-124">欧洲</span><span class="sxs-lookup"><span data-stu-id="a5187-124">Europe</span></span> |
> | <span data-ttu-id="a5187-125">法语(法国)</span><span class="sxs-lookup"><span data-stu-id="a5187-125">French (France)</span></span> | <span data-ttu-id="a5187-126">fr-FR</span><span class="sxs-lookup"><span data-stu-id="a5187-126">fr-FR</span></span> | <span data-ttu-id="a5187-127">欧洲</span><span class="sxs-lookup"><span data-stu-id="a5187-127">Europe</span></span> |
> | <span data-ttu-id="a5187-128">法语(加拿大)</span><span class="sxs-lookup"><span data-stu-id="a5187-128">French (Canada)</span></span> | <span data-ttu-id="a5187-129">fr-CA</span><span class="sxs-lookup"><span data-stu-id="a5187-129">fr-CA</span></span> | <span data-ttu-id="a5187-130">北美</span><span class="sxs-lookup"><span data-stu-id="a5187-130">North America</span></span> |
> | <span data-ttu-id="a5187-131">西班牙语(西班牙)</span><span class="sxs-lookup"><span data-stu-id="a5187-131">Spanish (Spain)</span></span> | <span data-ttu-id="a5187-132">es-ES</span><span class="sxs-lookup"><span data-stu-id="a5187-132">es-ES</span></span> | <span data-ttu-id="a5187-133">欧洲</span><span class="sxs-lookup"><span data-stu-id="a5187-133">Europe</span></span> |
> | <span data-ttu-id="a5187-134">西班牙语(墨西哥)</span><span class="sxs-lookup"><span data-stu-id="a5187-134">Spanish (Mexico)</span></span> | <span data-ttu-id="a5187-135">es-MX</span><span class="sxs-lookup"><span data-stu-id="a5187-135">es-MX</span></span> | <span data-ttu-id="a5187-136">北美</span><span class="sxs-lookup"><span data-stu-id="a5187-136">North America</span></span> |
> | <span data-ttu-id="a5187-137">中文</span><span class="sxs-lookup"><span data-stu-id="a5187-137">Chinese</span></span> | <span data-ttu-id="a5187-138">zh-CN</span><span class="sxs-lookup"><span data-stu-id="a5187-138">zh-CN</span></span> | <span data-ttu-id="a5187-139">亚洲</span><span class="sxs-lookup"><span data-stu-id="a5187-139">Asia</span></span> | 
> | <span data-ttu-id="a5187-140">阿拉伯语</span><span class="sxs-lookup"><span data-stu-id="a5187-140">Arabic</span></span> | <span data-ttu-id="a5187-141">ar-SA</span><span class="sxs-lookup"><span data-stu-id="a5187-141">ar-SA</span></span> | <span data-ttu-id="a5187-142">亚洲</span><span class="sxs-lookup"><span data-stu-id="a5187-142">Asia</span></span> |
> | <span data-ttu-id="a5187-143">德语</span><span class="sxs-lookup"><span data-stu-id="a5187-143">German</span></span> | <span data-ttu-id="a5187-144">de-DE</span><span class="sxs-lookup"><span data-stu-id="a5187-144">de-DE</span></span> | <span data-ttu-id="a5187-145">欧洲</span><span class="sxs-lookup"><span data-stu-id="a5187-145">Europe</span></span> |
> | <span data-ttu-id="a5187-146">意大利语</span><span class="sxs-lookup"><span data-stu-id="a5187-146">Italian</span></span> | <span data-ttu-id="a5187-147">it-IT</span><span class="sxs-lookup"><span data-stu-id="a5187-147">it-IT</span></span> | <span data-ttu-id="a5187-148">欧洲</span><span class="sxs-lookup"><span data-stu-id="a5187-148">Europe</span></span> | 
> | <span data-ttu-id="a5187-149">日语</span><span class="sxs-lookup"><span data-stu-id="a5187-149">Japanese</span></span> | <span data-ttu-id="a5187-150">ja-JP</span><span class="sxs-lookup"><span data-stu-id="a5187-150">ja-JP</span></span> | <span data-ttu-id="a5187-151">亚洲</span><span class="sxs-lookup"><span data-stu-id="a5187-151">Asia</span></span> |
> | <span data-ttu-id="a5187-152">朝鲜语</span><span class="sxs-lookup"><span data-stu-id="a5187-152">Korean</span></span> | <span data-ttu-id="a5187-153">ko-KR</span><span class="sxs-lookup"><span data-stu-id="a5187-153">ko-KR</span></span> | <span data-ttu-id="a5187-154">亚洲</span><span class="sxs-lookup"><span data-stu-id="a5187-154">Asia</span></span> |
> | <span data-ttu-id="a5187-155">荷兰语</span><span class="sxs-lookup"><span data-stu-id="a5187-155">Dutch</span></span> | <span data-ttu-id="a5187-156">nl-NL</span><span class="sxs-lookup"><span data-stu-id="a5187-156">nl-NL</span></span> | <span data-ttu-id="a5187-157">欧洲</span><span class="sxs-lookup"><span data-stu-id="a5187-157">Europe</span></span> |
> | <span data-ttu-id="a5187-158">波兰语</span><span class="sxs-lookup"><span data-stu-id="a5187-158">Polish</span></span> | <span data-ttu-id="a5187-159">pl-PL</span><span class="sxs-lookup"><span data-stu-id="a5187-159">pl-PL</span></span> | <span data-ttu-id="a5187-160">欧洲</span><span class="sxs-lookup"><span data-stu-id="a5187-160">Europe</span></span> | 
> | <span data-ttu-id="a5187-161">罗马尼亚语</span><span class="sxs-lookup"><span data-stu-id="a5187-161">Romanian</span></span> | <span data-ttu-id="a5187-162">ro-RO</span><span class="sxs-lookup"><span data-stu-id="a5187-162">ro-RO</span></span> | <span data-ttu-id="a5187-163">欧洲</span><span class="sxs-lookup"><span data-stu-id="a5187-163">Europe</span></span> |
> | <span data-ttu-id="a5187-164">俄语</span><span class="sxs-lookup"><span data-stu-id="a5187-164">Russian</span></span> | <span data-ttu-id="a5187-165">ro-RU</span><span class="sxs-lookup"><span data-stu-id="a5187-165">ro-RU</span></span> | <span data-ttu-id="a5187-166">欧洲</span><span class="sxs-lookup"><span data-stu-id="a5187-166">Europe</span></span> |
> | <span data-ttu-id="a5187-167">希腊语</span><span class="sxs-lookup"><span data-stu-id="a5187-167">Greek</span></span> | <span data-ttu-id="a5187-168">el-GR</span><span class="sxs-lookup"><span data-stu-id="a5187-168">el-GR</span></span> | <span data-ttu-id="a5187-169">欧洲</span><span class="sxs-lookup"><span data-stu-id="a5187-169">Europe</span></span> |
> | <span data-ttu-id="a5187-170">葡萄牙语 （巴西）</span><span class="sxs-lookup"><span data-stu-id="a5187-170">Portugese (Brazil)</span></span> | <span data-ttu-id="a5187-171">pt-BR</span><span class="sxs-lookup"><span data-stu-id="a5187-171">pt-BR</span></span> | <span data-ttu-id="a5187-172">南美洲的众多/欧洲</span><span class="sxs-lookup"><span data-stu-id="a5187-172">South America/Europe</span></span> |
> | <span data-ttu-id="a5187-173">Portuese （葡萄牙）</span><span class="sxs-lookup"><span data-stu-id="a5187-173">Portuese (Portugal)</span></span> | <span data-ttu-id="a5187-174">pt-PR</span><span class="sxs-lookup"><span data-stu-id="a5187-174">pt-PR</span></span> | <span data-ttu-id="a5187-175">南美洲的众多/欧洲</span><span class="sxs-lookup"><span data-stu-id="a5187-175">South America/Europe</span></span> |

<span data-ttu-id="a5187-176">这些语言资源包含 UI 字符串、 语音语言和语音 （语音合成）。</span><span class="sxs-lookup"><span data-stu-id="a5187-176">These language resources contain UI strings, speech language and voices (speech synthesis).</span></span> <span data-ttu-id="a5187-177">可以与一个或多个这些资源生成 Windows IoT 映像且必须在映像期间指定和更高版本不能修改它们。</span><span class="sxs-lookup"><span data-stu-id="a5187-177">Windows IoT images can be built with one or more of these resources and they must be specified during the image time and cannot be modified later.</span></span> <span data-ttu-id="a5187-178">请注意，UI 语言相关的资源是独立于语音语言和语音的资源。</span><span class="sxs-lookup"><span data-stu-id="a5187-178">Note that UI language related resources are independent than speech language and voice resources.</span></span>

### <a name="specifying-ui-and-speech-resources"></a><span data-ttu-id="a5187-179">指定的 UI 和语音资源</span><span class="sxs-lookup"><span data-stu-id="a5187-179">Specifying UI and Speech resources</span></span> 
<span data-ttu-id="a5187-180">在 OEM 输入 xml 文件中，必需的 UI 和语音语言指定，如下所示</span><span class="sxs-lookup"><span data-stu-id="a5187-180">In the OEM Input xml file, the required UI and speech languages are specified as shown below</span></span>

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


### <a name="specifying-speech-data-resources"></a><span data-ttu-id="a5187-181">指定语音数据资源</span><span class="sxs-lookup"><span data-stu-id="a5187-181">Specifying Speech Data resources</span></span>
<span data-ttu-id="a5187-182">在 OEM 输入 xml 文件中，将指定所需的语音数据资源，如下所示，</span><span class="sxs-lookup"><span data-stu-id="a5187-182">In the OEM Input xml file, the required speech data resources are specified as shown below,</span></span>

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
> <span data-ttu-id="a5187-183">默认情况下，EN-US 语音数据会包含在映像中。</span><span class="sxs-lookup"><span data-stu-id="a5187-183">By default, en-US speech data is included in the image.</span></span>

### <a name="samples"></a><span data-ttu-id="a5187-184">示例</span><span class="sxs-lookup"><span data-stu-id="a5187-184">Samples</span></span>
* <span data-ttu-id="a5187-185">请参阅[MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample)多种语言支持</span><span class="sxs-lookup"><span data-stu-id="a5187-185">See [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) for multiple languages support</span></span>
* <span data-ttu-id="a5187-186">请参阅[SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) FR-FR 的与 EN-US 作为回退语言的语言。</span><span class="sxs-lookup"><span data-stu-id="a5187-186">See [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) for fr-FR language with en-US as fallback language.</span></span>
    * <span data-ttu-id="a5187-187">请注意，当更改启动 UI 语言，`administrator`帐户名称还转换中启动 UI 语言。</span><span class="sxs-lookup"><span data-stu-id="a5187-187">Note that when the boot UI language is changed, the `administrator` account name is also translated in the boot UI language.</span></span> <span data-ttu-id="a5187-188">因此，在-FR 它是`administrateur`。</span><span class="sxs-lookup"><span data-stu-id="a5187-188">So, in fr-FR it is `administrateur`.</span></span> <span data-ttu-id="a5187-189">请参阅[OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span><span class="sxs-lookup"><span data-stu-id="a5187-189">See [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span></span>

## <a name="changing-user-preferences-language-region-speech-and-voice"></a><span data-ttu-id="a5187-190">更改用户首选项 （语言、 区域、 语音和语音）</span><span class="sxs-lookup"><span data-stu-id="a5187-190">Changing user preferences (language, region, speech and voice)</span></span>

<span data-ttu-id="a5187-191">UWP 应用程序可以使用 WinRT Api 来设置区域、 首选的 UI 语言列表中，语音语言和应为默认情况下使用的语音。</span><span class="sxs-lookup"><span data-stu-id="a5187-191">UWP application can use WinRT APIs to set the region, preferred UI language list, speech language and voice that should be by default used.</span></span> <span data-ttu-id="a5187-192">一次首选的 UI 语言列表设置，UWP 应用程序将尝试加载相应的资源，（除非应用程序以编程方式可防止发生的）。</span><span class="sxs-lookup"><span data-stu-id="a5187-192">Once preferred UI language list set, UWP application will try to load the corresponding resources (unless application programmatically prevents that).</span></span>
 
<span data-ttu-id="a5187-193">如果应用程序不具有相应的资源，则将加载回退资源。</span><span class="sxs-lookup"><span data-stu-id="a5187-193">If the application doesn’t have the corresponding resources, then fallback resources will be loaded.</span></span> <span data-ttu-id="a5187-194">同样，如果首选语言的操作系统资源不是 Windows IoT 映像的一部分，Windows IoT 将使用其回退的可能英语 (EN-US)。</span><span class="sxs-lookup"><span data-stu-id="a5187-194">Similarly, if the OS resources for the preferred languages aren’t part of the Windows IoT image, Windows IoT will use its fallback ones likely English (en-US).</span></span>

* <span data-ttu-id="a5187-195">使用区域设置`TrySetHomeGeographicRegion`在[Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span><span class="sxs-lookup"><span data-stu-id="a5187-195">Set region using `TrySetHomeGeographicRegion` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="a5187-196">设置 UI 语言时，使用`TrySetLanguages`在[Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span><span class="sxs-lookup"><span data-stu-id="a5187-196">Set UI language using `TrySetLanguages` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="a5187-197">使用集语音语言`TrySetSystemSpeechLanguageAsync`在[Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span><span class="sxs-lookup"><span data-stu-id="a5187-197">Set speech language using `TrySetSystemSpeechLanguageAsync` in [Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span></span>
* <span data-ttu-id="a5187-198">设置使用语音`TrySetDefaultVoiceAsync`在[Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span><span class="sxs-lookup"><span data-stu-id="a5187-198">Set voice using `TrySetDefaultVoiceAsync` in [Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span></span>

> [!NOTE]
> <span data-ttu-id="a5187-199">对于正常运行，Cortana 需要区域、 UI 语言和语音语言，使其保持一致，例如： 区域 FR、 UI 和语音语言 FR-FR 或区域 ES、 UI 和语音语言 es 的多少号。</span><span class="sxs-lookup"><span data-stu-id="a5187-199">For proper functioning, Cortana requires the region, UI language and speech language to be consistent, e.g.: region FR, UI and speech languages fr-FR or region ES, UI and speech languages es-ES.</span></span> <span data-ttu-id="a5187-200">Cortana 使用其自己的语音，UWP 应用程序不能更改它。</span><span class="sxs-lookup"><span data-stu-id="a5187-200">Cortana uses its own voice, UWP application cannot change it.</span></span>

## <a name="iotsettingsexe"></a><span data-ttu-id="a5187-201">IoTSettings.exe</span><span class="sxs-lookup"><span data-stu-id="a5187-201">IoTSettings.exe</span></span>

<span data-ttu-id="a5187-202">若要了解有关更改的区域以及用户或语音语言来构建 Cortana 启用产品的设置的详细信息，请阅读我们[命令行实用工具](../manage-your-device/CommandLineUtils.md)文档。</span><span class="sxs-lookup"><span data-stu-id="a5187-202">To learn more about changing settings for region and user or speech language to build Cortana enabled products, please read our [Command Line Utils](../manage-your-device/CommandLineUtils.md) documentation.</span></span>
