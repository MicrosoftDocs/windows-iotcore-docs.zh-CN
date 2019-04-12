---
title: 移动宽带连接
author: saraclay
ms.author: saclayt
ms.date: 06/12/18
ms.topic: article
description: 了解如何使用移动宽带连接的 Windows 10 IoT Core。
keywords: windows iot，MBB，移动宽带连接
ms.openlocfilehash: 3afa48e049e38f7e26308434ba6f7349ac0be050
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510937"
---
## <a name="mobile-broadband-connection"></a>移动宽带连接

支持的移动宽带连接[Windows 10 IoT Core](http://windowsondevices.com)。 如果你的 IoT 网关支持的移动宽带调制解调器模块，可以使用`MBBConnect`工具，可帮助 IoT Core 中的移动宽带连接的安装程序配置。

`MBBConnect` 检索连接中，订阅者 ID、 SIM ICC ID、 接口名称和家庭提供程序名称等的相关信息。然后，创建连接配置文件。 将需要执行操作的唯一是提供 APN，并且它将自动设置连接。

`MBBConnect` 是开发和测试使用 MinnowBoard 最大值基于运行 IoT Core 版本 16299 和移动宽带调制解调器模块的 SIM 卡从主要电信提供商在中国台湾地区的 IoT 网关。

### <a name="usage"></a>用法

1. 复制`MBBConnect.exe`到 IoT 网关。

   * [FTP](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. 网关通过 Powershell 或 SSH 连接。

   * [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [SSH](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. 切换到的文件夹位置`MBBConnect.exe`所在。 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a>示例
下面的示例在 PowerShell 中使用 MBBConnect.exe。 例如，如果此 APN SIM 卡的"Internet"，请使用`MBBConnect.exe Internet`连接。
 
输出消息会显示该流：

* 状态将变为未连接从已连接。 

* 已成功配置 WWAN 网络。

移动宽带连接尝试示例[此处](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect)。
