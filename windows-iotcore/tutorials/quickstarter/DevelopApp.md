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
# <a name="develop-an-app-for-your-device"></a><span data-ttu-id="6f74a-104">开发适用于你的设备的应用</span><span class="sxs-lookup"><span data-stu-id="6f74a-104">Develop an app for your device</span></span>

> [!NOTE]
> <span data-ttu-id="6f74a-105">部署到 RS5 时，visual Studio 将生成一个含义模糊的错误 （或使用 OpenSSH RS4 启用） IoT 图像，除非已从 RS4 或更高版本的 SDK 安装 Visual Studio 可以访问。</span><span class="sxs-lookup"><span data-stu-id="6f74a-105">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="6f74a-106">以后，即可使用默认的应用运行的工作设备，你将需要你的设备至下一级别的开发和部署你的设备上的应用程序。</span><span class="sxs-lookup"><span data-stu-id="6f74a-106">Now that you have a working device with the default app running, you'll want to take your device to the next level by developing and deploying an app on your device.</span></span> <span data-ttu-id="6f74a-107">在深入之前示例，你将需要下载[Visual Studio 2017](https://www.visualstudio.com/downloads/)用于开发应用程序。</span><span class="sxs-lookup"><span data-stu-id="6f74a-107">Before diving into samples, you'll need to download [Visual Studio 2017](https://www.visualstudio.com/downloads/) for application development.</span></span>

<span data-ttu-id="6f74a-108">如果您打算使用C++项目，下载 Visual Studio 2017 时，请务必选中的复选框相同的方式与它们在下面的示例：</span><span class="sxs-lookup"><span data-stu-id="6f74a-108">If you're planning to use C++ for your projects, when downloading Visual Studio 2017, make sure to check the boxes the same way as they are in the example below:</span></span>

![基础知识C++和 Windows 10 IoT](../../media/DevelopApp/VS-CPP.jpg)

<span data-ttu-id="6f74a-110">如果有兴趣在将来开发背景，Arduino 连线或控制台应用程序，您还需要下载中的项目模板[Visual Studio 库](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15)。</span><span class="sxs-lookup"><span data-stu-id="6f74a-110">If you're interested in developing background, Arduino Wiring or console applications in the future, you'll also want to download project templates from the [Visual Studio Gallery](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15).</span></span>


<span data-ttu-id="6f74a-111">若要获取与应用启动并运行，我们建议从与以下建议的初学者示例。</span><span class="sxs-lookup"><span data-stu-id="6f74a-111">To get up and running with an app, we recommend starting with a suggested starter sample below.</span></span> <span data-ttu-id="6f74a-112">但如果您准备好部署您自己的应用程序，我们还提供有用的后面部分中的链接。</span><span class="sxs-lookup"><span data-stu-id="6f74a-112">But if you're ready to deploy your own app, we've also provided helpful links in the section after.</span></span>

## <a name="suggested-starter-samples"></a><span data-ttu-id="6f74a-113">建议的初学者示例</span><span class="sxs-lookup"><span data-stu-id="6f74a-113">Suggested starter samples</span></span>

* [<span data-ttu-id="6f74a-114">你好，Blinky</span><span class="sxs-lookup"><span data-stu-id="6f74a-114">Hello Blinky</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky)
* [<span data-ttu-id="6f74a-115">Hello World</span><span class="sxs-lookup"><span data-stu-id="6f74a-115">Hello World</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloWorld)
* [<span data-ttu-id="6f74a-116">IoT 启动应用程序示例</span><span class="sxs-lookup"><span data-stu-id="6f74a-116">IoT Startup App sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTStartApp)
* [<span data-ttu-id="6f74a-117">RPi 认知服务示例</span><span class="sxs-lookup"><span data-stu-id="6f74a-117">RPi Cognitive Service sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/RPiCognitiveService) 



<span data-ttu-id="6f74a-118">部署后你的应用-祝贺你，现已将此 quickstarter ！</span><span class="sxs-lookup"><span data-stu-id="6f74a-118">Once you've deployed your app - congratulations, you've finished this quickstarter!</span></span> <span data-ttu-id="6f74a-119">继续播放，或如果已在您头周围弹跳的一些建议请查看我们的文档上使用 Windows 10 IoT commercializing。</span><span class="sxs-lookup"><span data-stu-id="6f74a-119">Continue to play around or, if you have a few ideas bouncing around in your head, check out our documentation on commercializing with Windows 10 IoT.</span></span> 

## <a name="app-development-resources"></a><span data-ttu-id="6f74a-120">应用开发资源</span><span class="sxs-lookup"><span data-stu-id="6f74a-120">App development resources</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="6f74a-121">主题</span><span class="sxs-lookup"><span data-stu-id="6f74a-121">Topic</span></span></th>
<th align="left"><span data-ttu-id="6f74a-122">描述</span><span class="sxs-lookup"><span data-stu-id="6f74a-122">Description</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)"><span data-ttu-id="6f74a-123">前台应用程序开发</span><span class="sxs-lookup"><span data-stu-id="6f74a-123">Developing foreground applications</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f74a-124">了解有关 Windows 10 IoT 核心版，以及 UWP 支持的不同语言和支持的非 UWP 应用程序类型。</span><span class="sxs-lookup"><span data-stu-id="6f74a-124">Learn about the different languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)"><span data-ttu-id="6f74a-125">开发后台应用程序</span><span class="sxs-lookup"><span data-stu-id="6f74a-125">Developing background applications</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f74a-126">了解有关 Windows 10 IoT 核心版，以及 UWP 支持的不同语言和支持的非 UWP 应用程序类型。</span><span class="sxs-lookup"><span data-stu-id="6f74a-126">Learn about the different languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)"><span data-ttu-id="6f74a-127">使用 Visual Studio 部署应用</span><span class="sxs-lookup"><span data-stu-id="6f74a-127">Deploy an App with Visual Studio</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f74a-128">了解如何使用 Visual Studio 在不同的应用部署到 Windows 10 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="6f74a-128">Learn how to deploy your different apps with Visual Studio to your Windows 10 IoT Core device.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)"><span data-ttu-id="6f74a-129">使用远程控制台应用程序调试调试应用</span><span class="sxs-lookup"><span data-stu-id="6f74a-129">Debug your app using Remote Console App Debugging</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f74a-130">了解如何调试在 Visual Studio 中使用远程控制台应用程序调试的应用。</span><span class="sxs-lookup"><span data-stu-id="6f74a-130">Learn how to debug your apps using Remote Console App Debugging in Visual Studio.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)"><span data-ttu-id="6f74a-131">在 Windows 10 IoT Core 设备上安装您的应用程序</span><span class="sxs-lookup"><span data-stu-id="6f74a-131">Install your app on your Windows 10 IoT Core device</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="6f74a-132">了解如何将应用安装到 Windows 10 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="6f74a-132">Learn how to install your app to your Windows 10 IoT Core device.</span></span></p></td>
</tr>

</tbody>
</table>
