---
title: 计算机视觉
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 IoT 设备获得有关 Microosft 认知服务和 OpenCV。
keywords: windows iot，计算机影像，认知服务，OpenCV
ms.openlocfilehash: f6d10024f0f52f7219eb3a63dcefa7fd2b4a6fe3
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510713"
---
# <a name="computer-vision"></a>计算机视觉

人类相对轻松地认为我们三维世界。 从早期的年龄，我们的大脑可以收集有价值的见解，包括功能标识、 障碍避免、 协调、 深度产品感受和许多其他从 visual 触发操作。 计算机视觉是尝试使用的处理器和照相机来执行相同的操作。 它有无数今天的设备的应用程序。 无人机可以使用它来快速检测和飞行; 期间避免障碍一个工厂可以使用它来检测程序集行中; 上的最小组件中的修饰的缺陷和一个人可以使用它来检测其核心速率，而无需使用的监视器或医生的设备。 我们专注于数据的世界进行了计算机视觉的令人难以置信活动研究区域。 公司中被视为不大可能甚至十年前的方法利用它。 如计算机、 相机、 和数据变得更始终贯彻在当今社会，应进行工具能够利用计算机视觉的最令人兴奋功能访问和使用尽可能一样简单。 Windows 10 IoT Core 尝试满足这种需要通过与两个产品/服务的兼容性：Microsoft 认知服务和 OpenCV。

## <a name="services"></a>Services
___

### <a name="cognitive-services"></a>认知服务

#### <a name="overview"></a>概述
认知服务最初 Microsoft 研究项目称为 Project Oxford，Api 中执行高级"认知任务"的集合。 这些 Api 拉取根据高度训练机器学习的探索和部署 Microsoft research 多年的模型对数据的见解。

认知服务由 5 个类别：影像、 语音、 语言、 知识和搜索。

您可以找到有关认知服务有关认知服务的详细信息[网站](https://www.microsoft.com/cognitive-services)。

视觉类别，对于计算机影像应用程序，最有价值的类别包含四种 Api:计算机视觉、 情感、 人脸和视频。 这些 Api 提供以下功能：
- 面部识别
- 运动检测
- 表情识别
- 视频防抖动
- 图像内容分析

认知服务非常适合用于处理大量的数据，访问 Microsoft Azure，并极大地减少了您应用程序的上市时间，作为视觉 Api 通常证明是独立开发实现起来非常耗时。 使用这些 Api 的模型是良好的培训和广泛归功于 Microsoft Research 的工作。 另一方面，其云连接要求会降低系统性能，并创建连接到 internet 的要求。

#### <a name="pricing"></a>定价
每个 API 的订阅将每个月 (300 到 30,000，具体取决于该 API) 附带一组可用的事务。 超出此初始数量后, 服务附带了合理的价格。 例如，情感 API 免费提供首先 30,000 个事务，并需要 0.10 美元或 0.25 美元后，每个 1000年事务，具体取决于订阅类型。

在上找到有关认知服务定价详细信息及其[网站](https://www.microsoft.com/cognitive-services/en-us/pricing)。

#### <a name="get-started"></a>入门
若要使用认知服务，用户必须注册认知服务网站上接收的 API 密钥。 后向认知服务提供 API 密钥，用户可以调用在"定价"部分中所述的限制范围内的 Api。

每个 API 的文档可能位于认知服务[网站](https://www.microsoft.com/cognitive-services/en-us/documentation)。

所有认知服务 Api 可以实现任何硬件平台使用C#。

想要在 IoT 设备上运行认知服务？ 请访问我们[教程](https://developer.microsoft.com/en-us/windows/iot/samples/cognitiveservices)若要开始。

### <a name="opencv"></a>OpenCV

OpenCV 是一个开放源代码计算机视觉和机器学习计算效率和实时应用程序而设计的软件库。 它的广泛流行开发人员和由于其前所未有的效率、 灵活的工具、 支持广泛的平台，行业中且充满活力的开发人员的在线社区。 它是到目前为止最受欢迎的开源计算机视觉工具。 OpenCV 库都可用于 C /C++，Java，和C#。

OpenCV[网站](http://opencv.org/)提供其他详细信息。

OpenCV 功能：
- 本地图像和视频处理和分析
- 实时对象标识、 匹配和跟踪
- 实时面部识别
- 距离确定从映像和实时
- 三维映射/建模/重建
- 图像 （如组合和颜色更改） 编辑

OpenCV 提供了很多优点。 由于优化 C 是非常有效的本地数据处理 /C++内部结构和 GPU 使用 OpenCL （如果已启用） 对其的访问。 它包含大多数，如果不是全部，当前可用的计算机视觉功能。 其使用寿命和实用程序建立了一个丰富而有经验的在线社区可帮助新用户与应用程序或库问题。 但是，没有陡峭的学习曲线由于复杂的代码和库设置以及不一致教程和示例代码。

目前，使用 IoT Core OpenCV 仅适用于用户生成源，这可能非常耗时的库。 正因为如此，我们将积极努力使 OpenCV 更方便地通过为其创建 NuGet 包的集合，在 IoT Core 上设置。 NuGet 包，将使用认知服务，允许开发人员预生成的库导入到其应用程序，需单击几下提供完整的功能。 使用 NuGet 包的应用程序将继续从专用的服务器; 接收库更新用户无需对开放源代码软件的公共更改时重新生成新的源代码。 包还免除了仅使用的库在设备上的存储空间。

这是当前工作正在进行的因此请随时查看 WindowsOnDevices.com 更新 ！

在此期间，若要为 ARM 生成源的库，请访问[GitHub 存储库](https://github.com/Microsoft/opencv/tree/vs2015-samples-ARM)。

想要在 IoT Core 设备上运行 OpenCV 吗？ 请访问我们[教程](https://developer.microsoft.com/en-us/windows/iot/samples/opencv)若要开始。

## <a name="comparing-opencv-and-cognitive-services"></a>比较 OpenCV 和认知服务

> |        |Microsoft 认知服务|OpenCV|
> |---------------------|--------|------|
> |在 Windows 上易于使用|是|否 |
> |体系结构支持|ARM，x86 x64 | ARM，x86 x64|
> |面部识别和跟踪| 是 | 是|
> |表情识别| 是 | 是|
> |三维重建和映射| 否 | 是|
> |内容检测| 检测到的一般功能而不是特定对象 | 是|
> |视频防抖动| 是 | 是|
> |运动检测| 是 | 是|
> |社区| 认知服务跨多个行业和几个流行的网站，包括 how-old.net 和 celebslike.me 具有许多活动用户 | OpenCV 是非常受欢迎的开源项目;成千上万的用户具有的贡献和维护它|
> |文档| 认知服务总体具有清晰、 最广泛的文档 | 有许多示例可用联机，但每个示例由不同人员编写，并因此可能会不一致有时|
> |Free| 是的对某个扩展盘区 (更多详细信息[此处](https://azure.microsoft.com/pricing/details/cognitive-services/)) | 是|
> |性能| 所有操作和 API 调用都需要访问云中的数据 | 所有算法都是优化和本地的以及使用C++而不是 Python 提高速度，甚至更多|
> |支持的照相机/硬件| 任何 USB 或嵌入的相机 | 任何 USB 或嵌入的相机|
> |支持的语言/框架| C#UWP | C /C++，Python、 Java、 C#，UWP|
> |启动时间| 用户可以使用以及可直接从文档的直观 Api 的代码示例 | OpenCV 的强大功能和灵活性意味着，需要大量配置和代码来执行复杂的操作|
> |链接| [示例程序](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CognitiveServicesExample) | [示例程序](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/OpenCVExample) |
> |    |   [认知服务网站](https://azure.microsoft.com/services/cognitive-services/) |  [OpenCV 网站](http://opencv.org/)


