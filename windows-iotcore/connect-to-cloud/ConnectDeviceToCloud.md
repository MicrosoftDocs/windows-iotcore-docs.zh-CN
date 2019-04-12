---
title: 将设备连接到云
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何将设备连接到云。
keywords: windows iot，Azure，安全性，受信任的平台模块、 SoC
ms.openlocfilehash: ff54bbfa1aaf30d08107fac72ba59ae5a04aa247
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59511004"
---
# <a name="connect-your-device-to-the-cloud"></a><span data-ttu-id="37291-104">将设备连接到云</span><span class="sxs-lookup"><span data-stu-id="37291-104">Connect your device to the cloud</span></span>

<span data-ttu-id="37291-105">将安全信息，例如密码或证书存储在设备上无法使设备受到危害。</span><span class="sxs-lookup"><span data-stu-id="37291-105">Storing secure information such as a password or a certificate on a device could make a device vulnerable to exposure.</span></span> <span data-ttu-id="37291-106">密码是欢心办法危及设备或整个系统的安全。</span><span class="sxs-lookup"><span data-stu-id="37291-106">A leaked password is a surefire way to compromise the security of a device or an entire system.</span></span> <span data-ttu-id="37291-107">在 Windows 系列，支持的操作系统的安全性的技术是受信任的平台模块。</span><span class="sxs-lookup"><span data-stu-id="37291-107">In the Windows family, the technology that supports the security of the OS is the Trusted Platform Module.</span></span>

<span data-ttu-id="37291-108">一个[受信任的平台模块](https://en.wikipedia.org/wiki/Trusted_Platform_Module)(TPM) 设备是可以存储数据和执行计算的微型控制器。</span><span class="sxs-lookup"><span data-stu-id="37291-108">A [Trusted Platform Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module) (TPM) device is a microcontroller that can store data and perform computations.</span></span> <span data-ttu-id="37291-109">它可以是焊接到计算机的主板的离散芯片或集成到芯片 (SoC) 上的系统制造商的模块。</span><span class="sxs-lookup"><span data-stu-id="37291-109">It can be either a discrete chip soldered to a computer's motherboard or a module integrated into the system on a chip (SoC) by the manufacturer.</span></span> 

## <a name="inside-the-tpm"></a><span data-ttu-id="37291-110">TPM 内部</span><span class="sxs-lookup"><span data-stu-id="37291-110">Inside the TPM</span></span> 

<span data-ttu-id="37291-111">TPM 的关键功能是它只写的内存。</span><span class="sxs-lookup"><span data-stu-id="37291-111">A key capability of the TPM is its write-only memory.</span></span> <span data-ttu-id="37291-112">根据在其中的数据，TPM 还可以计算的加密哈希 (如[HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code))、 基于该数据。</span><span class="sxs-lookup"><span data-stu-id="37291-112">Based on the data in it, TPM can also compute a cryptographic hash (such as the [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)), based on that data.</span></span>
<span data-ttu-id="37291-113">不可能的秘密给定哈希，但如果机密识别这两个参与方的通信，就可以确定是否从另一方收到的哈希通过生成的该机密。</span><span class="sxs-lookup"><span data-stu-id="37291-113">It’s impossible to uncover the secret given the hash, but if the secret is known to both parties of communication, it is possible to determine whether the hash received from another party was produced from that secret.</span></span>

<span data-ttu-id="37291-114">使用加密密钥的基本理念： 建立并在设备预配过程期间的 IoT 设备和云之间共享的机密 （也称为共享的访问密钥）。</span><span class="sxs-lookup"><span data-stu-id="37291-114">The basic idea behind using cryptographic keys: the secret (also called the shared access key) is established and shared between the IoT device and the cloud during the device provisioning process.</span></span> <span data-ttu-id="37291-115">从该点开始，将使用派生自该机密的 HMAC IoT 设备进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="37291-115">From that point on, an HMAC derived from the secret will be used to authenticate the IoT device.</span></span>

## <a name="device-provisioning"></a><span data-ttu-id="37291-116">设备预配</span><span class="sxs-lookup"><span data-stu-id="37291-116">Device Provisioning</span></span> 

<span data-ttu-id="37291-117">预配 Windows 10 IoT Core 设备的工具称为 IoT 核心版仪表板，可以从下载[下载页面](http://go.microsoft.com/fwlink/?LinkID=708576)。</span><span class="sxs-lookup"><span data-stu-id="37291-117">The tool that provisions Windows 10 IoT Core devices is called the IoT Core Dashboard and can be downloaded from [the downloads page](http://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

<span data-ttu-id="37291-118">在仪表板生成的 OS 映像，并安全地将你的设备连接到 Azure。</span><span class="sxs-lookup"><span data-stu-id="37291-118">The dashboard produces an image of the OS and securely connects your device to Azure.</span></span> <span data-ttu-id="37291-119">这是通过将物理设备与 Azure IoT 中心中的设备 ID 相关联并 imprinting 到设备的 TPM 的特定于设备的共享的访问密钥。</span><span class="sxs-lookup"><span data-stu-id="37291-119">This is done by associating the physical device with the device ID in the Azure IoT Hub and imprinting the device-specific shared access key to the device's TPM.</span></span> 

<span data-ttu-id="37291-120">对于不带 TPM 芯片的设备，该工具可以安装软件模拟的 TPM。</span><span class="sxs-lookup"><span data-stu-id="37291-120">For devices that don’t have a TPM chip, the tool can install a software-emulated TPM.</span></span> <span data-ttu-id="37291-121">这不提供安全性，但允许您开发应用程序使用的创建者设备 （如 Raspberry Pi 2 或 3） 和使用 TPM 的硬件设备上有"点燃"的安全，而无需更改应用。</span><span class="sxs-lookup"><span data-stu-id="37291-121">This does not provide security but allows you to develop your app using a maker device (such as Raspberry Pi 2 or 3) and have security "light up" on a device with the hardware TPM without having to change the app.</span></span> 

<span data-ttu-id="37291-122">若要将设备连接到 Azure 中，单击"连接到 Azure"选项卡上：</span><span class="sxs-lookup"><span data-stu-id="37291-122">To connect your device to Azure, click on the "Connect to Azure" tab:</span></span>

![打开连接到 Azure 的选项卡](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen01.png)

<span data-ttu-id="37291-124">你将需要登录到你的 Azure 帐户。</span><span class="sxs-lookup"><span data-stu-id="37291-124">You will be asked to log in to your Azure account.</span></span> <span data-ttu-id="37291-125">选择 Azure IoT 中心的所需的实例，并将你的物理设备与之关联。</span><span class="sxs-lookup"><span data-stu-id="37291-125">Pick the desired instance of Azure IoT Hub and associate your physical device with it.</span></span> <span data-ttu-id="37291-126">如果在 Azure 订阅中没有任何 IoT 中心实例，该工具将允许您创建一个免费的实例。</span><span class="sxs-lookup"><span data-stu-id="37291-126">If you don’t have any IoT Hub instances in your Azure subscription, the tool will let you create a free instance.</span></span> 

<span data-ttu-id="37291-127">选择 IoT 中心和设备 ID 将与设备相关联之后, 可以上的共享的访问密钥，该设备的标记在 TPM 上：</span><span class="sxs-lookup"><span data-stu-id="37291-127">Once you have selected the IoT Hub and the device ID to associate your device with, you can imprint the shared access key of that device on your TPM:</span></span>

![设备预配](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen02.png)

<span data-ttu-id="37291-129">你的设备现在已准备好以安全方式连接到 Azure。</span><span class="sxs-lookup"><span data-stu-id="37291-129">Your device is now ready to connect to Azure in a secure way.</span></span> 

<span data-ttu-id="37291-130">Windows Device Portal 还可用于动态获取 IoT 中心连接字符串，当它首次连接到 internet 后正在预配。</span><span class="sxs-lookup"><span data-stu-id="37291-130">You can also use the Windows Device Portal to dynamically acquire an IoT Hub connection string when it first connects to the internet after being provisioned.</span></span> <span data-ttu-id="37291-131">这可以从设备门户的"Azure 客户端"选项卡。</span><span class="sxs-lookup"><span data-stu-id="37291-131">This can be done from the "Azure Clients" tab in the Device Portal.</span></span>

![Azure 客户端选项卡](../media/ConnectDeviceToCloud/azure-clients.png)

## <a name="helpful-resources"></a><span data-ttu-id="37291-133">有用的资源：</span><span class="sxs-lookup"><span data-stu-id="37291-133">Helpful resources:</span></span>
* [<span data-ttu-id="37291-134">将应用连接到 Azure</span><span class="sxs-lookup"><span data-stu-id="37291-134">Connecting your app to Azure</span></span>](../connect-to-cloud/ConnectAppToCloud.md)
* [<span data-ttu-id="37291-135">IoT 核心版为构建安全应用程序</span><span class="sxs-lookup"><span data-stu-id="37291-135">Building secure apps for IoT Core</span></span>](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core/#oqFLXiWIL1iCF8j9.97)
