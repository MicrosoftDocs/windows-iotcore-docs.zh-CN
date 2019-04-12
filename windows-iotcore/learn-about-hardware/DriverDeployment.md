---
title: 驱动程序部署
author: parameshbabu
ms.author: pabab
ms.date: 08/22/2017
ms.topic: article
description: 了解如何生成和部署使用 Visual Studio 的驱动程序。
keywords: windows 10 IoT Core，驱动程序部署
ms.openlocfilehash: aad50718ea44c46d676509fe2c5b408d471afc19
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510981"
---
# <a name="driver-deployment"></a>驱动程序部署

部署使用 Visual Studio 的 Windows 10 IoT Core 上的驱动程序。 

配置你的 Visual Studio 驱动程序项目，以便可以编译和部署驱动程序开发阶段的特定平台的驱动程序。 

对于此练习中可以使用[gpiokmdfdemo 示例驱动程序](https://github.com/ms-iot/samples/tree/develop/DriverSamples)。

如果您希望向映像添加驱动程序，请访问中的说明我们[IoT 制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image)。

## <a name="step-1--setup"></a>步骤 1:安装 
___

### <a name="on-the-device"></a>在设备上

* 请确保你的设备有 IoTCore 图像按照[入门说明](https://go.microsoft.com/fwlink/?linkid=860461)。
* 连接到你的设备通过[Powershell](../connect-your-device/PowerShell.md)。

### <a name="on-the-pc"></a>在 PC 上

* 请确保已安装 Visual Studio 2017。
* 安装[Windows 驱动程序工具包](https://developer.microsoft.com/windows/hardware/windows-driver-kit)。  你将需要安装 SDK 和 WDK。
* 安装证书，因此驱动程序签名正确，并可以在你的设备上运行。 从提升的命令提示符执行下面列出的命令：

    1.  `cd c:\Program Files (x86)\Windows Kits\10\Tools\bin\i386` 
    2.  `set WPDKContentRoot=c:\Program Files (x86)\Windows Kits\10`
    3.  `InstallOEMCerts.cmd`
  
* 将应用修复以启用从 VS F5 部署。 在提升的命令提示符中，执行以下命令：

    1.  `cd %TEMP%` (将目录更改为`c:\users\<usernsme>\Appdata\Local\Temp`)
    2.  `md “WdkTempFiles”` 手动创建一个"WdkTempFiles"目录，这是在工具中的 bug 的解决方法，需要完成*仅一次*在 PC 中。


## <a name="step-2--provision-device-with-visual-studio"></a>步骤 2:使用 Visual Studio 的预配设备 
___
* 打开 Visual Studio 并选择**驱动程序 > 测试 > 配置设备 > 添加新设备**
    * 如果未显示驱动程序菜单选项，检查是否已安装 SDK。

* 在中**设备配置**对话框中， 
    * 为目标设备输入用户友好显示名称
    * 选择设备类型 = 移动版
    * 在显示列表中，按 IP 地址进行排序和查找 IoT 设备的地址和选择。 如果有两个条目，选择具有非零 GUID。  请确保选择的行-它应突出显示蓝色
    * 在对话框的底部两个单选按钮。  选择一个指出**预配设备，并选择调试器设置**。  选择**下一步**

* 上**配置调试器设置**，设置合适的设置。  请注意以下事项：
   * MinnowBoardMax 可用网络来进行调试。
       * 使用连接类型**网络**
       * 选择某个端口-可以使用默认值
       * 选择一些密钥-可以使用默认值
       * 选择运行 visual studio 的计算机的主机 IP。  不要使用 autonet (169.xxx) 地址。
       * 选择**下一步**
       
  ![配置调试设置](../media/DriverDeployment/confdbgsettings.png)
       
    * 在 Raspberry Pi 使用串行进行内核调试。
       *  将相应的串行调试电缆连接到 PI，并将主机计算机
       *  选择**串行**的连接类型
       *  填写其余部分根据 Raspberry Pi 的参数。
       *  选择**下一步**

* WDK 通过 VS，现在将预配的 IoT 设备。  将在设备上安装 TAEF 和 WDTF 并且为内核调试根据上面提供的设置将设置设备。

* 完成后，设备可能会重新启动。  在进度屏幕**设备配置**将提供状态，并显示完整的 IoT 设备已完成的安装时。 按**完成**。

![配置进度](../media/DriverDeployment/confprogress.png)

* 现在已预配设备并**设备测试配置**状态显示**配置为用于驱动程序测试**

![ConfigureDevices](../media/DriverDeployment/ConfigureDevices.png)

## <a name="step-3--configure-visual-studio-driver-project"></a>步骤 3:配置 Visual Studio 驱动程序项目
___    
1. 在管理员模式下启动 Visual Studio 并打开 visual studio 驱动程序项目。
2. 确保目标平台版本与安装在你的开发计算机上的 SDK 匹配。 从“解决方案资源管理器”窗口中选择“项目属性”。  在“常规配置属性”下，确保目标平台版本与安装在你的开发计算机上的 SDK 匹配。  您可以检查从 SDK 的版本**控制面板 > 程序 > 程序和功能**。
3. 下**项目 > 添加新项 > Visual C++ > Windows 驱动程序**，选择**包清单**，然后按**添加**。

![PackageManifest](../media/DriverDeployment/PackageManifest.png)

 `Package.pkg.xml` 文件将添加到项目。 在此文件中指定的所有者、 平台、 组件和子组件的标记。 
 
![Package-pkg-xml](../media/DriverDeployment/Package-pkg-xml.png)
 
4. 设置在程序包版本号**项目属性 > PackageGen > 版本**。 请注意，每次需要执行该驱动程序安装/重新安装，此版本号会递增。

![PackageVersion](../media/DriverDeployment/PackageVersion.png)

5. 下**项目属性 > 驱动程序签名 > 测试证书**，选择测试证书 （Phone OEM 测试证书）

![DriverSigning](../media/DriverDeployment/DriverTestSigning.png)

6. 转到**驱动程序安装**，然后选择**部署**

![InstallOptions](../media/DriverDeployment/installOptions.png)

* 从**目标设备名称**下拉列表中，选择在预配过程中创建上述目标。 请注意，两个选项**安装 / 重新安装**并**快速重新安装**。 选择选项并单击**确定**。
* **安装 / 重新安装**用于驱动程序添加到目标的初始安装。  这将安装使用 Windows 更新堆栈的驱动程序包，并且可能需要几分钟。 这必须使用每次更改 INF 文件。 
    
> [!TIP]
> 每次使用此选项在初始安装后安装驱动程序，必须递增程序包版本号。

* **快速重新安装**已安装驱动程序，并没有后续更改的驱动程序 INF 文件这会影响注册表后可以使用。  此方法会跳过安装过程，然后关闭与该驱动程序相关联的所有 devnodes、 逐过程复制驱动程序并重新启动 devnode。  这需要花费几个 (< 20) 秒。

    
> [!WARNING]
> 此方法是不能保证成功 – 如果 devnode 不能为关闭，以释放该驱动程序由于某种原因，则操作将失败。  这可能是由于硬件故障或初始发生故障的驱动程序实现。  安装/重新安装选项，必须在这种情况下使用。


你的 Visual Studio 项目现已准备就绪，可生成驱动程序并将其部署到目标设备。 如果你将需要生成 ACPI 表并复制到目标设备的示例 gpiokmdfdemo 驱动程序，然后按照中的步骤[构建 Visual Studio 中的驱动程序](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2)。


## <a name="step-4--build-and-deploy-driver"></a>步骤 4:生成和部署驱动程序
___
这可以在两个方面，使用**F5**密钥和使用**部署**选项。 这两种方式构建和部署驱动程序 （即其设备上安装） 和 F5 将 Visual Studio 内核调试程序附加到已安装并加载驱动程序。 

某些用户更喜欢使用**部署**功能和附加不同内核调试程序，如 WinDBG 或 KD。  这可以提供更大的灵活性比使用 VS 调试器。

### <a name="deploy"></a>部署
1.  右键单击解决方案资源管理器中的项目
2.  选择**部署**

![部署](../media/DriverDeployment/deploy.png) 

3.  部署过程应继续进行。  IoT 设备部署后，将重启和安装正在进行时，应显示"齿轮"屏幕。

生成输出采用**输出**窗口部署状态也是在输出窗口时安装完成，设备将再次，重新启动和 VS 输出屏幕将指示成功或失败。

### <a name="f5"></a>F5

1.  从生成窗口中，确保正确配置 – 当前生成体系结构是与目标设备体系结构相同。  这是其中的目标名称中具有体系结构是有价值。  在右上角中间在 VS 中的菜单栏上的视图框中，将显示目标。
2.  按**F5**。  目标生成、 部署，并将附加到 VS 内核调试程序。

* 重新启动后，请确保 PowerShell 仍连接到它，否则，重新连接到目标设备使用 PowerShell`enter-pssession`命令...


## <a name="known-issues"></a>已知问题
___

### <a name="provisioning-errors"></a>预配错误
在与 MinnowBoardMax 交互期间的争用条件可能导致在预配期间报告失败。  事实上，预配最有可能成功。

**错误的列表：**
 
* 错误：任务的"注册的 WDTF"无法成功完成。
* 错误：任务"配置内核调试程序设置 （可能需要重启）"无法成功完成

**解决方法：** 几乎可以肯定可以忽略这些错误。

**详细信息：**

以下的错误将显示在**设备配置配置进度**对话框：

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

现在你可以安全地单击**完成**，然后**应用**并**确定**。

这是良性错误格式正确的结果日志格式不正确导致的争用条件。 这可以通过查看以下区域中的日志文件进行验证：

1. 打开到 FTP 连接到的 IP 的设备 （如设备屏幕所示）`Data/test/bin/DriverTest/Run`目录。
例如
`ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`

2. 复制`Configuring_computer_settings_(possible_reboot)_identifier.wtl`到本地计算机的文件。  请注意日志文件名称与匹配失败任务的名称。
3. 在记事本中打开该文件
4. 滚动到日志底部。  下面的文本将会显示，指示已成功预配。

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

