---
title: 计算机视觉
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何将 Microosft 认知服务和 OpenCV 用于 IoT 设备。
keywords: windows iot，计算机视觉，认知服务，OpenCV
ms.openlocfilehash: f6d10024f0f52f7219eb3a63dcefa7fd2b4a6fe3
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169195"
---
# <a name="computer-vision"></a>计算机视觉

人认为我们的三维世界是相对轻松的。 从早期的时代开始，我们的大脑可以收集有价值的见解，包括特征标识、障碍、障碍、协调、深度认知等。 计算机视觉尝试使用处理器和照相机来执行相同的操作。 对于当今的设备，它具有无数个应用程序。 无人机可以使用它快速检测并避免在飞行期间发生障碍;工厂可以使用它来检测程序集线条上最小组件中的修饰缺陷;用户可以使用它来检测其心率，而无需使用显示器或医生的设备。 我们的数据中心世界使计算机视觉成为一个非常活跃的研究领域。 公司在本来就十年前的方式中利用它。 随着计算机、照相机和数据在我们的社会中变得越来越根深蒂固，使用计算机视觉的最令人兴奋的功能应尽可能易于访问和使用。 Windows 10 IoT Core 尝试通过与两个产品/服务的兼容性来满足此需要：Microsoft 认知服务和 OpenCV。

## <a name="services"></a>Services
___

### <a name="cognitive-services"></a>认知服务

#### <a name="overview"></a>概述
认知服务最初称为 Project Oxford 的 Microsoft 研究项目，是一组执行高级 "认知任务" 的 Api。 这些 Api 基于经过高度训练的机器学习模型，从 Microsoft Research 探索和开发的多年来获取见解。

认知服务包括5个类别：视觉、语音、语言、知识和搜索。

可在认知服务[网站](https://www.microsoft.com/cognitive-services)上找到有关认知服务的详细信息。

远景类别是计算机视觉应用程序的最有价值的类别，其中包含四个 Api：计算机视觉、情感、面部和视频。 这些 Api 提供以下功能：
- 面部识别
- 动作检测
- 情感识别
- 视频抖动
- 图像内容分析

认知服务非常适合处理大量数据、访问 Microsoft Azure 并大大降低应用程序的上市时间，因为远景 Api 通常会证明是独立开发的时间。 由于 Microsoft 调研的努力，为这些 Api 使用的模型具有良好的培训和广泛的内容。 另一方面，其云连接性要求可降低系统性能，并为 internet 连接产生要求。

#### <a name="pricing"></a>定价
每个 API 订阅都附带一组每月的免费事务（300到30000，具体取决于 API）。 超过此初始金额后，服务会提供合理的价格。 例如，情感 API 免费提供前30000个事务，并且在此之后需要 $0.10 或 $0.25 每个1000事务，具体取决于订阅类型。

有关认知服务定价的详细信息，请参阅他们的[网站](https://www.microsoft.com/cognitive-services/en-us/pricing)。

#### <a name="get-started"></a>入门
若要使用认知服务，用户必须在认知 Services 网站注册，才能接收 API 密钥。 向认知服务提供 API 密钥后，用户可以在 "定价" 部分中提到的限制内调用 Api。

有关每个 API 的文档，请参阅认知服务[网站](https://www.microsoft.com/cognitive-services/en-us/documentation)。

所有认知服务 API 都可以使用C#在任何硬件平台上实现。

想要在 IoT 设备上运行认知服务？ 请访问我们的[教程](https://developer.microsoft.com/en-us/windows/iot/samples/cognitiveservices)，开始学习。

### <a name="opencv"></a>OpenCV

OpenCV 是一种开放源计算机视觉和机器学习软件库，专为计算效率和实时应用程序而设计。 由于其高效率、丰富的工具、对各种平台的支持以及使开发人员生动生动的在线社区，因此它在开发人员和行业中广泛受欢迎。 目前为止，它是最受欢迎的开源计算机视觉工具。 适用于 C/C++、Java 和C#的 OpenCV 库。

OpenCV[网站](http://opencv.org/)提供其他详细信息。

OpenCV 功能：
- 本地图像和视频处理和分析
- 实时对象标识、匹配和跟踪
- 实时面部识别
- 从图像和实时确定的距离
- 3D 映射/建模/重建
- 图像编辑（如排版和颜色更改）

OpenCV 提供了许多优势。 由于已使用 OpenCL （如果已启用）优化的 C/C++内部和对 GPU 的访问，因此，本地数据处理非常高效。 它包含当前可用的大多数计算机视觉功能。 它的生存期和实用工具形成了丰富且经验丰富的在线社区，可帮助新用户解决应用程序或库问题。 另一方面，由于复杂的代码和库设置以及教程和示例代码中的不一致，还会出现一条陡的学习曲线。

目前，使用 IoT Core 的 OpenCV 仅适用于用户基于源构建库，这可能会非常耗时。 为此，我们正在积极努力通过为其创建 NuGet 包集合来更轻松地在 IoT Core 上设置 OpenCV。 通过认知服务使用的 NuGet 包，开发人员只需单击几下鼠标，即可将预构建的库导入到其应用程序中。 使用 NuGet 包的应用程序将继续从专用服务器接收库更新;当开源软件发生公开更改时，用户无需重新生成新的源代码。 包还可使用库中的部件来释放设备上的存储空间。

当前正在进行一项工作，请继续检查 WindowsOnDevices.com 是否有更新！

同时，若要从 ARM 的源构建库，请访问[GitHub 存储库](https://github.com/Microsoft/opencv/tree/vs2015-samples-ARM)。

想要在 IoT Core 设备上运行 OpenCV？ 请访问我们的[教程](https://developer.microsoft.com/en-us/windows/iot/samples/opencv)，开始学习。

## <a name="comparing-opencv-and-cognitive-services"></a>比较 OpenCV 和认知服务

> |        |Microsoft 认知服务|OpenCV|
> |---------------------|--------|------|
> |易于在 Windows 上使用|是|否 |
> |体系结构支持|ARM、x86、x64 | ARM、x86、x64|
> |面部识别和跟踪| 是 | 是|
> |情感识别| 是 | 是|
> |3D 重建和映射| 否 | 是|
> |内容检测| 检测常规功能，而不是特定对象 | 是|
> |视频抖动| 是 | 是|
> |动作检测| 是 | 是|
> |社区| 认知服务包含多个行业的多个活动用户和几个热门网站，包括 how-old.net 和 celebslike.me | OpenCV 是非常受欢迎的开源项目;成千上万的人对 it 做出了贡献并维护了|
> |文档| 认知服务具有全面的清晰文档 | 可以联机使用许多示例，但每个示例都是由不同的人编写的，因此，可能会不一致。|
> |Free| 是，到一个范围内（更多[详细信息，](https://azure.microsoft.com/pricing/details/cognitive-services/)请参阅） | 是|
> |性能| 所有操作和 API 调用都需要访问云中的数据 | 所有算法都经过优化和本地，使用C++而不是 Python 会进一步提高速度|
> |支持的相机/硬件| 任何 USB 或嵌入式相机 | 任何 USB 或嵌入式相机|
> |支持的语言/框架| C#，UWP | C/C++、Python、Java、 C#UWP|
> |启动时间| 用户可以直接在文档中使用代码示例和直观的 Api | OpenCV 的强大功能和灵活性意味着它还需要大量配置和代码来执行复杂的操作|
> |链接| [示例程序](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CognitiveServicesExample) | [示例程序](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/OpenCVExample) |
> |    |   [认知服务网站](https://azure.microsoft.com/services/cognitive-services/) |  [OpenCV 网站](http://opencv.org/)


