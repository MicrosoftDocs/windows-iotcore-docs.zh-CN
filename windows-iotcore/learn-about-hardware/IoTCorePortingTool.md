---
title: Windows 10 IoT Core API 移植工具
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Windows 10 IoT Core API 移植工具来估算迁移成本。
keywords: windows iot，API 移植工具，API 移植，二进制文件
ms.openlocfilehash: 5d7ffa00fb6ac9739b69227d5ed3248d7c466b7b
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655785"
---
# <a name="windows-10-iot-core-api-porting-tool"></a><span data-ttu-id="37e38-104">Windows 10 IoT Core API 移植工具</span><span class="sxs-lookup"><span data-stu-id="37e38-104">Windows 10 IoT Core API Porting Tool</span></span>

<span data-ttu-id="37e38-105">Windows 10 IoT Core 仅支持 Windows 的各种早期版本中提供的 Win32 和 .NET API 外围应用的子集。</span><span class="sxs-lookup"><span data-stu-id="37e38-105">Windows 10 IoT Core only supports a subset of the Win32 and .NET API surface area available on various prior versions of Windows.</span></span> <span data-ttu-id="37e38-106">此工具将扫描您的二进制文件，并向您提供这些二进制文件使用的 Api 的报告，并提供可能的替换建议。</span><span class="sxs-lookup"><span data-stu-id="37e38-106">This tool will scan your binaries and give you a report of the APIs these binaries use that aren't available and give suggestions for possible replacements.</span></span> <span data-ttu-id="37e38-107">这既有助于估计到 IoT 核心的端口成本，也有助于你的工作方式。</span><span class="sxs-lookup"><span data-stu-id="37e38-107">This will both help with estimating the cost of a port to IoT Core as well as help you along the way.</span></span>


## <a name="usage"></a><span data-ttu-id="37e38-108">使用情况</span><span class="sxs-lookup"><span data-stu-id="37e38-108">Usage</span></span>

<span data-ttu-id="37e38-109">Windows 10 IoT Core API 移植工具可在 " [ms-iot-实用程序](https://github.com/ms-iot/iot-utilities) " GitHub 存储库中找到。</span><span class="sxs-lookup"><span data-stu-id="37e38-109">The Windows 10 IoT Core API Porting Tool can be found in the [ms-iot/iot-utilities](https://github.com/ms-iot/iot-utilities) GitHub repository.</span></span>  <span data-ttu-id="37e38-110">下载 [存储库 zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) ，并将 IoTAPIPortingTool 文件夹复制到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="37e38-110">Download the [repository zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) and copy the IoTAPIPortingTool folder to your local machine.</span></span>  <span data-ttu-id="37e38-111">在 Visual Studio 2017 中打开 **IoTAPIPortingTool** 并生成项目。</span><span class="sxs-lookup"><span data-stu-id="37e38-111">Open **IoTAPIPortingTool.sln** in Visual Studio 2017 and build the project.</span></span>  <span data-ttu-id="37e38-112">这将生成 `IotAPIPortingTool.exe`。</span><span class="sxs-lookup"><span data-stu-id="37e38-112">This will generate `IotAPIPortingTool.exe`.</span></span>

<span data-ttu-id="37e38-113">可以通过运行来使用该工具 `IoTAPIPortingTool.exe <Application path> [-os]` 。</span><span class="sxs-lookup"><span data-stu-id="37e38-113">You can use the tool by running `IoTAPIPortingTool.exe <Application path> [-os]`.</span></span>

*  <span data-ttu-id="37e38-114">`<Application path>` 用于迁移工具的应用程序的 exe</span><span class="sxs-lookup"><span data-stu-id="37e38-114">`<Application path>` exe of application that porting tool is used for</span></span>

*  <span data-ttu-id="37e38-115">`-os` 如果你不打算使用 UWP，则应该指定。</span><span class="sxs-lookup"><span data-stu-id="37e38-115">`-os` should be specified if you are not planning to use UWP.</span></span>  <span data-ttu-id="37e38-116">默认情况下，该工具会针对 Windows UWP 平台验证你的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="37e38-116">By default, the tool validates your binaries against the Windows UWP platform.</span></span>

> [!NOTE]
> <span data-ttu-id="37e38-117">必须从 Visual Studio 开发人员命令提示运行 IoTAPIPortingTool.exe。</span><span class="sxs-lookup"><span data-stu-id="37e38-117">IoTAPIPortingTool.exe must be run from a Visual Studio Developer Command Prompt.</span></span> <span data-ttu-id="37e38-118">需要导航到包含该 IotAPIPortingTool.exe 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="37e38-118">You need to navigate to the folder that contains the IotAPIPortingTool.exe.</span></span>
```
        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os
```
## <a name="output"></a><span data-ttu-id="37e38-119">输出</span><span class="sxs-lookup"><span data-stu-id="37e38-119">Output</span></span>

<span data-ttu-id="37e38-120">此工具将在包含的同一文件夹中 (csv) 文件生成逗号分隔值 `IotAPIPortingTool.exe` 。</span><span class="sxs-lookup"><span data-stu-id="37e38-120">The tool will generate a comma-separated values (csv) file in same folder that contains the `IotAPIPortingTool.exe`.</span></span> <span data-ttu-id="37e38-121">该文件的名称为 `IoTAPIPortingTool.csv` (或者， `IoTAPIPortingToolOS.csv` 如果指定了-os) ，则在命令行上有一个摘要。</span><span class="sxs-lookup"><span data-stu-id="37e38-121">The file is named `IoTAPIPortingTool.csv` (or, `IoTAPIPortingToolOS.csv` if -os is specified) and a summary will be on the command line.</span></span> <span data-ttu-id="37e38-122">`.csv`在 Excel 中打开文件以分析完整的输出。</span><span class="sxs-lookup"><span data-stu-id="37e38-122">Open the `.csv` file in Excel to analyze the complete output.</span></span>
