---
title: 计算机视觉
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何对 IoT 设备使用 Microosft 认知服务和 OpenCV。
keywords: windows iot， 计算机视觉， 认知服务， OpenCV
ms.openlocfilehash: 47d195545bf4b59351c6a1b08b3d6f0d4f47b07c
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229694"
---
# <a name="computer-vision"></a>计算机视觉

人类相对容易地感知我们的三维世界。 从早期开始，我们的大脑可以收集有价值的见解，包括特征识别、障碍规避、协调、深度感知，以及来自视觉障碍的许多其他见解。 计算机视觉是尝试使用处理器和相机执行相同的操作。 它拥有适用于当今设备的数个应用程序。 无人机可以使用它在飞行期间快速检测和避免障碍;工厂可以使用它来检测装配线上最小组件中的修饰缺陷;并且一个人可以使用它来检测其心动率，而无需使用监视器或医生的设备。 以数据为中心的世界使计算机视觉成为一个非常活跃的研究领域。 公司以十年前无法实现的方式利用它。 随着计算机、照相机和数据在我们的社会越来越受到支持，应尽量使利用计算机视觉最令人心动的功能的工具变得易于访问和使用。 Windows 10 IoT 核心版 Microsoft 认知服务和 OpenCV 这两个产品/服务，尝试满足此需求。

## <a name="services"></a>服务
___

### <a name="cognitive-services"></a>认知服务

#### <a name="overview"></a>概述
认知服务最初是名为 Project 的 Microsoft Research 项目，是执行高级"认知任务"的 API 集合。 这些 API 基于 Microsoft Research 多年来的探索和开发中经过高度训练的机器学习模型，从数据中拉取见解。

认知服务由 5 个类别组成：视觉、语音、语言、知识和搜索。

可以在认知服务网站上找到有关认知服务 [详细信息](https://www.microsoft.com/cognitive-services)。

视觉类别是计算机视觉应用程序最有价值的类别，包含四个 API：计算机视觉、情感、人脸和视频。 这些 API 提供以下功能：
- 面部识别
- 动作检测
- 情感识别
- 视频稳定
- 图像内容分析

认知服务非常适用于处理大量数据、访问 Microsoft Azure，并极大地缩短应用程序的上市时间，因为视觉 API 通常证明独立开发非常耗时。 由于 Microsoft Research 的工作，用于这些 API 的模型经过良好训练且广泛。 另一方面，其云连接要求会降低系统性能，并创建 Internet 连接的要求。

#### <a name="pricing"></a>定价
每个 API 订阅每月附带一组免费事务 (300 到 30，000 个，具体取决于 API) 。 超过此初始金额后，服务会提供合理的价格。 例如，情感 API 免费提供前 30，000 个事务，之后每 1000 个事务需要 $0.10 或 $0.25，具体取决于订阅类型。

有关认知服务定价的更多详细信息，请参阅其 [网站](https://www.microsoft.com/cognitive-services/en-us/pricing)。

#### <a name="get-started"></a>入门
若要使用认知服务，用户必须在 Congitive Services 网站上注册以接收 API 密钥。 向认知服务提供 API 密钥后，用户可以在"定价"部分中提到的限制内调用 API。

可以在认知服务网站上找到每个 API [的文档](https://www.microsoft.com/cognitive-services/en-us/documentation)。

所有认知服务 API都可以通过 C# 在任何硬件平台上实现。

想要在 IoT 设备上运行认知服务？ 请访问 [我们的教程](https://developer.microsoft.com/en-us/windows/iot/samples/cognitiveservices) 以开始使用。

### <a name="opencv"></a>OpenCV

OpenCV 是一种开源计算机视觉和机器学习软件库，专为计算效率和实时应用程序设计。 它以前所未有的效率、通用工具、对各种平台的支持以及活跃的在线开发人员社区，在开发人员和行业中广泛使用。 它是到目前为止最常用的开源计算机视觉工具。 OpenCV 库适用于 C/C++、Java 和 C#。

OpenCV [网站提供了](http://opencv.org/) 更多详细信息。

OpenCV 功能：
- 本地图像和视频处理和分析
- 实时对象标识、匹配和跟踪
- 实时面部识别
- 从图像和实时距离确定
- 3D 映射/建模/重构
- 图像编辑 (，如合成和颜色更改) 

OpenCV 具有许多优点。 它非常适用于本地数据处理，因为优化了 C/C++ 内部机制，并且它使用 OpenCL (访问 GPU（如果) ）。 它包含当前可用的大多数（如果不是全部）计算机视觉功能。 其长期性和实用工具已形成一个广泛且经验丰富的在线社区，可帮助新用户解决应用程序或库问题。 另一方面，由于复杂的代码和库设置以及教程和示例代码中的不一致，存在一个复杂的学习曲线。

目前，只有当用户从源生成库时，具有 IoT Core 的 OpenCV 才有效，这很耗时。 因此，我们正在努力通过为 IoT Core 创建一组 NuGet包，使 OpenCV 更易于设置。 认知NuGet包允许开发人员将预构建的库导入到其应用程序中，通过单击几下鼠标即可提供完整的功能。 使用 NuGet 包的应用程序将继续从专用服务器接收库更新;当对开源软件进行公共更改时，用户不需要重新生成新的源代码。 该包还仅使用库的某些部分来节省设备的存储空间。

这是当前正在处理的工作，因此请 WindowsOnDevices.com 更新！

同时，若要从 ARM 的源生成库，请访问GitHub[存储库](https://github.com/Microsoft/opencv/tree/vs2015-samples-ARM)。

想要在 IoT Core 设备上运行 OpenCV？ 请访问 [我们的教程](https://developer.microsoft.com/en-us/windows/iot/samples/opencv) 以开始使用。

## <a name="comparing-opencv-and-cognitive-services"></a>比较 OpenCV 和认知服务

> |功能|Microsoft 认知服务|OpenCV|
> |---------------------|--------|------|
> |易于在 Windows|是|否 |
> |体系结构支持|ARM、x86、x64 | ARM、x86、x64|
> |面部识别和跟踪| 是 | 是|
> |情感识别| 是 | 是|
> |3D 重构和映射| 否 | 是|
> |内容检测| 检测常规功能而不是特定对象 | 是|
> |视频稳定| 是 | 是|
> |动作检测| 是 | 是|
> |社区| 认知服务在多个行业和一些热门网站中有许多活跃用户，包括 how-old.net celebslike.me | OpenCV 是一个非常受欢迎的开源项目;成千上万的人为它贡献并维护了它|
> |文档| 认知服务具有全面的清晰文档 | 可以联机使用许多示例，但每个示例都是由不同的人编写的，因此，可能会不一致。|
> |免费| 是的， [此处](https://azure.microsoft.com/pricing/details/cognitive-services/) (详细信息)  | 是|
> |性能| 所有操作和 API 调用都需要访问云中的数据 | 所有算法经过优化和本地，使用 c + + 而不是 Python 会进一步提高速度|
> |支持的相机/硬件| 任何 USB 或嵌入式相机 | 任何 USB 或嵌入式相机|
> |支持的语言/框架| C#、UWP | C/c + +、Python、Java、c #、UWP|
> |启动时间| 用户可以直接在文档中使用代码示例和直观的 Api | OpenCV 的强大功能和灵活性意味着它还需要大量配置和代码来执行复杂的操作|
> |链接| [示例程序](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CognitiveServicesExample) | [示例程序](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/OpenCVExample) |
> |    |   [认知服务网站](https://azure.microsoft.com/services/cognitive-services/) |  [OpenCV 网站](http://opencv.org/)
