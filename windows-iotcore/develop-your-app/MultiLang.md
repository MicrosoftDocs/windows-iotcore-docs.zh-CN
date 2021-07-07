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
# <a name="language-support"></a>语言支持

语言支持可以在两个级别启用：应用程序级别和 OS 级别，具体取决于在映像上提供的语言资源。

## <a name="languages-in-uwp-applications"></a>UWP 应用程序中的语言
UWP 应用程序语言不限于 OS 中包含的语言。  事实上，不触发 shell UI 或利用语音资源的 IoT 设备可以通过其 UWP 应用程序以许多不同的语言提供设备体验，即使基础 Windows 10 IoT 核心版 OS 是在 en-US 默认模式下构建的。 

UWP 应用程序必须为需要支持的语言提供资源。 [Windows。Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) API 可用于指定与语言相关的首选项。

请参阅下面的示例应用程序：

* [IoTDefaultApp 示例](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [ApplicationResources 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a>OS 中的语言

Windows 10IoTCore 工具包现在包括以下语言的语言资源：

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
> | 巴西 (语)  | pt-BR | 南美洲/欧洲 |
> | 葡萄牙 (语)  | pt-PT | 南美洲/欧洲 |

这些语言资源包含 UI 字符串、语音语言和语音 (语音合成) 。 WindowsIoT 映像可以使用其中一个或多个资源生成，必须在映像期间指定，以后不能修改。 请注意，与 UI 语言相关的资源独立于语音语言和语音资源。

### <a name="specifying-ui-and-speech-resources"></a>指定 UI 和语音资源 
在 OEM 输入 xml 文件中，指定所需的 UI 和语音语言，如下所示

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
在 OEM 输入 xml 文件中，指定所需的语音数据资源，如下所示，

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
> 默认情况下，en-US 语音数据包含在图像中。

### <a name="samples"></a>示例
* 有关[多种语言支持，请参阅 MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample)
* 请参阅 [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) 了解 fr-FR 语言，将 en-US 用作回退语言。
    * 请注意，当更改启动 UI 语言时，帐户名称 `administrator` 也会以启动 UI 语言翻译。 因此，在 fr-FR 中，它是 `administrateur` 。 请参阅 [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)

## <a name="changing-user-preferences-language-region-speech-and-voice"></a>更改用户首选项 (语言、区域、语音和语音) 

UWP 应用程序可以使用 WinRT API 来设置默认应该使用的区域、首选 UI 语言列表、语音语言和语音。 设置首选 UI 语言列表后，UWP 应用程序将尝试加载相应的 (，除非应用程序以编程方式阻止) 。
 
如果应用程序没有相应的资源，则加载回退资源。 同样，如果首选语言的 OS 资源不是 Windows IoT 映像的一部分，Windows IoT 将使用其回退资源（可能是英语 (en-US) ）。

* 在 `TrySetHomeGeographicRegion` tem 中Windows.Sys[ 区域。UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)
* 在 tem 中Windows.Sys`TrySetLanguages` [ UI 语言。UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)
* 使用 中的 设置 `TrySetSystemSpeechLanguageAsync` 语音[Windows。Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)
* 在 Windows `TrySetDefaultVoiceAsync` [中设置语音。Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer)

> [!NOTE]
> 若要正常运行，Cortana区域、UI 语言和语音语言保持一致，例如：区域 FR、UI 和语音语言 fr-FR 或区域 ES、UI 和语音语言 es-ES。 Cortana使用自己的语音，UWP 应用程序无法更改它。

## <a name="iotsettingsexe"></a>IoTSettings.exe

若要详细了解如何更改区域和用户或语音语言的设置以构建 Cortana 启用的产品，请阅读我们的[命令行 Utils](../manage-your-device/CommandLineUtils.md)文档。
