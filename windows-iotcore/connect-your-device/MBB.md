---
title: 移动宽带连接
ms.date: 06/12/2018
ms.topic: article
description: 使用适用于 Windows 10 IoT Core 的 Mobile 宽带连接。 使用 MBBConnect 工具帮助在 IoT Core 中设置移动宽带连接的配置。
keywords: windows iot，MBB，mobile 宽带连接
ms.openlocfilehash: c10e56bc42bf2c77eb74d0e7cd8170cceaa72b75
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782589"
---
# <a name="mobile-broadband-connection"></a>移动宽带连接

[Windows 10 IoT Core](http://windowsondevices.com)支持移动宽带连接。 如果 IoT 网关支持移动宽带调制解调器模块，则可以使用该 `MBBConnect` 工具来帮助在 IoT Core 中设置移动宽带连接的配置。

`MBBConnect` 检索连接的相关信息，例如订户 ID、SIM ICC ID、接口名称和 home 提供商名称等。然后，它会创建连接配置文件。 你需要执行的唯一操作是提供 APN，并会自动设置连接。

`MBBConnect` 基于 MinnowBoard 的基于最大的 IoT 网关，运行 IoT Core 版本16299和 mobile 宽带调制解调器模块，并通过台湾的主要电信提供商提供 SIM 卡。

### <a name="usage"></a>使用情况

1. 复制 `MBBConnect.exe` 到 IoT 网关。

   * [FTP](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. 通过 PowerShell 或 SSH 连接网关。

   * [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [SSH](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. 切换到所在的文件夹 `MBBConnect.exe` 。 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a>示例
下面的示例在 PowerShell 中使用 MBBConnect.exe。 例如，如果 SIM 卡的 APN 是 "Internet"，请使用 `MBBConnect.exe Internet` 进行连接。
 
输出消息将显示流：

* 状态从 "未连接" 更改为 "已连接"。 

* 已成功配置 WWAN 网络。

[在此处](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect)试用移动宽带连接的示例。
