---
title: 创建单元测试
author: bfjelds
ms.author: bfjelds
ms.date: 10/08/2018
ms.topic: article
description: 了解多个硬件供应商的芯片 (Soc) 上的 IoT Core 支持的单元测试。
keywords: windows iot，单元测试，UWP
ms.openlocfilehash: aebe60bebad1062d19142e5434cd7277801b3e4f
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782879"
---
# <a name="developing-unit-tests"></a><span data-ttu-id="7bc03-104">开发单元测试</span><span class="sxs-lookup"><span data-stu-id="7bc03-104">Developing unit tests</span></span>
<span data-ttu-id="7bc03-105">了解 Windows 10 IoT Core 支持的 UWP 单元测试。</span><span class="sxs-lookup"><span data-stu-id="7bc03-105">Learn about UWP unit testing supported on Windows 10 IoT Core.</span></span>

## <a name="uwp-unit-tests"></a><span data-ttu-id="7bc03-106">UWP 单元测试</span><span class="sxs-lookup"><span data-stu-id="7bc03-106">UWP Unit Tests</span></span>
___

<span data-ttu-id="7bc03-107">单元测试为应用开发人员提供重要的保护和验证。</span><span class="sxs-lookup"><span data-stu-id="7bc03-107">Unit tests provide vital protection and validation for app developers.</span></span>  <span data-ttu-id="7bc03-108">Visual Studio 15.6 在新的测试平台中添加了对 Windows 10 IoT Core 的支持。</span><span class="sxs-lookup"><span data-stu-id="7bc03-108">Visual Studio 15.6 added support for Windows 10 IoT Core in its new test platform.</span></span>  <span data-ttu-id="7bc03-109">通过此新支持，可以创建可作为持续集成生成的一部分或直接从 Visual Studio 中执行的 UWP 功能的单元测试。</span><span class="sxs-lookup"><span data-stu-id="7bc03-109">With this new support, it is possible to create unit tests for UWP functionality that can execute as part of a Continuous Integration build or directly from Visual Studio.</span></span>


### <a name="create-new-unit-test-project"></a><span data-ttu-id="7bc03-110">创建新的单元测试项目</span><span class="sxs-lookup"><span data-stu-id="7bc03-110">Create new unit test project</span></span>
___

1. <span data-ttu-id="7bc03-111">打开 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7bc03-111">Open Visual Studio</span></span>

2. <span data-ttu-id="7bc03-112">创建新的单元测试项目 ![ 安装应用](../media/UnitTests/newproject.png)</span><span class="sxs-lookup"><span data-stu-id="7bc03-112">Create a new unit test project ![Install App](../media/UnitTests/newproject.png)</span></span>

3. <span data-ttu-id="7bc03-113">更新 UnitTest.cs 以包含测试代码</span><span class="sxs-lookup"><span data-stu-id="7bc03-113">Update UnitTest.cs to include your test code</span></span>
   ```C#
   namespace UnitTestProject1
   {
    [TestClass]
    public class UnitTest1
    {
        [TestMethod]
        public void TestMethod1()
        {
            // test code here
        }
    }
   }
   ```


### <a name="remotely-run-unit-test-on-windows-10-iot-core-device"></a><span data-ttu-id="7bc03-114">在 Windows 10 IoT Core 设备上远程运行单元测试</span><span class="sxs-lookup"><span data-stu-id="7bc03-114">Remotely run unit test on Windows 10 IoT Core device</span></span>
___

1. <span data-ttu-id="7bc03-115">打开 Visual Studio 测试资源管理器 (测试 > Windows > 测试资源管理器) 。</span><span class="sxs-lookup"><span data-stu-id="7bc03-115">Open the Visual Studio Test Explorer (Test > Windows > Test Explorer).</span></span>
 <span data-ttu-id="7bc03-116">![测试资源管理器](../media/UnitTests/show-test-explorer.png)</span><span class="sxs-lookup"><span data-stu-id="7bc03-116">![Test Explorer](../media/UnitTests/show-test-explorer.png)</span></span>

1. <span data-ttu-id="7bc03-117">若要运行测试部署，你的项目必须采用与 (专门使用通用身份验证和远程计算机) 配置 UWP 应用相同的方式进行配置。</span><span class="sxs-lookup"><span data-stu-id="7bc03-117">For test deployment to work, your project must be configured in the same way UWP apps are configured (specifically using Universal Authentication and Remote Machine).</span></span>  <span data-ttu-id="7bc03-118">有关详细信息，请参阅 [使用 Visual Studio 部署应用](../develop-your-app/appdeployment.md) 。</span><span class="sxs-lookup"><span data-stu-id="7bc03-118">See [Deploy an App with Visual Studio](../develop-your-app/appdeployment.md) for specifics.</span></span>

1. <span data-ttu-id="7bc03-119">若要远程运行单元测试，可以使用测试资源管理器，右键单击所需的 TestMethod，然后选择 "运行/调试选定的测试" " ![ 测试资源管理器"](../media/UnitTests/test-explorer.png)</span><span class="sxs-lookup"><span data-stu-id="7bc03-119">To remotely run a unit test, you can use the Test Explorer and right-click the desired TestMethod and selecting Run/Debug Selected Tests ![Test Explorer](../media/UnitTests/test-explorer.png)</span></span>

1. <span data-ttu-id="7bc03-120">若要远程运行或调试所有单元测试，可以使用测试 > 运行或测试 > 调试 ![ 测试资源管理器 ](../media/UnitTests/run-tests.png)
  ![ 测试资源管理器](../media/UnitTests/debug-tests.png)</span><span class="sxs-lookup"><span data-stu-id="7bc03-120">To remotely run or debug all unit tests, you can use Test > Run or Test > Debug ![Test Explorer](../media/UnitTests/run-tests.png)
 ![Test Explorer](../media/UnitTests/debug-tests.png)</span></span>
   

### <a name="configure-unit-tests-as-part-of-a-continuous-integration-build"></a><span data-ttu-id="7bc03-121">将单元测试配置为持续集成生成的一部分</span><span class="sxs-lookup"><span data-stu-id="7bc03-121">Configure unit tests as part of a Continuous Integration build</span></span>
___

<span data-ttu-id="7bc03-122">Visual Studio 团队创建了一个精彩的博客文章，其中展示了如何将 Windows 10 IoT 核心单元测试合并到 VSTS 生成： [DevOps For iot With Win10 IoT Core、UWP 和 VSTS](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)</span><span class="sxs-lookup"><span data-stu-id="7bc03-122">The Visual Studio team has created a great blog post showing how to incorporate Windows 10 IoT Core unit tests into a VSTS build: [DevOps for IoT with Win10 IoT Core, UWP, and VSTS](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)</span></span>

