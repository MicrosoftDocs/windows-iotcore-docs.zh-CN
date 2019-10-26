---
title: Windows 10 IoT Core API 移植工具
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows 10 IoT Core API 移植工具来估算迁移成本。
keywords: windows iot，API 移植工具，API 移植，二进制文件
ms.openlocfilehash: 1a7acf4a027ef19a8920c7b10f6be61657d2d76a
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918089"
---
# <a name="windows-10-iot-core-api-porting-tool"></a><span data-ttu-id="8e40f-104">Windows 10 IoT Core API 移植工具</span><span class="sxs-lookup"><span data-stu-id="8e40f-104">Windows 10 IoT Core API Porting Tool</span></span>

<span data-ttu-id="8e40f-105">Windows 10 IoT Core 仅支持 Windows 的各种早期版本中提供的 Win32 和 .Net API 外围应用的子集。</span><span class="sxs-lookup"><span data-stu-id="8e40f-105">Windows 10 IoT Core only supports a subset of the Win32 and .Net API surface area available on various prior versions of Windows.</span></span> <span data-ttu-id="8e40f-106">此工具将扫描您的二进制文件，并向您提供这些二进制文件使用的 Api 的报告，并提供可能的替换建议。</span><span class="sxs-lookup"><span data-stu-id="8e40f-106">This tool will scan your binaries and give you a report of the APIs these binaries use that aren't available and give suggestions for possible replacements.</span></span> <span data-ttu-id="8e40f-107">这既有助于估计到 IoT 核心的端口成本，也有助于你的工作方式。</span><span class="sxs-lookup"><span data-stu-id="8e40f-107">This will both help with estimating the cost of a port to IoT Core as well as help you along the way.</span></span>


## <a name="usage"></a><span data-ttu-id="8e40f-108">Usage</span><span class="sxs-lookup"><span data-stu-id="8e40f-108">Usage</span></span>

<span data-ttu-id="8e40f-109">Windows 10 IoT 核心版 API 移植工具可在 [ms-iot/iot-utilities](https://github.com/ms-iot/iot-utilities) github 存储库中找到。</span><span class="sxs-lookup"><span data-stu-id="8e40f-109">The Windows 10 IoT Core API Porting Tool can be found in the [ms-iot/iot-utilities](https://github.com/ms-iot/iot-utilities) github repository.</span></span>  <span data-ttu-id="8e40f-110">下载[存储库 zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) ，并将 IoTAPIPortingTool 文件夹复制到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="8e40f-110">Download the [repository zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) and copy the IoTAPIPortingTool folder to your local machine.</span></span>  <span data-ttu-id="8e40f-111">在 Visual Studio 2017 中打开**IoTAPIPortingTool**并生成项目。</span><span class="sxs-lookup"><span data-stu-id="8e40f-111">Open **IoTAPIPortingTool.sln** in Visual Studio 2017 and build the project.</span></span>  <span data-ttu-id="8e40f-112">这将生成 `IotAPIPortingTool.exe`。</span><span class="sxs-lookup"><span data-stu-id="8e40f-112">This will generate `IotAPIPortingTool.exe`.</span></span>

<span data-ttu-id="8e40f-113">可通过运行 `IoTAPIPortingTool.exe <Application path> [-os]` 使用该工具。</span><span class="sxs-lookup"><span data-stu-id="8e40f-113">You can use the tool by running `IoTAPIPortingTool.exe <Application path> [-os]`.</span></span>

*  <span data-ttu-id="8e40f-114">用于迁移工具的应用程序 `<Application path>` exe</span><span class="sxs-lookup"><span data-stu-id="8e40f-114">`<Application path>` exe of application that porting tool is used for</span></span>

*  <span data-ttu-id="8e40f-115">如果你不计划使用 UWP，应指定 `-os`。</span><span class="sxs-lookup"><span data-stu-id="8e40f-115">`-os` should be specified if you are not planning to use UWP.</span></span>  <span data-ttu-id="8e40f-116">默认情况下，该工具针对 WindowsUWP 平台验证你的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="8e40f-116">By default, the tool validates your binaries against the Windows UWP platform.</span></span>

> [!NOTE] 
> <span data-ttu-id="8e40f-117">必须从 Visual Studio 开发人员命令提示中运行 IoTAPIPortingTool。</span><span class="sxs-lookup"><span data-stu-id="8e40f-117">IoTAPIPortingTool.exe must be run from a Visual Studio Developer Command Prompt.</span></span> <span data-ttu-id="8e40f-118">需要导航到包含 IotAPIPortingTool 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="8e40f-118">You need to navigate to the folder that contains the IotAPIPortingTool.exe.</span></span> 

        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os 

## <a name="output"></a><span data-ttu-id="8e40f-119">输出</span><span class="sxs-lookup"><span data-stu-id="8e40f-119">Output</span></span>

<span data-ttu-id="8e40f-120">此工具将在包含 `IotAPIPortingTool.exe`的同一文件夹中生成一个逗号分隔值（csv）文件。</span><span class="sxs-lookup"><span data-stu-id="8e40f-120">The tool will generate a comma separated values (csv) file in same folder that contains the `IotAPIPortingTool.exe`.</span></span> <span data-ttu-id="8e40f-121">该文件的名称为 `IoTAPIPortingTool.csv` （或者，如果指定了-os，则 `IoTAPIPortingToolOS.csv`），并在命令行上有一个摘要。</span><span class="sxs-lookup"><span data-stu-id="8e40f-121">The file is named `IoTAPIPortingTool.csv` (or, `IoTAPIPortingToolOS.csv` if -os is specified) and a summary will be on the command line.</span></span> <span data-ttu-id="8e40f-122">在 Excel 中打开 `.csv` 文件来分析完整输出。</span><span class="sxs-lookup"><span data-stu-id="8e40f-122">Open the `.csv` file in Excel to analyze the complete output.</span></span>
