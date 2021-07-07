---
title: 开发适用于设备的应用
ms.date: 04/17/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何添加和开发适合你的设备的应用。 查看指向建议的初学者示例和应用开发资源的链接。
keywords: Windows 10 IoT 核心版, 入门, 开发应用, 应用
ms.openlocfilehash: 25023bc064e89a37218110b5afa9fda72c2cbbbd
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230474"
---
# <a name="develop-an-app-for-your-device"></a><span data-ttu-id="31c1b-105">开发适用于设备的应用</span><span class="sxs-lookup"><span data-stu-id="31c1b-105">Develop an app for your device</span></span>

> [!NOTE]
> <span data-ttu-id="31c1b-106">在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="31c1b-106">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="31c1b-107">有了一个工作设备并可运行默认应用以后，则需让设备进入下一阶段，即开发应用并将其部署到设备上。</span><span class="sxs-lookup"><span data-stu-id="31c1b-107">Now that you have a working device with the default app running, you'll want to take your device to the next level by developing and deploying an app on your device.</span></span> <span data-ttu-id="31c1b-108">在探索示例之前，需下载进行应用程序开发所需的 [Visual Studio 2017](https://www.visualstudio.com/downloads/)。</span><span class="sxs-lookup"><span data-stu-id="31c1b-108">Before diving into samples, you'll need to download [Visual Studio 2017](https://www.visualstudio.com/downloads/) for application development.</span></span>

<span data-ttu-id="31c1b-109">如果打算将 C++ 用于项目，则在下载 Visual Studio 2017 时，请确保勾选以下示例中所示的框：</span><span class="sxs-lookup"><span data-stu-id="31c1b-109">If you're planning to use C++ for your projects, when downloading Visual Studio 2017, make sure to check the boxes the same way as they are in the example below:</span></span>

![适用于 C++ 和 Windows 10 IoT 的基本组件](../../media/DevelopApp/VS-CPP.jpg)

<span data-ttu-id="31c1b-111">如果对将来开发后台应用程序、Arduino 接线应用程序或控制台应用程序感兴趣，则还需从 [Visual Studio 库](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15)下载项目模板。</span><span class="sxs-lookup"><span data-stu-id="31c1b-111">If you're interested in developing background, Arduino Wiring or console applications in the future, you'll also want to download project templates from the [Visual Studio Gallery](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15).</span></span>


<span data-ttu-id="31c1b-112">若要开始使用某个应用，我们推荐你从下面建议的初学者示例着手。</span><span class="sxs-lookup"><span data-stu-id="31c1b-112">To get up and running with an app, we recommend starting with a suggested starter sample below.</span></span> <span data-ttu-id="31c1b-113">但是，如果你已准备好部署自己的应用，也可参考我们在后续部分提供的有用链接。</span><span class="sxs-lookup"><span data-stu-id="31c1b-113">But if you're ready to deploy your own app, we've also provided helpful links in the section after.</span></span>

## <a name="suggested-starter-samples"></a><span data-ttu-id="31c1b-114">建议的初学者示例</span><span class="sxs-lookup"><span data-stu-id="31c1b-114">Suggested starter samples</span></span>

* [<span data-ttu-id="31c1b-115">Hello Blinky</span><span class="sxs-lookup"><span data-stu-id="31c1b-115">Hello Blinky</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky)
* [<span data-ttu-id="31c1b-116">Hello World</span><span class="sxs-lookup"><span data-stu-id="31c1b-116">Hello World</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloWorld)
* [<span data-ttu-id="31c1b-117">IoT 启动应用示例</span><span class="sxs-lookup"><span data-stu-id="31c1b-117">IoT Startup App sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTStartApp)
* [<span data-ttu-id="31c1b-118">RPi 认知服务示例</span><span class="sxs-lookup"><span data-stu-id="31c1b-118">RPi Cognitive Service sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/RPiCognitiveService) 



<span data-ttu-id="31c1b-119">一旦部署应用，那么祝贺你，你已完成本快速启动！</span><span class="sxs-lookup"><span data-stu-id="31c1b-119">Once you've deployed your app - congratulations, you've finished this quickstarter!</span></span> <span data-ttu-id="31c1b-120">请继续探索。或者，如果你脑海中有一些创意，请查看我们的文档，了解 Windows 10 IoT 的商业化情况。</span><span class="sxs-lookup"><span data-stu-id="31c1b-120">Continue to play around or, if you have a few ideas bouncing around in your head, check out our documentation on commercializing with Windows 10 IoT.</span></span> 

## <a name="app-development-resources"></a><span data-ttu-id="31c1b-121">应用开发资源</span><span class="sxs-lookup"><span data-stu-id="31c1b-121">App development resources</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="31c1b-122">主题</span><span class="sxs-lookup"><span data-stu-id="31c1b-122">Topic</span></span></th>
<th align="left"><span data-ttu-id="31c1b-123">说明</span><span class="sxs-lookup"><span data-stu-id="31c1b-123">Description</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><span data-ttu-id="31c1b-124"><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)">开发前台应用程序</a></span><span class="sxs-lookup"><span data-stu-id="31c1b-124"><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)">Developing foreground applications</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="31c1b-125">了解 Windows 10 IoT 核心版支持的不同语言，以及支持的 UWP 和非 UWP 应用类型。</span><span class="sxs-lookup"><span data-stu-id="31c1b-125">Learn about the different languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="31c1b-126"><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)">开发后台应用程序</a></span><span class="sxs-lookup"><span data-stu-id="31c1b-126"><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)">Developing background applications</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="31c1b-127">了解 Windows 10 IoT 核心版支持的不同语言，以及支持的 UWP 和非 UWP 应用类型。</span><span class="sxs-lookup"><span data-stu-id="31c1b-127">Learn about the different languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="31c1b-128"><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)">使用 Visual Studio 部署应用</a></span><span class="sxs-lookup"><span data-stu-id="31c1b-128"><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)">Deploy an App with Visual Studio</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="31c1b-129">了解如何使用 Visual Studio 将不同的应用部署到 Windows 10 IoT 核心版设备。</span><span class="sxs-lookup"><span data-stu-id="31c1b-129">Learn how to deploy your different apps with Visual Studio to your Windows 10 IoT Core device.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="31c1b-130"><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)">使用远程控制台应用调试来调试应用</a></span><span class="sxs-lookup"><span data-stu-id="31c1b-130"><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)">Debug your app using Remote Console App Debugging</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="31c1b-131">了解如何在 Visual Studio 中使用远程控制台应用调试来调试应用。</span><span class="sxs-lookup"><span data-stu-id="31c1b-131">Learn how to debug your apps using Remote Console App Debugging in Visual Studio.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="31c1b-132"><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)">在 Windows 10 IoT 核心版设备上安装应用</a></span><span class="sxs-lookup"><span data-stu-id="31c1b-132"><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)">Install your app on your Windows 10 IoT Core device</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="31c1b-133">了解如何将应用安装到 Windows 10 IoT 核心版设备。</span><span class="sxs-lookup"><span data-stu-id="31c1b-133">Learn how to install your app to your Windows 10 IoT Core device.</span></span></p></td>
</tr>

</tbody>
</table>
