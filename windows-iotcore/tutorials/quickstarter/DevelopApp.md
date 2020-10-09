---
title: 开发适用于设备的应用
ms.date: 04/17/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何添加和开发适合你的设备的应用。 查看指向建议的初学者示例和应用开发资源的链接。
keywords: Windows 10 IoT 核心版, 入门, 开发应用, 应用
ms.openlocfilehash: 3b41c7de76644b25193fdf751667e8fd119b4951
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91657273"
---
# <a name="develop-an-app-for-your-device"></a>开发适用于设备的应用

> [!NOTE]
> 在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。

有了一个工作设备并可运行默认应用以后，则需让设备进入下一阶段，即开发应用并将其部署到设备上。 在探索示例之前，需下载进行应用程序开发所需的 [Visual Studio 2017](https://www.visualstudio.com/downloads/)。

如果打算将 C++ 用于项目，则在下载 Visual Studio 2017 时，请确保勾选以下示例中所示的框：

![适用于 C++ 和 Windows 10 IoT 的基本组件](../../media/DevelopApp/VS-CPP.jpg)

如果对将来开发后台应用程序、Arduino 接线应用程序或控制台应用程序感兴趣，则还需从 [Visual Studio 库](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15)下载项目模板。


若要开始使用某个应用，我们推荐你从下面建议的初学者示例着手。 但是，如果你已准备好部署自己的应用，也可参考我们在后续部分提供的有用链接。

## <a name="suggested-starter-samples"></a>建议的初学者示例

* [Hello Blinky](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky)
* [Hello World](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloWorld)
* [IoT 启动应用示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTStartApp)
* [RPi 认知服务示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/RPiCognitiveService) 



一旦部署应用，那么祝贺你，你已完成本快速启动！ 请继续探索。或者，如果你脑海中有一些创意，请查看我们的文档，了解 Windows 10 IoT 的商业化情况。 

## <a name="app-development-resources"></a>应用开发资源

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">主题</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)">开发前台应用程序</a></p></td>
<td align="left"><p>了解 Windows 10 IoT 核心版支持的不同语言，以及支持的 UWP 和非 UWP 应用类型。</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)">开发后台应用程序</a></p></td>
<td align="left"><p>了解 Windows 10 IoT 核心版支持的不同语言，以及支持的 UWP 和非 UWP 应用类型。</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)">使用 Visual Studio 部署应用</a></p></td>
<td align="left"><p>了解如何使用 Visual Studio 将不同的应用部署到 Windows 10 IoT 核心版设备。</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)">使用远程控制台应用调试来调试应用</a></p></td>
<td align="left"><p>了解如何在 Visual Studio 中使用远程控制台应用调试来调试应用。</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)">在 Windows 10 IoT 核心版设备上安装应用</a></p></td>
<td align="left"><p>了解如何将应用安装到 Windows 10 IoT 核心版设备。</p></td>
</tr>

</tbody>
</table>
