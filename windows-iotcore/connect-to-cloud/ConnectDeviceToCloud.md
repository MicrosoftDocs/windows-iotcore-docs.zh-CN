---
title: 将设备连接到云
ms.date: 08/28/2017
ms.topic: article
description: 了解如何将设备连接到云。
keywords: windows iot，Azure，安全性，受信任的平台模块，SoC
ms.openlocfilehash: 62120695d2209227f938ebd5635380f226dddfc1
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721502"
---
# <a name="connect-your-device-to-the-cloud"></a><span data-ttu-id="c183c-104">将设备连接到云</span><span class="sxs-lookup"><span data-stu-id="c183c-104">Connect your device to the cloud</span></span>

<span data-ttu-id="c183c-105">在设备上存储安全信息（如密码或证书）可能会使设备容易遭受曝光。</span><span class="sxs-lookup"><span data-stu-id="c183c-105">Storing secure information such as a password or a certificate on a device could make a device vulnerable to exposure.</span></span> <span data-ttu-id="c183c-106">泄漏密码是一种损害设备或整个系统的安全的 surefire 方式。</span><span class="sxs-lookup"><span data-stu-id="c183c-106">A leaked password is a surefire way to compromise the security of a device or an entire system.</span></span> <span data-ttu-id="c183c-107">在 Windows 系列中，支持操作系统安全的技术是受信任的平台模块。</span><span class="sxs-lookup"><span data-stu-id="c183c-107">In the Windows family, the technology that supports the security of the OS is the Trusted Platform Module.</span></span>

<span data-ttu-id="c183c-108">[受信任的平台模块](https://en.wikipedia.org/wiki/Trusted_Platform_Module)（TPM）设备是一个可以存储数据和执行计算的微控制器。</span><span class="sxs-lookup"><span data-stu-id="c183c-108">A [Trusted Platform Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module) (TPM) device is a microcontroller that can store data and perform computations.</span></span> <span data-ttu-id="c183c-109">它可以是焊接到计算机主板上的离散芯片，也可以是制造商提供的芯片（SoC）上集成到系统中的模块。</span><span class="sxs-lookup"><span data-stu-id="c183c-109">It can be either a discrete chip soldered to a computer's motherboard or a module integrated into the system on a chip (SoC) by the manufacturer.</span></span> 

## <a name="inside-the-tpm"></a><span data-ttu-id="c183c-110">TPM 内部</span><span class="sxs-lookup"><span data-stu-id="c183c-110">Inside the TPM</span></span> 

<span data-ttu-id="c183c-111">TPM 的一项重要功能是它只写内存。</span><span class="sxs-lookup"><span data-stu-id="c183c-111">A key capability of the TPM is its write-only memory.</span></span> <span data-ttu-id="c183c-112">根据数据，TPM 还可以根据数据计算加密哈希（例如[HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)）。</span><span class="sxs-lookup"><span data-stu-id="c183c-112">Based on the data in it, TPM can also compute a cryptographic hash (such as the [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)), based on that data.</span></span>
<span data-ttu-id="c183c-113">由于哈希，无法发现机密，但如果对双方的通信都知道密码，则可能会确定是否从该机密产生了从另一方收到的哈希。</span><span class="sxs-lookup"><span data-stu-id="c183c-113">It’s impossible to uncover the secret given the hash, but if the secret is known to both parties of communication, it is possible to determine whether the hash received from another party was produced from that secret.</span></span>

<span data-ttu-id="c183c-114">使用加密密钥的基本思路：机密（也称为共享访问密钥）在设备预配过程中建立并共享 IoT 设备和云。</span><span class="sxs-lookup"><span data-stu-id="c183c-114">The basic idea behind using cryptographic keys: the secret (also called the shared access key) is established and shared between the IoT device and the cloud during the device provisioning process.</span></span> <span data-ttu-id="c183c-115">从此时开始，将使用从机密派生的 HMAC 对 IoT 设备进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="c183c-115">From that point on, an HMAC derived from the secret will be used to authenticate the IoT device.</span></span>

## <a name="device-provisioning"></a><span data-ttu-id="c183c-116">设备预配</span><span class="sxs-lookup"><span data-stu-id="c183c-116">Device Provisioning</span></span> 

<span data-ttu-id="c183c-117">设置 Windows 10 IoT Core 设备的工具称为 IoT 核心仪表板，可以从[下载页](https://go.microsoft.com/fwlink/?LinkID=708576)下载。</span><span class="sxs-lookup"><span data-stu-id="c183c-117">The tool that provisions Windows 10 IoT Core devices is called the IoT Core Dashboard and can be downloaded from [the downloads page](https://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

<span data-ttu-id="c183c-118">仪表板会生成操作系统映像，并将设备安全连接到 Azure。</span><span class="sxs-lookup"><span data-stu-id="c183c-118">The dashboard produces an image of the OS and securely connects your device to Azure.</span></span> <span data-ttu-id="c183c-119">这是通过将物理设备与 Azure IoT 中心中的设备 ID 相关联并将设备特定的共享访问密钥 imprinting 到设备的 TPM 来完成的。</span><span class="sxs-lookup"><span data-stu-id="c183c-119">This is done by associating the physical device with the device ID in the Azure IoT Hub and imprinting the device-specific shared access key to the device's TPM.</span></span> 

<span data-ttu-id="c183c-120">对于没有 TPM 芯片的设备，此工具可以安装软件模拟的 TPM。</span><span class="sxs-lookup"><span data-stu-id="c183c-120">For devices that don’t have a TPM chip, the tool can install a software-emulated TPM.</span></span> <span data-ttu-id="c183c-121">这并不提供安全性，但允许使用 maker 设备开发应用（如 Raspberry Pi 2 或3），并在具有硬件 TPM 的设备上具有安全性 "亮起"，而无需更改应用。</span><span class="sxs-lookup"><span data-stu-id="c183c-121">This does not provide security but allows you to develop your app using a maker device (such as Raspberry Pi 2 or 3) and have security "light up" on a device with the hardware TPM without having to change the app.</span></span> 

<span data-ttu-id="c183c-122">若要将设备连接到 Azure，请单击 "连接到 Azure" 选项卡：</span><span class="sxs-lookup"><span data-stu-id="c183c-122">To connect your device to Azure, click on the "Connect to Azure" tab:</span></span>

![打开 "连接到 Azure" 选项卡](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen01.png)

<span data-ttu-id="c183c-124">系统将要求你登录到 Azure 帐户。</span><span class="sxs-lookup"><span data-stu-id="c183c-124">You will be asked to log in to your Azure account.</span></span> <span data-ttu-id="c183c-125">选择所需的 Azure IoT 中心实例，并将你的物理设备与它相关联。</span><span class="sxs-lookup"><span data-stu-id="c183c-125">Pick the desired instance of Azure IoT Hub and associate your physical device with it.</span></span> <span data-ttu-id="c183c-126">如果 Azure 订阅中没有任何 IoT 中心实例，则该工具将允许你创建一个免费的实例。</span><span class="sxs-lookup"><span data-stu-id="c183c-126">If you don’t have any IoT Hub instances in your Azure subscription, the tool will let you create a free instance.</span></span> 

<span data-ttu-id="c183c-127">选择要与设备关联的 IoT 中心和设备 ID 后，你可以在 TPM 上为该设备的共享访问密钥加上一个选项：</span><span class="sxs-lookup"><span data-stu-id="c183c-127">Once you have selected the IoT Hub and the device ID to associate your device with, you can imprint the shared access key of that device on your TPM:</span></span>

![预配设备](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen02.png)

<span data-ttu-id="c183c-129">你的设备现在可以通过安全方式连接到 Azure。</span><span class="sxs-lookup"><span data-stu-id="c183c-129">Your device is now ready to connect to Azure in a secure way.</span></span> 

<span data-ttu-id="c183c-130">你还可以使用 Windows 设备门户在设置后首次连接到 internet 时，动态获取 IoT 中心连接字符串。</span><span class="sxs-lookup"><span data-stu-id="c183c-130">You can also use the Windows Device Portal to dynamically acquire an IoT Hub connection string when it first connects to the internet after being provisioned.</span></span> <span data-ttu-id="c183c-131">这可以从设备门户中的 "Azure 客户端" 选项卡完成。</span><span class="sxs-lookup"><span data-stu-id="c183c-131">This can be done from the "Azure Clients" tab in the Device Portal.</span></span>

![Azure 客户端选项卡](../media/ConnectDeviceToCloud/azure-clients.png)

## <a name="helpful-resources"></a><span data-ttu-id="c183c-133">有用资源：</span><span class="sxs-lookup"><span data-stu-id="c183c-133">Helpful resources:</span></span>
* [<span data-ttu-id="c183c-134">将你的应用连接到 Azure</span><span class="sxs-lookup"><span data-stu-id="c183c-134">Connecting your app to Azure</span></span>](../connect-to-cloud/ConnectAppToCloud.md)
* [<span data-ttu-id="c183c-135">为 IoT Core 构建安全应用</span><span class="sxs-lookup"><span data-stu-id="c183c-135">Building secure apps for IoT Core</span></span>](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core/#oqFLXiWIL1iCF8j9.97)
