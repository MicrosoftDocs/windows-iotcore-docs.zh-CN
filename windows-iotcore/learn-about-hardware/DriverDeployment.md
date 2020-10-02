---
title: 驱动程序部署
author: parameshbabu
ms.author: pabab
ms.date: 08/22/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 在 Windows 10 IoT Core 上构建并部署驱动程序。 配置你的 Visual Studio 驱动程序项目，以便可以编译和部署特定平台的驱动程序。
keywords: windows 10 IoT Core，驱动程序部署
ms.openlocfilehash: 772cd46022a69f68ebfd9ec79c7c2eb3fe7933c0
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655903"
---
# <a name="driver-deployment"></a>驱动程序部署

使用 Visual Studio 在 Windows 10 IoT Core 上部署驱动程序。

配置你的 Visual Studio 驱动程序项目，以便可以在驱动程序开发阶段为特定平台编译和部署驱动程序。

对于本练习，可以使用 [gpiokmdfdemo 示例驱动程序](https://github.com/ms-iot/samples/tree/develop/DriverSamples)。

如果要将驱动程序添加到映像，请访问 [IoT 制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image)中的说明。

## <a name="step-1-setup"></a>步骤1：安装
___

### <a name="on-the-device"></a>在设备上

* 请确保你的设备按照 [入门说明](https://go.microsoft.com/fwlink/?linkid=860461)安装了 IoTCore 映像。
* 通过 [PowerShell](../connect-your-device/PowerShell.md)连接到你的设备。

### <a name="on-the-pc"></a>在电脑上

* 请确保已安装 Visual Studio 2017。
* 安装 [Windows 驱动程序工具包](https://developer.microsoft.com/windows/hardware/windows-driver-kit)。  你将需要安装 SDK 和 WDK。
* 安装证书，以便对驱动程序进行正确签名，并且可以在设备上运行。 从提升权限的命令提示符处执行下列命令：

    1.  `cd c:\Program Files (x86)\Windows Kits\10\Tools\bin\i386`
    2.  `set WPDKContentRoot=c:\Program Files (x86)\Windows Kits\10`
    3.  `InstallOEMCerts.cmd`

* 应用修补程序，以从 VS 启用 F5 部署。 在提升的命令提示符下，执行以下命令：

    1.  `cd %TEMP%` ( 会将目录更改为 `c:\users\<usernsme>\Appdata\Local\Temp`) 
    2.  `md “WdkTempFiles”` 手动创建 "WdkTempFiles" 目录这是工具中 bug 的一种解决方法，只需在 PC 中执行 *一次* 。


## <a name="step-2-provision-device-with-visual-studio"></a>步骤2：在 Visual Studio 中预配设备
___
* 打开 Visual Studio 并选择 " **驱动程序" > 测试 > 配置设备 > 添加新设备**
    * 如果未显示 "驱动程序" 菜单选项，请检查是否安装了 SDK。

* 在 " **设备配置** " 对话框中，
    * 为目标设备输入用户友好的显示名称
    * 选择设备类型 = 移动
    * 在显示的列表中，按 IP 地址排序，查找 IoT 设备的地址并选择。 如果有两个条目，请选择一个具有非零 GUID 的条目。  确保行已选中–应突出显示蓝色
    * 对话框底部有两个单选按钮。  选择 " **设置设备"，然后选择 "调试器设置**"。  选择“下一步”

* 在 " **配置调试器设置**" 上，设置适当的设置。  注意以下事项：
   * MinnowBoardMax 可以使用网络进行调试。
       * 使用连接类型 **网络**
       * 选择某个端口–默认值可以使用
       * 选择一些密钥-默认值可以使用
       * 选择运行 visual studio 的计算机的主机 IP。  请勿使用 autonet (169.xxx) 地址。
       * 选择“下一步”

  ![配置调试设置](../media/DriverDeployment/confdbgsettings.png)

    * Raspberry Pi 使用串行进行内核调试。
       *  将相应的串行调试电缆连接到 PI 和主机
       *  为连接类型选择 " **串行** "
       *  针对 Raspberry Pi 填写参数的其余部分。
       *  选择“下一步”

* 通过 VS，WDK 现在将预配 IoT 设备。  将在设备上安装 TAEF 和 WDTF，并按上面提供的设置针对内核调试设置设备。

* 完成后，设备可能会重新启动。  **设备配置**上的进度屏幕将提供状态，并在 IoT 设备完成安装后显示完成。 按 " **完成**"。

![配置进度](../media/DriverDeployment/confprogress.png)

* 设备现已设置，**设备测试配置**状态显示为 "**驱动程序测试**"

![配置设备](../media/DriverDeployment/ConfigureDevices.png)

## <a name="step-3-configure-visual-studio-driver-project"></a>步骤3：配置 Visual Studio 驱动程序项目
___    
1. 在管理员模式下启动 Visual Studio，然后打开 visual studio 驱动程序项目。
2. 请确保目标平台版本与开发计算机上安装的 SDK 匹配。 从 "解决方案资源管理器" 窗口中选择 "项目属性"。  在 "常规配置属性" 下，确保目标平台版本与开发计算机上安装的 SDK 匹配。  可以从 "控制面板" 中检查 SDK 的版本， **> 程序 ">" 程序和功能**"。
3. 在 " **Project > Visual C++ > Windows 驱动程序添加新项" >**，选择 " **包清单** " 并按 " **添加**"。

![程序包清单](../media/DriverDeployment/PackageManifest.png)

 `Package.pkg.xml` 文件将被添加到项目。 在此文件中，指定所有者、平台、组件和子组件标记。

![包 .pkg xml](../media/DriverDeployment/Package-pkg-xml.png)

4. 在 **项目属性 > PackageGen > 版本**中设置包版本号。 请注意，每次需要执行驱动程序的安装/重新安装时，此版本号必须递增。

![包版本](../media/DriverDeployment/PackageVersion.png)

5. 在 " **项目属性 > 驱动程序签名" > 测试证书**"下，选择" 测试证书 (电话 OEM 测试证书 ") 

![DriverSigning](../media/DriverDeployment/DriverTestSigning.png)

6. 请参阅 **驱动程序安装** 并选择 **部署**

![安装选项](../media/DriverDeployment/installOptions.png)

* 从 " **目标设备名称** " 下拉列表中，选择在预配过程中创建的目标。 请注意两个用于 **安装/重新** 安装和 **快速重新安装**的选项。 选择一个选项，然后单击 **"确定"**。
* **安装/重新安装** 用于向目标驱动程序的初始安装。  这将使用 Windows 更新堆栈安装驱动程序包，可能需要几分钟时间。 每次更改 INF 文件时都必须使用此文件。

> [!TIP]
> 在初始安装后，每次用此选项安装驱动程序时，包版本号必须递增。

* 安装驱动程序后，可以使用**快速重新安装**，并且不会对驱动程序 INF 文件进行后续更改，这会影响注册表。  此方法将绕过安装过程，关闭与驱动程序相关的所有 devnodes，将驱动程序复制到，并重新启动 devnode。  这会花费几个 ( # B0 20) 秒。


> [!WARNING]
> 不保证此方法成功-如果由于某种原因无法关闭 devnode 来释放驱动程序，操作将失败。  这可能是由硬件故障或驱动程序的初始错误实现引起的。  在这种情况下，必须使用 "安装/重新安装" 选项。


你的 Visual Studio 项目现在已准备好生成驱动程序并将其部署到目标设备。 如果使用的是示例 gpiokmdfdemo 驱动程序，则需要生成 ACPI 表，并将其复制到目标设备，然后按照在 [Visual Studio 中生成驱动程序](https://developer.microsoft.com/windows/iot/samples/driverlab2)中的步骤进行操作。


## <a name="step-4-build-and-deploy-driver"></a>步骤4：生成并部署驱动程序
___
这可以通过两种方式来完成：使用 **F5** 键并使用 " **部署** " 选项。 在这两种方法中，将生成并部署该驱动程序 (即，将其安装到设备) 上，然后 F5 将 Visual Studio 内核调试器附加到安装和加载的驱动程序。

某些用户喜欢使用 **部署** 功能并附加不同的内核调试器，如 WINDBG 或 KD。  与使用 VS 调试器相比，这可以提供更大的灵活性。

### <a name="deploy"></a>部署
1.  右键单击解决方案资源管理器中的项目
2.  选择“部署”

![选择“部署”](../media/DriverDeployment/deploy.png)

3.  部署过程应继续。  IoT 设备将在部署后重新启动，并在进行安装时显示 "齿轮" 屏幕。

生成输出在 " **输出** " 窗口中，安装完成后也会出现在 "输出" 窗口中，设备将再次重新启动，而 VS 输出屏幕将指示成功或失败。

### <a name="f5"></a>F5

1.  在 "生成" 窗口中，确保配置正确– "当前生成" 与目标设备相同。  在这种情况下，目标名称中的这种情况非常有用。  目标将显示在 VS 中的菜单栏上的 "视图" 框中，位于右上方。
2.  按 **F5**。  目标将生成、部署并附加到 VS 内核调试器。

* 重新启动后，请确保 PowerShell 仍连接到它，否则，请使用 PowerShell 命令重新连接到目标设备。 `enter-pssession`


## <a name="known-issues"></a>已知问题
___

### <a name="provisioning-errors"></a>预配错误
与 MinnowBoardMax 交互过程中的争用条件可能会导致在预配过程中出现报告故障。  事实上，预配可能会成功。

**错误列表：**

* 错误：任务 "注册 WDTF" 未能成功完成。
* 错误：任务 "配置内核调试器设置 (可能重新启动) " 无法成功完成

**解决方法：** 几乎肯定会忽略这些错误。

**详细**

**设备配置配置进度**对话框中将显示以下错误：

```
Installing necessary components...
Removing TAEF test service
    Task "Removing TAEF test service" completed successfully
Copying required files
    Task "Copying required files" completed successfully
Registering TAEF Test Service
    Task "Registering TAEF Test Service" completed successfully
Starting TAEF Test Service
    Task "Starting TAEF Test Service" completed successfully
Registering WDTF
    Task "Registering WDTF" completed successfully
Configuring TAEF test service to start automatically
    Task "Configuring TAEF test service to start automatically" completed successfully
Configuring kernel debugger settings (possible reboot)
    ERROR: Task "Configuring kernel debugger settings (possible reboot)" failed to complete successfully. Look at the logs in the driver test group explorer for more details on the failure.
Configuring computer settings (possible reboot)
Waiting for task to complete...
Waiting for task to complete...
    Task "Configuring computer settings (possible reboot)" completed successfully
Computer configuration log file://C:/Users/username/AppData/Roaming/Microsoft/WDKTestInfrastructure/ProvisioningLogs/Driver%20Test%20Computer%20Configuration%log
Failed installing components
```

此时，你可以安全地单击 " **完成** "，然后单击 " **应用** **" 和 "确定"**。

这是由争用情况形成的良性错误，导致结果日志的格式不正确。 可以通过查看以下区域中的日志文件来对此进行验证：

1. 打开到设备 IP 的 FTP 连接 (如设备屏幕上所示) 到 `Data/test/bin/DriverTest/Run` 目录。
例如，`ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`

2. 将 `Configuring_computer_settings_(possible_reboot)_identifier.wtl` 文件复制到本地计算机。  请注意，日志文件名称与失败的任务的名称相匹配。
3. 在记事本中打开文件
4. 滚动到日志的底部。  将显示以下文本，指示预配成功。

```
<PFRollup
    Total="1"
    Passed="1"
    Failed="0"
    Blocked="0"
    Warned="0"
    Skipped="0" CA="6191559" LA="6191619" >
    <rti id="2109770915" />
    <ctx id="384048256" />
</PFRollup>
</WTT-Logger>
```
