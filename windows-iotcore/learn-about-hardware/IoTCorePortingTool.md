---
title: Windows 10 IoT Core API 移植工具
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows 10 IoT Core API 移植工具来估计迁移成本。
keywords: windows iot，API 移植工具、 API 移植、 二进制文件
ms.openlocfilehash: 56ca0d57752f000bf9e908fd32f514c3ae3264e5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510795"
---
# <a name="windows-10-iot-core-api-porting-tool"></a><span data-ttu-id="b7595-104">Windows 10 IoT Core API 移植工具</span><span class="sxs-lookup"><span data-stu-id="b7595-104">Windows 10 IoT Core API Porting Tool</span></span>

<span data-ttu-id="b7595-105">Windows 10 IoT 核心版仅支持在各种以前版本的 Windows 上的 Win32 和.Net API 表面区域的子集。</span><span class="sxs-lookup"><span data-stu-id="b7595-105">Windows 10 IoT Core only supports a subset of the Win32 and .Net API surface area available on various prior versions of Windows.</span></span> <span data-ttu-id="b7595-106">此工具将扫描您的二进制文件，并为您提供的 Api 使用这些二进制文件不可用，并且提供有关可能的替换建议的报告。</span><span class="sxs-lookup"><span data-stu-id="b7595-106">This tool will scan your binaries and give you a report of the APIs these binaries use that aren't available and give suggestions for possible replacements.</span></span> <span data-ttu-id="b7595-107">这将同时帮助估算成本 IoT 核心版的端口，以及帮助你在此过程。</span><span class="sxs-lookup"><span data-stu-id="b7595-107">This will both help with estimating the cost of a port to IoT Core as well as help you along the way.</span></span>


## <a name="usage"></a><span data-ttu-id="b7595-108">用法</span><span class="sxs-lookup"><span data-stu-id="b7595-108">Usage</span></span>

<span data-ttu-id="b7595-109">Windows 10 IoT 核心版 API 移植工具可在 [ms-iot/iot-utilities](https://github.com/ms-iot/iot-utilities) github 存储库中找到。</span><span class="sxs-lookup"><span data-stu-id="b7595-109">The Windows 10 IoT Core API Porting Tool can be found in the [ms-iot/iot-utilities](https://github.com/ms-iot/iot-utilities) github repository.</span></span>  <span data-ttu-id="b7595-110">下载[存储库 zip](https://github.com/ms-iot/iot-utilities/archive/master.zip)将 IoTAPIPortingTool 文件夹复制到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="b7595-110">Download the [repository zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) and copy the IoTAPIPortingTool folder to your local machine.</span></span>  <span data-ttu-id="b7595-111">打开**IoTAPIPortingTool.sln**在 Visual Studio 2017 并生成项目。</span><span class="sxs-lookup"><span data-stu-id="b7595-111">Open **IoTAPIPortingTool.sln** in Visual Studio 2017 and build the project.</span></span>  <span data-ttu-id="b7595-112">这将生成 `IotAPIPortingTool.exe`。</span><span class="sxs-lookup"><span data-stu-id="b7595-112">This will generate `IotAPIPortingTool.exe`.</span></span>

<span data-ttu-id="b7595-113">可通过运行 `IoTAPIPortingTool.exe <Application path> [-os]` 使用该工具。</span><span class="sxs-lookup"><span data-stu-id="b7595-113">You can use the tool by running `IoTAPIPortingTool.exe <Application path> [-os]`.</span></span>

*  `<Application path>` <span data-ttu-id="b7595-114">迁移工具用于应用程序的 exe</span><span class="sxs-lookup"><span data-stu-id="b7595-114">exe of application that porting tool is used for</span></span>

*  `-os` <span data-ttu-id="b7595-115">应指定是否您不打算使用 UWP。</span><span class="sxs-lookup"><span data-stu-id="b7595-115">should be specified if you are not planning to use UWP.</span></span>  <span data-ttu-id="b7595-116">默认情况下，该工具针对 WindowsUWP 平台验证你的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="b7595-116">By default, the tool validates your binaries against the Windows UWP platform.</span></span>

> [!NOTE] 
> <span data-ttu-id="b7595-117">必须从 Visual Studio 开发人员命令提示运行 IoTAPIPortingTool.exe。</span><span class="sxs-lookup"><span data-stu-id="b7595-117">IoTAPIPortingTool.exe must be run from a Visual Studio Developer Command Prompt.</span></span> <span data-ttu-id="b7595-118">您需要导航到包含 IotAPIPortingTool.exe 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="b7595-118">You need to navigate to the folder that contains the IotAPIPortingTool.exe.</span></span> 

        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os 

## <a name="output"></a><span data-ttu-id="b7595-119">输出</span><span class="sxs-lookup"><span data-stu-id="b7595-119">Output</span></span>

<span data-ttu-id="b7595-120">此工具将在包含的相同文件夹中生成逗号分隔的值 (csv) 文件`IotAPIPortingTool.exe`。</span><span class="sxs-lookup"><span data-stu-id="b7595-120">The tool will generate a comma separated values (csv) file in same folder that contains the `IotAPIPortingTool.exe`.</span></span> <span data-ttu-id="b7595-121">将该文件命名`IoTAPIPortingTool.csv`(或者，`IoTAPIPortingToolOS.csv`如果指定-os) 和摘要将在命令行上。</span><span class="sxs-lookup"><span data-stu-id="b7595-121">The file is named `IoTAPIPortingTool.csv` (or, `IoTAPIPortingToolOS.csv` if -os is specified) and a summary will be on the command line.</span></span> <span data-ttu-id="b7595-122">在 Excel 中打开 `.csv` 文件来分析完整输出。</span><span class="sxs-lookup"><span data-stu-id="b7595-122">Open the `.csv` file in Excel to analyze the complete output.</span></span>
