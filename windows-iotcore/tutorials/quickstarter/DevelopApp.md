---
title: 开发适用于你的设备的应用
author: saraclay
ms.author: saclayt
ms.date: 04/17/2018
ms.topic: article
description: 了解如何添加和开发适用于你的设备应用
keywords: Windows 10 IoT 核心版、 开始，开发应用程序，应用程序
ms.openlocfilehash: f5ee15c2115d6e10a2a8ade1522c7b66cf788bee
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59511034"
---
# <a name="develop-an-app-for-your-device"></a>开发适用于你的设备的应用

> [!NOTE]
> 部署到 RS5 时，visual Studio 将生成一个含义模糊的错误 （或使用 OpenSSH RS4 启用） IoT 图像，除非已从 RS4 或更高版本的 SDK 安装 Visual Studio 可以访问。

以后，即可使用默认的应用运行的工作设备，你将需要你的设备至下一级别的开发和部署你的设备上的应用程序。 在深入之前示例，你将需要下载[Visual Studio 2017](https://www.visualstudio.com/downloads/)用于开发应用程序。

如果您打算使用C++项目，下载 Visual Studio 2017 时，请务必选中的复选框相同的方式与它们在下面的示例：

![基础知识C++和 Windows 10 IoT](../../media/DevelopApp/VS-CPP.jpg)

如果有兴趣在将来开发背景，Arduino 连线或控制台应用程序，您还需要下载中的项目模板[Visual Studio 库](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15)。


若要获取与应用启动并运行，我们建议从与以下建议的初学者示例。 但如果您准备好部署您自己的应用程序，我们还提供有用的后面部分中的链接。

## <a name="suggested-starter-samples"></a>建议的初学者示例

* [你好，Blinky](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky)
* [Hello World](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloWorld)
* [IoT 启动应用程序示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTStartApp)
* [RPi 认知服务示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/RPiCognitiveService) 



部署后你的应用-祝贺你，现已将此 quickstarter ！ 继续播放，或如果已在您头周围弹跳的一些建议请查看我们的文档上使用 Windows 10 IoT commercializing。 

## <a name="app-development-resources"></a>应用开发资源

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">主题</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)">前台应用程序开发</a></p></td>
<td align="left"><p>了解有关 Windows 10 IoT 核心版，以及 UWP 支持的不同语言和支持的非 UWP 应用程序类型。</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)">开发后台应用程序</a></p></td>
<td align="left"><p>了解有关 Windows 10 IoT 核心版，以及 UWP 支持的不同语言和支持的非 UWP 应用程序类型。</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)">使用 Visual Studio 部署应用</a></p></td>
<td align="left"><p>了解如何使用 Visual Studio 在不同的应用部署到 Windows 10 IoT Core 设备。</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)">使用远程控制台应用程序调试调试应用</a></p></td>
<td align="left"><p>了解如何调试在 Visual Studio 中使用远程控制台应用程序调试的应用。</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)">在 Windows 10 IoT Core 设备上安装您的应用程序</a></p></td>
<td align="left"><p>了解如何将应用安装到 Windows 10 IoT Core 设备。</p></td>
</tr>

</tbody>
</table>
