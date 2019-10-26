---
title: 移动宽带连接
ms.date: 06/12/2018
ms.topic: article
description: 了解如何使用适用于 Windows 10 IoT Core 的 Mobile 宽带连接。
keywords: windows iot，MBB，mobile 宽带连接
ms.openlocfilehash: 2bf9a153fb77ab7f92bad727847cdf581d0b7729
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918337"
---
# <a name="mobile-broadband-connection"></a>移动宽带连接

[Windows 10 IoT Core](http://windowsondevices.com)支持移动宽带连接。 如果 IoT 网关支持移动宽带调制解调器模块，则可以使用 `MBBConnect` 工具来帮助在 IoT Core 中设置移动宽带连接的配置。

`MBBConnect` 检索连接的相关信息，例如订户 ID、SIM ICC ID、接口名称和 home 提供商名称等。然后，它会创建连接配置文件。 您需要做的唯一事情是提供 APN，并自动设置连接。

`MBBConnect` 基于 MinnowBoard 的基于最大的 IoT 网关进行开发和测试，运行 IoT Core 版本16299和 mobile 宽带调制解调器模块，通过台湾的主要电信提供商提供 SIM 卡。

### <a name="usage"></a>Usage

1. 将 `MBBConnect.exe` 复制到 IoT 网关。

   * [FTP](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. 通过 Powershell 或 SSH 连接网关。

   * [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [SSH](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. 切换到 `MBBConnect.exe` 所在的文件夹。 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a>示例
下面的示例在 PowerShell 中使用 MBBConnect。 例如，如果 SIM 卡的 APN 是 "Internet"，请使用 `MBBConnect.exe Internet` 进行连接。
 
输出消息将显示流：

* 状态从 "未连接" 更改为 "已连接"。 

* 已成功配置 WWAN 网络。

[在此处](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect)试用移动宽带连接的示例。
