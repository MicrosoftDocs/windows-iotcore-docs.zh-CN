---
title: 创建单元测试
author: bfjelds
ms.author: bfjelds
ms.date: 10/08/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解多个硬件供应商的芯片 (Soc) 上的 IoT Core 支持的单元测试。
keywords: windows iot，单元测试，UWP
ms.openlocfilehash: ed905cd83030ac091be84c3f328372e3c80a7feb
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228983"
---
# <a name="developing-unit-tests"></a>开发单元测试
了解 Windows 10 IoT 核心版上支持的 UWP 单元测试。

## <a name="uwp-unit-tests"></a>UWP 单元测试
___

单元测试为应用开发人员提供重要的保护和验证。  Visual Studio 15.6 在新的测试平台中添加了对 Windows 10 IoT 核心版的支持。  利用这一新的支持，可以创建 UWP 功能的单元测试，该功能可作为持续集成生成的一部分或直接从 Visual Studio 执行。


### <a name="create-new-unit-test-project"></a>创建新的单元测试项目
___

1. 打开 Visual Studio

2. 创建新的单元测试项目 ![ 安装应用](../media/UnitTests/newproject.png)

3. 更新 UnitTest 以包含测试代码
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


### <a name="remotely-run-unit-test-on-windows-10-iot-core-device"></a>在 Windows 10 IoT 核心版设备上远程运行单元测试
___

1. 打开 Visual Studio 测试资源管理器 (测试 > Windows > 测试资源管理器) 。
 ![测试资源管理器](../media/UnitTests/show-test-explorer.png)

1. 若要运行测试部署，你的项目必须采用与 (专门使用通用身份验证和远程计算机) 配置 UWP 应用相同的方式进行配置。  有关详细信息，请参阅[部署具有 Visual Studio 的应用](../develop-your-app/appdeployment.md)。

1. 若要远程运行单元测试，可以使用测试资源管理器，右键单击所需的 TestMethod，然后选择 "运行/调试选定的测试" " ![ 测试资源管理器 1"](../media/UnitTests/test-explorer.png)

1. 若要远程运行或调试所有单元测试，可以使用测试 > 运行或测试 > 调试 ![ 测试资源管理器 2 ](../media/UnitTests/run-tests.png)
  ![ 测试资源管理器3](../media/UnitTests/debug-tests.png)


### <a name="configure-unit-tests-as-part-of-a-continuous-integration-build"></a>将单元测试配置为持续集成生成的一部分
___

Visual Studio 团队已经创建了一个很好的博客文章，其中展示了如何将 Windows 10 IoT 核心版单元测试合并为 VSTS 生成：[使用 Win10 iot Core、UWP 和 VSTS 的 iot DevOps](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)
