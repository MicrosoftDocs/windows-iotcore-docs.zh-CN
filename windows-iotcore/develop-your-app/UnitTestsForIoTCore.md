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
# <a name="developing-unit-tests"></a>开发单元测试
了解 UWP 单元测试在 Windows 10 IoT 核心版上受支持。

## <a name="uwp-unit-tests"></a>UWP 单元测试
___

单元测试提供了重要的保护和验证应用程序开发人员。  Visual Studio 15.6 版在其新的测试平台中添加对 Windows 10 IoT Core 的支持。  利用此新的支持，就可以创建 UWP 功能的一部分，或直接从 Visual Studio 的持续集成生成可执行单元测试。


### <a name="create-new-unit-test-project"></a>创建新的单元测试项目
___

1. 打开 Visual Studio

2. 创建新的单元测试项目![安装应用](../media/UnitTests/newproject.png)

3. 更新 UnitTest.cs 包含测试代码
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


### <a name="remotely-run-unit-test-on-windows-10-iot-core-device"></a>在 Windows 10 IoT Core 设备上远程运行单元测试
___

1. 打开 Visual Studio 测试资源管理器 (测试 > Windows > 测试资源管理器)。
 ![测试资源管理器](../media/UnitTests/show-test-explorer.png)

1. 若要运行的测试部署，你的项目必须配置与 UWP 应用配置 （特别使用通用身份验证和远程计算机） 相同的方式。  请参阅[使用 Visual Studio 部署应用](../develop-your-app/appdeployment.md)了解详细信息。

1. 若要远程运行单元测试，可以使用测试资源管理器和右键单击所需的 TestMethod 并选择运行/调试所选测试![测试资源管理器](../media/UnitTests/test-explorer.png)

1. 若要远程运行或调试的所有单元测试，可以使用测试 > 运行或测试 > 都调试![测试资源管理器](../media/UnitTests/run-tests.png)
 ![测试资源管理器](../media/UnitTests/debug-tests.png)
   

### <a name="configure-unit-tests-as-part-of-a-continuous-integration-build"></a>配置单元测试作为持续集成生成的一部分
___

Visual Studio 团队已创建了显示如何将 Windows 10 IoT Core 单元测试合并到 VSTS 生成出色的博客文章：[Win10 IoT 核心版、 UWP、 与 VSTS IoT 的 DevOps](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)

