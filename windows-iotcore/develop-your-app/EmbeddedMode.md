---
title: 嵌入模式
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
description: 了解如何配置 Windows 以允许嵌入模式下，启用后台应用程序和其他功能。
keywords: windows iot、 嵌入的模式、 后台应用程序
ms.openlocfilehash: ca8124d97a9161a1539eff92c55cf3630cf0a049
ms.sourcegitcommit: b719e66699372e1339c2316cab45df2a474d09a0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2019
ms.locfileid: "66252178"
---
# <a name="embedded-mode"></a>嵌入模式

Windows IoT Core 和 Windows IoT 企业版支持嵌入的模式。 使嵌入的模式：

* [后台应用程序 （阅读更多）](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* LowLevelDevice 功能的使用
* 系统管理功能的使用

在窗口 IoT Core 上始终启用嵌入的模式。
必须在 Windows IoT 企业版上按照以下步骤启用嵌入的模式。

## <a name="background-applications"></a>后台应用程序

使用 Visual Studio 中的后台应用程序 (IoT) 模板创建后台应用程序。
详细了解如何创建[后台应用程序](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)。

后台运行，而不停止且资源限制的应用程序。 此外，如果出于某种原因停止后台应用程序和嵌入连接模式下启用的后台应用程序将由系统重新启动。

时系统将自动重新启动后台应用程序，必须启用系统锁定功能以防止用户停止或干扰后台应用程序的操作。

## <a name="lowlevel-device-capability-and-lowleveldevice-capability"></a>lowLevel 设备功能和 lowLevelDevice 功能

**LowLevel**设备功能，如 GPIO、 SPI 和 I2C 低级别的硬件接口访问。

* [灾难从天而降 Sample(GPIO)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)
* [加速感应器示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

**LowLevelDevices**功能允许应用访问自定义设备时满足其他要求的数量。 此功能不应混淆 lowLevel 设备功能，可对 GPIO、 I2C、 SPI 和 PWM 设备访问权限。

请参阅[应用功能声明](https://docs.microsoft.com/en-us/windows/uwp/packaging/app-capability-declarations)有关详细信息。

## <a name="systemmanagment-capability"></a>systemManagment 功能

为你的应用程序启用 systemManagment 功能时这是已解锁的 Api 集：  

* [Windows.System.ProcessLauncher](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [Windows.System.TimeZoneSettings](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [Windows.System.ShutdownManager](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [Windows.Globalization.Language.TrySetInputMethodLanguageTag](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a>调试后台应用程序

如果正在调试的设备运行的不是 Windows IoT 核心版，并且看到以下任一错误消息，你需要确保该设备上已启用 AllowEmbeddedMode 且“嵌入模式”服务处于运行状态：

* 端点映射程序中未提供更多端点。
* 此程序由组策略阻止。 有关详细信息，请与系统管理员联系。

## <a name="changing-the-mode"></a>更改模式
若要启用嵌入模式，你将需要在映像和配置设计器 (ICD)（将 AllowEmbeddedMode 设置为 1）中创建设置包。  若要安装 ICD，你需要下载并安装适用于 Windows 10 的 Windows ADK。

* [下载适用于 Windodws 10 的 Windows ADK](http://go.microsoft.com/fwlink/p/?LinkId=526740)
* [了解适用于 Windows 10 的 Windows ADK 中的新增功能](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)

1. 当安装 ADK 选择**映像和配置设计器 (ICD)**
2. 安装完成后运行 Windows 映像和配置设计器 (WICD)。

    ![WICD 图标](../media/EmbeddedMode/WICD_Icon.png)

3. 单击“高级预配”  。  将项目命名**AllowEmbeddedMode**然后单击**下一步**。
    ![Step3](../media/EmbeddedMode/Step3.png)

4. 选择**普遍适用于所有 Windows 版本**然后**下一步**。
    ![Step4](../media/EmbeddedMode/Step4.png)

5. 单击 **“完成”** 。

    ![步骤 5](../media/EmbeddedMode/Step5.png)

6. 在搜索框中键入**EmbeddedMode** ，然后单击**AllowEmbeddedMode**。

    ![步骤 6](../media/EmbeddedMode/Step6.png)

7. 在中心窗格中设置的值**AllowEmbeddedMode**到**是** ![Step7](../media/EmbeddedMode/Step7.png)

8. 单击导出 > 预配包

    ![步骤 8](../media/EmbeddedMode/Step8.png)

9. 单击“下一步”。

    ![步骤 9](../media/EmbeddedMode/Step9.png)

10. 单击“下一步”。

    ![步骤 10](../media/EmbeddedMode/Step10.png)

11. 单击“下一步”。

    ![步骤 11](../media/EmbeddedMode/Step11.png)

12. 单击生成。

    ![步骤 12](../media/EmbeddedMode/Step12.png)

13. 若要安装的嵌入的模式。双击 PPKG Windows IoT 企业版上的。PPKG。

14. 单击**可以，请将其添加**。
    单击是开 LUA 对话框中如果出现，然后单击**是，将其添加**上如下所示的对话框。
    ![Step14Standard](../media/EmbeddedMode/Step14Standard.png)


## <a name="configuring-a-background-application-to-run-automatically"></a>自动配置为运行一个后台应用程序
1. 若要配置后台应用程序自动运行你将需要按照的说明为[创建 MinnowBoardMax SD 卡](https://developer.microsoft.com/en-us/windows/iot/getstarted)并复制`D:\windows\system32\iotstartup.exe`（其中 d： 是 SD 卡）。

2. 若要获取已安装的后台应用程序类型的列表：

        C:\> iotstartup list BackgroundApplication1

3. 输出应包含每个已安装的后台应用将如下所示的完整名称：

        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee

5. 若要配置此应用程序运行时在引导类型：

        C:\> iotstartup add headless BackgroundApplication1

6. 如果后台应用程序已成功添加到启动列表您应看到：

        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1

7. 重启嵌入的模式设备：

8. 设备已重新启动后，后台应用程序将自动启动。  管理后台应用程序的嵌入模式服务可能需要几分钟才能开始。  嵌入的模式服务将监视启动列表上的后台应用程序，并确保他们获取它们停止时重新启动。  如果在短时间内多次停止后台应用程序将无法再重启。

9. 若要从启动列表类型中删除后台应用程序：

        C:\> iotstartup remove headless BackgroundApplication1

10. 如果从启动列表中删除后台应用程序输出将如下所示：

        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
