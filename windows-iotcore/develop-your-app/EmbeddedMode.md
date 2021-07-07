---
title: 嵌入模式
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何配置 Windows以允许嵌入模式，从而启用后台应用程序和其他功能。
keywords: windows iot， 嵌入式模式， 后台应用程序
ms.openlocfilehash: 234ef9cf416eabd446eb3bd27b6d8004bf40cb71
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229904"
---
# <a name="embedded-mode"></a>嵌入模式

IoT 核心Windows IoT Windows支持嵌入式Enterprise。 嵌入式模式启用：

* [后台应用程序 (阅读) ](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* 使用 lowLevelDevice 功能
* 使用 systemManagement 功能

在窗口 IoT 核心上始终启用嵌入式模式。
必须在 IoT 应用程序上按照以下步骤Windows嵌入式Enterprise。

## <a name="background-applications"></a>后台应用程序

后台应用程序是使用 Visual Studio 中的"后台应用程序 (IoT) 模板创建的。
详细了解如何创建 [后台应用程序](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)。

后台应用程序无需停止且没有资源限制即可运行。 此外，如果后台应用程序因某种原因停止并启用了嵌入模式，则系统会重启后台应用程序。

虽然系统将自动重启后台应用程序，但必须启用系统锁定功能，以防止用户停止或干扰后台应用程序的操作。

## <a name="lowlevel-device-capability-and-lowleveldevice-capability"></a>lowLevel 设备功能以及 lowLevelDevice 功能

**lowLevel** 设备功能提供对低级别硬件接口（如 GPIO、SPI 和 I2C）的访问权限。

* [GPIO (Blinky 示例) ](https://developer.microsoft.com/windows/iot/samples/helloblinky)
* [加速计示例](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

**lowLevelDevices** 功能允许应用在满足大量其他要求时访问自定义设备。 不能将此功能与 lowLevel 设备功能混淆，后者允许访问 GPIO、I2C、SPI 和 PWM 设备。

有关详细信息 [，请参阅应用](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) 功能声明。

## <a name="systemmanagment-capability"></a>systemManagment 功能

为应用程序启用 systemManagment 功能时，这是一组解锁的 API：  

* [Windows.System。ProcessLauncher](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [Windows.System.TimeZoneSettings](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [Windows.System。ShutdownManager](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [Windows。Globalization.Language.TrySetInputMethodLanguageTag](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a>调试后台应用程序

如果在未运行 Windows IoT Core 的设备上进行调试，并且看到以下错误消息之一，则需要确保在设备上启用 AllowEmbeddedMode 并确保嵌入模式服务正在运行：

* 终结点映射器中不再有可用的终结点。
* 此程序被组策略阻止。 有关详细信息，请与系统管理员联系。

## <a name="changing-the-mode"></a>更改模式
若要启用嵌入式模式，需要在映像和配置设计器的 ICD (创建设置 AllowEmbeddedMode=1) 预配包。  若要安装 ICD，需要下载并安装 Windows ADK Windows 10。

* [下载适用于 Windows 10 的 Windows ADK](https://go.microsoft.com/fwlink/p/?LinkId=526740)
* [了解适用于 Windows 10 的 Windows ADK 中的新增Windows 10](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)

1. 安装 ADK 时，选择"映像 **和配置设计器" (ICD)**
2. 安装完成后，在 WICD Windows映像和配置设计器 (运行) 。

    ![WICD 图标](../media/EmbeddedMode/WICD_Icon.png)

3. 单击 **"高级预配"。**  将项目命名 **为 AllowEmbeddedMode，** 然后单击"下一 **步"。**
    ![步骤#3](../media/EmbeddedMode/Step3.png)

4. 选择 **"通用到所有Windows"，然后选择**"下一 **步"。**
    ![步骤#4](../media/EmbeddedMode/Step4.png)

5. 单击“完成”  。

    ![步骤#5](../media/EmbeddedMode/Step5.png)

6. 在搜索框中键入 **EmbeddedMode，** 然后单击 **"AllowEmbeddedMode"。**

    ![步骤#6](../media/EmbeddedMode/Step6.png)

7. 在中心窗格中，将 **AllowEmbeddedMode** 的值设置为 **"是步骤** ![ #7](../media/EmbeddedMode/Step7.png)

8. 单击"导出>预配包"

    ![步骤#8](../media/EmbeddedMode/Step8.png)

9. 单击“下一步”。

    ![步骤#9](../media/EmbeddedMode/Step9.png)

10. 单击“下一步”。

    ![步骤#10](../media/EmbeddedMode/Step10.png)

11. 单击“下一步”。

    ![步骤#11](../media/EmbeddedMode/Step11.png)

12. 单击“生成”。

    ![步骤#12](../media/EmbeddedMode/Step12.png)

13. 安装嵌入模式 。在 IoT Windows上的 PPKG Enterprise双击 。PPKG。

14. 单击 **"是，添加"。**
    如果 LUA 对话框出现，请单击"是"，然后单击"是，在如下所示的对话框中添加它"。
    ![标准#14步骤](../media/EmbeddedMode/Step14Standard.png)


## <a name="configuring-a-background-application-to-run-automatically"></a>将后台应用程序配置为自动运行
1. 若要将后台应用程序配置为自动运行，需要按照说明创建 [MinnowBoardMax SD](https://developer.microsoft.com/windows/iot/getstarted) 卡，并复制 (其中 D： 是 `D:\windows\system32\iotstartup.exe` SD 卡) 。

2. 若要获取已安装的后台应用程序的列表，请键入：
```
        C:\> iotstartup list BackgroundApplication1
```
3. 输出应包含每个已安装的后台应用程序的全名，如下所示：
```
        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
```
5. 若要配置此应用以在启动类型下运行，请执行：
```
        C:\> iotstartup add headless BackgroundApplication1
```
6. 如果后台应用程序已成功添加到启动列表中，应会看到：
```
        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1
```
7. 重启嵌入式模式设备：

8. 重启设备后，后台应用程序将自动启动。  管理后台应用程序的嵌入式模式服务可能需要几分钟时间才能启动。  嵌入式模式服务将监视启动列表中的后台应用程序，并确保它们在停止时重启。  如果后台应用程序在短时间内多次停止，则它将不再重启。

9. 若要从启动列表中删除后台应用程序，请键入：
```
        C:\> iotstartup remove headless BackgroundApplication1
```
10. 如果从启动列表中删除了后台应用程序，则输出将如下所示：
```
        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
```
