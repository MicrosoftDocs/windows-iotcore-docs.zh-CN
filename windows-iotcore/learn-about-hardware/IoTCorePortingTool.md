---
title: Windows 10 IoT 核心版API 移植工具
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Windows 10 IoT 核心版 API 移植工具估算移植成本。
keywords: windows iot， API 移植工具， API 移植， 二进制文件
ms.openlocfilehash: 0b6631c3ee0afe5c60a972bcf69999e39f0d60dc
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229634"
---
# <a name="windows-10-iot-core-api-porting-tool"></a><span data-ttu-id="2a2f6-104">Windows 10 IoT 核心版API 移植工具</span><span class="sxs-lookup"><span data-stu-id="2a2f6-104">Windows 10 IoT Core API Porting Tool</span></span>

<span data-ttu-id="2a2f6-105">Windows 10 IoT 核心版仅支持各种早期版本的 Windows 上提供的 Win32 和 .NET API 图面Windows。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-105">Windows 10 IoT Core only supports a subset of the Win32 and .NET API surface area available on various prior versions of Windows.</span></span> <span data-ttu-id="2a2f6-106">此工具将扫描二进制文件，并报告这些二进制文件使用的不可用 API，并针对可能的替换提供建议。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-106">This tool will scan your binaries and give you a report of the APIs these binaries use that aren't available and give suggestions for possible replacements.</span></span> <span data-ttu-id="2a2f6-107">这两种方法都有助于估算 IoT 核心的端口成本，还有助于你完成这一步。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-107">This will both help with estimating the cost of a port to IoT Core as well as help you along the way.</span></span>


## <a name="usage"></a><span data-ttu-id="2a2f6-108">使用情况</span><span class="sxs-lookup"><span data-stu-id="2a2f6-108">Usage</span></span>

<span data-ttu-id="2a2f6-109">可以在Windows 10 IoT 核心版的[ms-iot/iot-utilities](https://github.com/ms-iot/iot-utilities) GitHub工具。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-109">The Windows 10 IoT Core API Porting Tool can be found in the [ms-iot/iot-utilities](https://github.com/ms-iot/iot-utilities) GitHub repository.</span></span>  <span data-ttu-id="2a2f6-110">下载 [存储库 zip，](https://github.com/ms-iot/iot-utilities/archive/master.zip) 将 IoTAPIPortingTool 文件夹复制到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-110">Download the [repository zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) and copy the IoTAPIPortingTool folder to your local machine.</span></span>  <span data-ttu-id="2a2f6-111">在 2017 Visual Studio打开 **IoTAPIPortingTool.sln** 并生成项目。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-111">Open **IoTAPIPortingTool.sln** in Visual Studio 2017 and build the project.</span></span>  <span data-ttu-id="2a2f6-112">这将生成 `IotAPIPortingTool.exe`。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-112">This will generate `IotAPIPortingTool.exe`.</span></span>

<span data-ttu-id="2a2f6-113">可以通过运行 来使用该工具 `IoTAPIPortingTool.exe <Application path> [-os]` 。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-113">You can use the tool by running `IoTAPIPortingTool.exe <Application path> [-os]`.</span></span>

*  <span data-ttu-id="2a2f6-114">`<Application path>` 用于移植工具的应用程序的 exe</span><span class="sxs-lookup"><span data-stu-id="2a2f6-114">`<Application path>` exe of application that porting tool is used for</span></span>

*  <span data-ttu-id="2a2f6-115">`-os` 如果打算使用 UWP，应指定 。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-115">`-os` should be specified if you are not planning to use UWP.</span></span>  <span data-ttu-id="2a2f6-116">默认情况下，该工具根据 UWP 平台Windows二进制文件。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-116">By default, the tool validates your binaries against the Windows UWP platform.</span></span>

> [!NOTE]
> <span data-ttu-id="2a2f6-117">IoTAPIPortingTool.exe必须运行自 Visual Studio 开发人员命令提示。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-117">IoTAPIPortingTool.exe must be run from a Visual Studio Developer Command Prompt.</span></span> <span data-ttu-id="2a2f6-118">需要导航到包含该文件夹IotAPIPortingTool.exe。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-118">You need to navigate to the folder that contains the IotAPIPortingTool.exe.</span></span>
```
        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os
```
## <a name="output"></a><span data-ttu-id="2a2f6-119">输出</span><span class="sxs-lookup"><span data-stu-id="2a2f6-119">Output</span></span>

<span data-ttu-id="2a2f6-120">该工具将在包含 的同 (csv) 文件中生成逗号分隔值 `IotAPIPortingTool.exe` 。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-120">The tool will generate a comma-separated values (csv) file in same folder that contains the `IotAPIPortingTool.exe`.</span></span> <span data-ttu-id="2a2f6-121">该文件名为 (，或者，如果 `IoTAPIPortingTool.csv` 指定了 `IoTAPIPortingToolOS.csv` -os) 则摘要将位于命令行上。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-121">The file is named `IoTAPIPortingTool.csv` (or, `IoTAPIPortingToolOS.csv` if -os is specified) and a summary will be on the command line.</span></span> <span data-ttu-id="2a2f6-122">打开 `.csv` 文件Excel以分析完整输出。</span><span class="sxs-lookup"><span data-stu-id="2a2f6-122">Open the `.csv` file in Excel to analyze the complete output.</span></span>
