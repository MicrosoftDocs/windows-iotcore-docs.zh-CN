---
title: 嵌入模式
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何将 Windows 配置为允许嵌入模式，启用后台应用程序和其他功能。
keywords: windows iot，embedded 模式，后台应用程序
ms.openlocfilehash: c7ecf9c4f163cf034c265b3e01581c9578dd9816
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656483"
---
# <a name="embedded-mode"></a>嵌入模式

Windows IoT Core 和 Windows IoT Enterprise 支持嵌入模式。 嵌入模式启用：

* [ (了解) 的后台应用程序 ](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* LowLevelDevice 功能的使用
* SystemManagement 功能的使用

Windows IoT Core 上始终启用嵌入模式。
必须通过在 Windows IoT Enterprise 上执行以下步骤来启用嵌入模式。

## <a name="background-applications"></a>后台应用程序

后台应用程序使用 Visual Studio 中的后台应用程序 (IoT) 模板来创建。
阅读有关创建 [后台应用程序](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)的详细信息。

后台应用程序在运行时无需停止并且没有资源限制。 此外，如果后台应用程序因某种原因而停止并且嵌入模式已启用，则系统会重新启动后台应用程序。

当系统将自动重新启动后台应用程序时，必须启用系统锁定功能，以防止用户停止或干扰后台应用程序的操作。

## <a name="lowlevel-device-capability-and-lowleveldevice-capability"></a>lowLevel 设备功能和 lowLevelDevice 功能

**LowLevel**设备功能提供对低级硬件接口（如 GPIO、SPI 和 I2C）的访问权限。

* [Blinky 示例 (GPIO) ](https://developer.microsoft.com/windows/iot/samples/helloblinky)
* [加速感应示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

当满足一些额外的要求时， **lowLevelDevices** 功能允许应用访问自定义设备。 不能将此功能与 lowLevel 设备功能混淆，后者允许访问 GPIO、I2C、SPI 和 PWM 设备。

有关详细信息，请参阅 [应用功能声明](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) 。

## <a name="systemmanagment-capability"></a>systemManagment 功能

为你的应用程序启用 systemManagment 功能时，这是一个已解除锁定的 Api 集：  

* [Windows.System。ProcessLauncher](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [Windows.System.TimeZoneSettings](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [Windows.System。ShutdownManager](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [Windows TrySetInputMethodLanguageTag](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a>调试后台应用程序

如果在未运行 Windows IoT Core 的设备上进行调试，并看到以下错误消息之一，你需要确保在设备上启用 AllowEmbeddedMode 并且嵌入模式服务正在运行：

* 终结点映射器中没有更多可用的终结点。
* 此程序已被组策略阻止。 有关详细信息，请与系统管理员联系。

## <a name="changing-the-mode"></a>更改模式
若要启用嵌入模式，你将需要在映像和配置设计器 (ICD) 中创建设置 AllowEmbeddedMode = 1 的预配包。  若要安装 ICD，需要下载并安装适用于 Windows 10 的 Windows ADK。

* [下载适用于 Windows 10 的 Windows ADK](https://go.microsoft.com/fwlink/p/?LinkId=526740)
* [了解适用于 Windows 10 的 Windows ADK 中的新增功能](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)

1. 安装 ADK 时 ** (ICD) **
2. 安装完成后，请运行 Windows 映像和配置设计器 (WICD) 。

    ![WICD 图标](../media/EmbeddedMode/WICD_Icon.png)

3. 单击 " **高级设置**"。  将项目命名为 **AllowEmbeddedMode** ，然后单击 " **下一步**"。
    ![步骤 #3](../media/EmbeddedMode/Step3.png)

4. 选择 " **通用"，** 然后选择 " **下一步**"。
    ![步骤 #4](../media/EmbeddedMode/Step4.png)

5. 单击“完成”。

    ![步骤 #5](../media/EmbeddedMode/Step5.png)

6. 在搜索框中键入 " **EmbeddedMode** "，然后单击 " **AllowEmbeddedMode**"。

    ![步骤 #6](../media/EmbeddedMode/Step6.png)

7. 在中心窗格中，将 **AllowEmbeddedMode** 的值设置为 **"是"** ![ 步骤 #7](../media/EmbeddedMode/Step7.png)

8. 单击 "导出" > 预配包

    ![步骤 #8](../media/EmbeddedMode/Step8.png)

9. 单击“下一步”。

    ![步骤 #9](../media/EmbeddedMode/Step9.png)

10. 单击“下一步”。

    ![步骤 #10](../media/EmbeddedMode/Step10.png)

11. 单击“下一步”。

    ![步骤 #11](../media/EmbeddedMode/Step11.png)

12. 单击“生成”。

    ![步骤 #12](../media/EmbeddedMode/Step12.png)

13. 安装嵌入模式。PPKG 在 Windows IoT Enterprise 上双击。PPKG.

14. 单击 **"是，添加它"**。
    在 LUA 对话框上单击 "是" （如果出现），然后单击 **"是，将其添加** 到下面显示的对话框中"。
    ![步骤 #14 标准](../media/EmbeddedMode/Step14Standard.png)


## <a name="configuring-a-background-application-to-run-automatically"></a>将后台应用程序配置为自动运行
1. 若要将后台应用程序配置为自动运行，需要按照说明 [创建 MINNOWBOARDMAX Sd 卡](https://developer.microsoft.com/windows/iot/getstarted) ，并将 `D:\windows\system32\iotstartup.exe` (其中 D：是 SD 卡) 。

2. 若要获取已安装后台应用程序的列表，请键入：
```
        C:\> iotstartup list BackgroundApplication1
```
3. 输出应包括每个已安装后台应用程序的完整名称，如下所示：
```
        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
```
5. 将此应用配置为在启动时运行类型：
```
        C:\> iotstartup add headless BackgroundApplication1
```
6. 如果后台应用程序已成功添加到启动列表，你应该会看到以下内容：
```
        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1
```
7. 重新启动嵌入的模式设备：

8. 设备重新启动后，后台应用程序将自动启动。  管理后台应用程序的嵌入模式服务可能需要几分钟的时间才能启动。  嵌入模式服务将监视启动列表上的后台应用程序，并确保它们在停止时重新启动。  如果后台应用程序在很短的时间内停止多次，则将不再重新启动该应用程序。

9. 若要从启动列表中删除后台应用程序，请执行以下操作：
```
        C:\> iotstartup remove headless BackgroundApplication1
```
10. 如果从启动列表中删除后台应用程序，输出将如下所示：
```
        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
```
