---
title: 创建单元测试
author: bfjelds
ms.author: bfjelds
ms.date: 10/08/2018
ms.topic: article
description: 了解有关 IoT Core 支持单元测试。
keywords: windows iot，单元测试、 UWP
ms.openlocfilehash: 0a54ad7ffa3065353045f0e2f81306a1a1e0ac13
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510880"
---
# <a name="developing-unit-tests"></a><span data-ttu-id="919ea-104">开发单元测试</span><span class="sxs-lookup"><span data-stu-id="919ea-104">Developing unit tests</span></span>
<span data-ttu-id="919ea-105">了解 UWP 单元测试在 Windows 10 IoT 核心版上受支持。</span><span class="sxs-lookup"><span data-stu-id="919ea-105">Learn about UWP unit testing supported on Windows 10 IoT Core.</span></span>

## <a name="uwp-unit-tests"></a><span data-ttu-id="919ea-106">UWP 单元测试</span><span class="sxs-lookup"><span data-stu-id="919ea-106">UWP Unit Tests</span></span>
___

<span data-ttu-id="919ea-107">单元测试提供了重要的保护和验证应用程序开发人员。</span><span class="sxs-lookup"><span data-stu-id="919ea-107">Unit tests provide vital protection and validation for app developers.</span></span>  <span data-ttu-id="919ea-108">Visual Studio 15.6 版在其新的测试平台中添加对 Windows 10 IoT Core 的支持。</span><span class="sxs-lookup"><span data-stu-id="919ea-108">Visual Studio 15.6 added support for Windows 10 IoT Core in its new test platform.</span></span>  <span data-ttu-id="919ea-109">利用此新的支持，就可以创建 UWP 功能的一部分，或直接从 Visual Studio 的持续集成生成可执行单元测试。</span><span class="sxs-lookup"><span data-stu-id="919ea-109">With this new support, it is possible to create unit tests for UWP functionality that can execute as part of a Continuous Integration build or directly from Visual Studio.</span></span>


### <a name="create-new-unit-test-project"></a><span data-ttu-id="919ea-110">创建新的单元测试项目</span><span class="sxs-lookup"><span data-stu-id="919ea-110">Create new unit test project</span></span>
___

1. <span data-ttu-id="919ea-111">打开 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="919ea-111">Open Visual Studio</span></span>

2. <span data-ttu-id="919ea-112">创建新的单元测试项目![安装应用](../media/UnitTests/newproject.png)</span><span class="sxs-lookup"><span data-stu-id="919ea-112">Create a new unit test project ![Install App](../media/UnitTests/newproject.png)</span></span>

3. <span data-ttu-id="919ea-113">更新 UnitTest.cs 包含测试代码</span><span class="sxs-lookup"><span data-stu-id="919ea-113">Update UnitTest.cs to include your test code</span></span>
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


### <a name="remotely-run-unit-test-on-windows-10-iot-core-device"></a><span data-ttu-id="919ea-114">在 Windows 10 IoT Core 设备上远程运行单元测试</span><span class="sxs-lookup"><span data-stu-id="919ea-114">Remotely run unit test on Windows 10 IoT Core device</span></span>
___

1. <span data-ttu-id="919ea-115">打开 Visual Studio 测试资源管理器 (测试 > Windows > 测试资源管理器)。</span><span class="sxs-lookup"><span data-stu-id="919ea-115">Open the Visual Studio Test Explorer (Test > Windows > Test Explorer).</span></span>
 ![测试资源管理器](../media/UnitTests/show-test-explorer.png)

1. <span data-ttu-id="919ea-117">若要运行的测试部署，你的项目必须配置与 UWP 应用配置 （特别使用通用身份验证和远程计算机） 相同的方式。</span><span class="sxs-lookup"><span data-stu-id="919ea-117">For test deployment to work, your project must be configured in the same way UWP apps are configured (specifically using Universal Authentication and Remote Machine).</span></span>  <span data-ttu-id="919ea-118">请参阅[使用 Visual Studio 部署应用](../develop-your-app/appdeployment.md)了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="919ea-118">See [Deploy an App with Visual Studio](../develop-your-app/appdeployment.md) for specifics.</span></span>

1. <span data-ttu-id="919ea-119">若要远程运行单元测试，可以使用测试资源管理器和右键单击所需的 TestMethod 并选择运行/调试所选测试![测试资源管理器](../media/UnitTests/test-explorer.png)</span><span class="sxs-lookup"><span data-stu-id="919ea-119">To remotely run a unit test, you can use the Test Explorer and right clicking the desired TestMethod and selecting Run/Debug Selected Tests ![Test Explorer](../media/UnitTests/test-explorer.png)</span></span>

1. <span data-ttu-id="919ea-120">若要远程运行或调试的所有单元测试，可以使用测试 > 运行或测试 > 都调试![测试资源管理器](../media/UnitTests/run-tests.png)
 ![测试资源管理器](../media/UnitTests/debug-tests.png)</span><span class="sxs-lookup"><span data-stu-id="919ea-120">To remotely run or debug all unit tests, you can use Test > Run or Test > Debug ![Test Explorer](../media/UnitTests/run-tests.png)
 ![Test Explorer](../media/UnitTests/debug-tests.png)</span></span>
   

### <a name="configure-unit-tests-as-part-of-a-continuous-integration-build"></a><span data-ttu-id="919ea-121">配置单元测试作为持续集成生成的一部分</span><span class="sxs-lookup"><span data-stu-id="919ea-121">Configure unit tests as part of a Continuous Integration build</span></span>
___

<span data-ttu-id="919ea-122">Visual Studio 团队已创建了显示如何将 Windows 10 IoT Core 单元测试合并到 VSTS 生成出色的博客文章：[Win10 IoT 核心版、 UWP、 与 VSTS IoT 的 DevOps](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)</span><span class="sxs-lookup"><span data-stu-id="919ea-122">The Visual Studio team has created a great blog post showing how to incorporate Windows 10 IoT Core unit tests into a VSTS build: [DevOps for IoT with Win10 IoT Core, UWP, and VSTS](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)</span></span>

