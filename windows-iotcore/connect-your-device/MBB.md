---
title: 移动宽带连接
author: saraclay
ms.author: saclayt
ms.date: 06/12/18
ms.topic: article
description: 了解如何使用适用于 Windows 10 IoT Core 的 Mobile 宽带连接。
keywords: windows iot, MBB, mobile 宽带连接
ms.openlocfilehash: 3afa48e049e38f7e26308434ba6f7349ac0be050
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168045"
---
## <a name="mobile-broadband-connection"></a>移动宽带连接

[Windows 10 IoT Core](http://windowsondevices.com)支持移动宽带连接。 如果 iot 网关支持移动宽带调制解调器模块, 则可以使用该`MBBConnect`工具来帮助在 IoT Core 中设置移动宽带连接的配置。

`MBBConnect`检索连接的相关信息, 例如订户 ID、SIM ICC ID、接口名称和 home 提供商名称等。然后, 它会创建连接配置文件。 您需要做的唯一事情是提供 APN, 并自动设置连接。

`MBBConnect`基于 MinnowBoard 的基于最大的 IoT 网关, 运行 IoT Core 版本16299和 mobile 宽带调制解调器模块, 并通过台湾的主要电信提供商提供 SIM 卡。

### <a name="usage"></a>用法

1. 复制`MBBConnect.exe`到 IoT 网关。

   * [FTP](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. 通过 Powershell 或 SSH 连接网关。

   * [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [SSH](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. 切换到所在的文件夹`MBBConnect.exe` 。 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a>示例
下面的示例在 PowerShell 中使用 MBBConnect。 例如, 如果 SIM 卡的 APN 是 "Internet", 请使用`MBBConnect.exe Internet`进行连接。
 
输出消息将显示流:

* 状态从 "未连接" 更改为 "已连接"。 

* 已成功配置 WWAN 网络。

[在此处](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect)试用移动宽带连接的示例。
