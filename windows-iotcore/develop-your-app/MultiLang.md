---
title: Windows 10 IoT 核心语言支持
author: msalehmsft
ms.author: msaleh
ms.date: 09/12/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解 UWP Core 上的 UWP 应用程序和 OS 中的多语言支持。
keywords: windows iot，语言，应用类型，UWP，OS
ms.openlocfilehash: 7559bcade5a9877d806bbaec090e02f4b9a160c0
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656123"
---
# <a name="language-support"></a>语言支持

可以在两个级别上启用语言支持：应用程序级别和操作系统级别，具体取决于映像中提供的语言资源。

## <a name="languages-in-uwp-applications"></a>UWP 应用程序中的语言
UWP 应用程序语言并不局限于操作系统中包含的语言。  事实上，不触发 shell UI 或利用语音资源的 IoT 设备可以通过其 UWP 应用程序提供多种不同语言的设备体验，即使基础 Windows 10 IoT 核心操作系统只是以 en-us 默认模式生成的。 

UWP 应用程序必须提供需要支持的语言的资源。 [ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) api 可用于指定与语言相关的首选项。

请参阅下面的示例应用程序：

* [IoTDefaultApp 示例](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [ApplicationResources 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a>操作系统中的语言

Windows 10 IoTCore 工具包现在包含适用于以下语言的语言资源：

> | 语言  | 代码 | 区域 |
> |-------------|-----|-----|
> | 英语（美国） | zh-CN | 北美 | 
> | 英语(英国) | en-GB | 欧洲 |
> | 法语（法国） | fr-FR | 欧洲 |
> | 法语（加拿大） | fr-CA | 北美 |
> | 西班牙语(西班牙) | es-ES | 欧洲 |
> | 西班牙语(墨西哥) | es-MX | 北美 |
> | 中文 | zh-CN | 亚洲 | 
> | 阿拉伯语 | ar-SA | 亚洲 |
> | 德语 | de-DE | 欧洲 |
> | 意大利语 | it-IT | 欧洲 | 
> | 日语 | ja-JP | 亚洲 |
> | 韩语 | ko-KR | 亚洲 |
> | 荷兰语 | nl-NL | 欧洲 |
> | 波兰语 | pl-PL | 欧洲 | 
> | 罗马尼亚语 | ro-RO | 欧洲 |
> | 俄语 | ru-RU | 欧洲 |
> | 希腊语 | el-GR | 欧洲 |
> | 葡萄牙语 (巴西)  | pt-BR | 南美/欧洲 |
> | Portuese (葡萄牙)  | pt-PT | 南美/欧洲 |

这些语言资源包含 UI 字符串、语音语言和语音 (语音合成) 。 Windows IoT 映像可以用一个或多个这些资源生成，并且必须在映像时间内指定，以后不能修改。 请注意，与 UI 语言相关的资源与语音语言和语音资源无关。

### <a name="specifying-ui-and-speech-resources"></a>指定 UI 和语音资源 
在 OEM 输入 xml 文件中，指定了所需的 UI 和语音语言，如下所示

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


### <a name="specifying-speech-data-resources"></a>指定语音数据资源
在 OEM 输入 xml 文件中，按如下所示指定所需的语音数据资源。

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
> 默认情况下，en-us 语音数据包括在映像中。

### <a name="samples"></a>示例
* 有关多语言支持，请参阅[MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample)
* 请参阅 [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) for fr-fr，并以 en-us 作为备用语言。
    * 请注意，当更改启动 UI 语言时， `administrator` 还会用启动 ui 语言转换帐户名称。 因此，在 fr-fr 中，它是 `administrateur` 。 请参阅 [OEMCustomization。](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)

## <a name="changing-user-preferences-language-region-speech-and-voice"></a>更改用户首选项 (语言、区域、语音和语音) 

UWP 应用程序可以使用 WinRT Api 来设置默认情况下应使用的区域、首选的 UI 语言列表、语音语言和语音。 在首选的 UI 语言列表集之后，UWP 应用程序将尝试加载相应的资源， (除非应用程序以编程方式阻止了) 。
 
如果应用程序没有相应的资源，则会加载回退资源。 同样，如果首选语言的 OS 资源不是 Windows IoT 映像的一部分，则 Windows IoT 将使用它的回退 (en-us) 。

* 使用 `TrySetHomeGeographicRegion`Windows.System 中的设置区域 [ 。UserProfile. GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)
* 使用 `TrySetLanguages`Windows.System 中的设置 UI 语言 [ 。UserProfile. GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)
* 在 SpeechRecognition 中使用设置语音语言。 `TrySetSystemSpeechLanguageAsync` [SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)
* `TrySetDefaultVoiceAsync`在[SpeechSynthesis. SpeechSynthesizer](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer)中使用设置语音。

> [!NOTE]
> 为了正常工作，Cortana 要求区域、UI 语言和语音语言保持一致，例如：区域 FR、UI 和语音语言 fr-fr 或地区 ES、UI 和语音语言 es。 Cortana 使用自己的语音，UWP 应用程序无法更改它。

## <a name="iotsettingsexe"></a>IoTSettings.exe

若要了解有关更改区域和用户或语音语言设置以构建启用 Cortana 的产品的详细信息，请阅读我们的 [命令行 Utils](../manage-your-device/CommandLineUtils.md) 文档。
