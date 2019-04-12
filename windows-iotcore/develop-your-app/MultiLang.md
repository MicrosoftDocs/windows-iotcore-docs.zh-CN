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
# <a name="language-support"></a>语言支持

可以在两个级别、 应用程序级别和 OS 级别，具体取决于可在映像上的语言资源启用语言支持。

## <a name="languages-in-uwp-applications"></a>在 UWP 应用程序中的语言
UWP 应用程序语言并不局限于操作系统中包含的语言。  事实上，不会触发命令行程序 UI 或利用语音资源的 IoT 设备可以提供通过其 UWP 应用程序的许多不同语言中的设备体验，即使只是在 EN-US 默认模式下构建基础的 Windows 10 IoT Core OS。 

UWP 应用程序必须提供所需受支持的语言资源。 [Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) Api 可用于指定与语言相关首选项。

请参阅下面的示例应用程序：

* [IoTDefaultApp 示例](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [应用程序资源使用示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a>在 OS 中的语言

Windows 10 IoTCore 工具包现在包括了以下语言版本的语言资源：

> | 语言  | 代码 | Region |
> |-------------|-----|-----|
> | 英语(美国) | en-US | 北美 | 
> | 英语 （英国） | en-GB | 欧洲 |
> | 法语(法国) | fr-FR | 欧洲 |
> | 法语(加拿大) | fr-CA | 北美 |
> | 西班牙语(西班牙) | es-ES | 欧洲 |
> | 西班牙语(墨西哥) | es-MX | 北美 |
> | 中文 | zh-CN | 亚洲 | 
> | 阿拉伯语 | ar-SA | 亚洲 |
> | 德语 | de-DE | 欧洲 |
> | 意大利语 | it-IT | 欧洲 | 
> | 日语 | ja-JP | 亚洲 |
> | 朝鲜语 | ko-KR | 亚洲 |
> | 荷兰语 | nl-NL | 欧洲 |
> | 波兰语 | pl-PL | 欧洲 | 
> | 罗马尼亚语 | ro-RO | 欧洲 |
> | 俄语 | ro-RU | 欧洲 |
> | 希腊语 | el-GR | 欧洲 |
> | 葡萄牙语 （巴西） | pt-BR | 南美洲的众多/欧洲 |
> | Portuese （葡萄牙） | pt-PR | 南美洲的众多/欧洲 |

这些语言资源包含 UI 字符串、 语音语言和语音 （语音合成）。 可以与一个或多个这些资源生成 Windows IoT 映像且必须在映像期间指定和更高版本不能修改它们。 请注意，UI 语言相关的资源是独立于语音语言和语音的资源。

### <a name="specifying-ui-and-speech-resources"></a>指定的 UI 和语音资源 
在 OEM 输入 xml 文件中，必需的 UI 和语音语言指定，如下所示

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
在 OEM 输入 xml 文件中，将指定所需的语音数据资源，如下所示，

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
> 默认情况下，EN-US 语音数据会包含在映像中。

### <a name="samples"></a>示例
* 请参阅[MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample)多种语言支持
* 请参阅[SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) FR-FR 的与 EN-US 作为回退语言的语言。
    * 请注意，当更改启动 UI 语言，`administrator`帐户名称还转换中启动 UI 语言。 因此，在-FR 它是`administrateur`。 请参阅[OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)

## <a name="changing-user-preferences-language-region-speech-and-voice"></a>更改用户首选项 （语言、 区域、 语音和语音）

UWP 应用程序可以使用 WinRT Api 来设置区域、 首选的 UI 语言列表中，语音语言和应为默认情况下使用的语音。 一次首选的 UI 语言列表设置，UWP 应用程序将尝试加载相应的资源，（除非应用程序以编程方式可防止发生的）。
 
如果应用程序不具有相应的资源，则将加载回退资源。 同样，如果首选语言的操作系统资源不是 Windows IoT 映像的一部分，Windows IoT 将使用其回退的可能英语 (EN-US)。

* 使用区域设置`TrySetHomeGeographicRegion`在[Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)
* 设置 UI 语言时，使用`TrySetLanguages`在[Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)
* 使用集语音语言`TrySetSystemSpeechLanguageAsync`在[Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)
* 设置使用语音`TrySetDefaultVoiceAsync`在[Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)

> [!NOTE]
> 对于正常运行，Cortana 需要区域、 UI 语言和语音语言，使其保持一致，例如： 区域 FR、 UI 和语音语言 FR-FR 或区域 ES、 UI 和语音语言 es 的多少号。 Cortana 使用其自己的语音，UWP 应用程序不能更改它。

## <a name="iotsettingsexe"></a>IoTSettings.exe

若要了解有关更改的区域以及用户或语音语言来构建 Cortana 启用产品的设置的详细信息，请阅读我们[命令行实用工具](../manage-your-device/CommandLineUtils.md)文档。
