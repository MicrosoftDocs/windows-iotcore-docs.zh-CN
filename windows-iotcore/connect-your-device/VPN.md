---
title: 在 Windows 10 IoT Core 上的 VPN
author: saraclay
ms.author: saclayt
ms.date: 11/19/2018
ms.topic: article
description: 了解如何使用安装程序，并配置 Windows 10 IoT Core 设备的 VPN 功能。
keywords: windows iot，VPN，安装程序、 设备
ms.openlocfilehash: 94eafcb74a05179a7741cb516b5e7be30b525092
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510787"
---
# <a name="leveraging-vpn-capabilities-for-your-windows-10-iot-core-device"></a><span data-ttu-id="72cb4-104">利用 VPN 功能为你的 Windows 10 IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="72cb4-104">Leveraging VPN capabilities for your Windows 10 IoT Core device</span></span>

<span data-ttu-id="72cb4-105">若要充分利用 Windows 10 IoT Core 的 VPN 功能，请执行下面的说明。</span><span class="sxs-lookup"><span data-stu-id="72cb4-105">In order to leverage the VPN capabilities of Windows 10 IoT Core, follow the instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="72cb4-106">必须适合最下面的说明。</span><span class="sxs-lookup"><span data-stu-id="72cb4-106">Most of the instructions below must be adapted.</span></span> <span data-ttu-id="72cb4-107">它们是特定于用户要连接的 VPN 主机。</span><span class="sxs-lookup"><span data-stu-id="72cb4-107">They are specific to the VPN host that the user is connecting to.</span></span> <span data-ttu-id="72cb4-108">使用的证书是示例。</span><span class="sxs-lookup"><span data-stu-id="72cb4-108">The certs used are examples.</span></span>

## <a name="establishing-a-vpn-connection"></a><span data-ttu-id="72cb4-109">建立 VPN 连接</span><span class="sxs-lookup"><span data-stu-id="72cb4-109">Establishing a VPN connection</span></span> 

1. <span data-ttu-id="72cb4-110">获取必要的证书并将复制到你的 IoT 设备 （例如到 \vpntest 文件夹）。</span><span class="sxs-lookup"><span data-stu-id="72cb4-110">Obtain the necessary certs and copy to your IoT device (e.g. to a \vpntest folder).</span></span>

* <span data-ttu-id="72cb4-111">RASTest.pfx</span><span class="sxs-lookup"><span data-stu-id="72cb4-111">RASTest.pfx</span></span>
* <span data-ttu-id="72cb4-112">IssuingCA.crl</span><span class="sxs-lookup"><span data-stu-id="72cb4-112">IssuingCA.crl</span></span>
* <span data-ttu-id="72cb4-113">RootCA.crl</span><span class="sxs-lookup"><span data-stu-id="72cb4-113">RootCA.crl</span></span>

2. <span data-ttu-id="72cb4-114">应用本地计算机证书。</span><span class="sxs-lookup"><span data-stu-id="72cb4-114">Apply local machine certs a.</span></span> <span data-ttu-id="72cb4-115">以管理员身份的设备到 PowerShell</span><span class="sxs-lookup"><span data-stu-id="72cb4-115">PowerShell into device as administrator</span></span>

```powershell
certmgr -add .\IssuingCA.crl -r localmachine -s root
certmgr -add .\RootCA.crl -r localmachine -s root
```

3. <span data-ttu-id="72cb4-116">应用用户证书。</span><span class="sxs-lookup"><span data-stu-id="72cb4-116">Apply user certs a.</span></span> <span data-ttu-id="72cb4-117">登录到"DefaultAccount"作为使用 SSH 的 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="72cb4-117">Login to the IoT Device using SSH as "DefaultAccount".</span></span>
<span data-ttu-id="72cb4-118">b.</span><span class="sxs-lookup"><span data-stu-id="72cb4-118">b.</span></span> <span data-ttu-id="72cb4-119">从命令提示符处，键入"PowerShell"。</span><span class="sxs-lookup"><span data-stu-id="72cb4-119">From the command prompt, type "PowerShell".</span></span>
<span data-ttu-id="72cb4-120">c.</span><span class="sxs-lookup"><span data-stu-id="72cb4-120">c.</span></span> <span data-ttu-id="72cb4-121">从 PowerShell （在中记录为"默认帐户"） 时发出以下命令：</span><span class="sxs-lookup"><span data-stu-id="72cb4-121">Issue the following commands from PowerShell (while logged in as "Default Account"):</span></span>

```powershell
$mypwd = ConvertTo-SecureString -String "<password>" -Force -AsPlainText
import-pfxcertificate -FilePath RasTest.pfx -CertStoreLocation cert:currentUser\my -Password $mypwd

Cert -add .\IssuingCA.crl -r currentuser -s my
certmgr -add .\RootCA.crl -r currentuser -s my
```

4. <span data-ttu-id="72cb4-122">修复主机文件添加到 c:\windows\system32\driverS\etc\hosts 文件 （如下所示的示例;） 的条目</span><span class="sxs-lookup"><span data-stu-id="72cb4-122">Fix hosts file Add an entry into c:\windows\system32\driverS\etc\hosts file (example shown below);</span></span>

> |    |    |    |
> |----|----| ---|
> | <span data-ttu-id="72cb4-123">10.10.10.10</span><span class="sxs-lookup"><span data-stu-id="72cb4-123">10.10.10.10</span></span> | <span data-ttu-id="72cb4-124">MyVPN.DomainName.org</span><span class="sxs-lookup"><span data-stu-id="72cb4-124">MyVPN.DomainName.org</span></span> | <span data-ttu-id="72cb4-125">根据需要使用 IP 地址和域的名称替换</span><span class="sxs-lookup"><span data-stu-id="72cb4-125">Replace with IP address and domain name as needed</span></span> |

5. <span data-ttu-id="72cb4-126">生成 VPN 测试应用的源代码中的"MyVPN.DomainName.org"替换。</span><span class="sxs-lookup"><span data-stu-id="72cb4-126">Build the VPN test app Replace the "MyVPN.DomainName.org" in the source code.</span></span> <span data-ttu-id="72cb4-127">根据需要进一步增强。</span><span class="sxs-lookup"><span data-stu-id="72cb4-127">Augment further as needed.</span></span>

6. <span data-ttu-id="72cb4-128">将在下面的代码部署到 Windows 10 IoT 设备的"启动和停止 VPN 连接"部分。</span><span class="sxs-lookup"><span data-stu-id="72cb4-128">Deploy the code below in the "Starting and stopping a VPN Connection" section to the Windows 10 IoT device.</span></span>
<span data-ttu-id="72cb4-129">输入任意"配置文件名称"，然后按"连接到 VPN"按钮。</span><span class="sxs-lookup"><span data-stu-id="72cb4-129">Enter an arbitrary "Profile name" and press the "Connect to VPN" button.</span></span> 


## <a name="starting-and-stopping-a-vpn-connection"></a><span data-ttu-id="72cb4-130">启动和停止 VPN 连接</span><span class="sxs-lookup"><span data-stu-id="72cb4-130">Starting and stopping a VPN connection</span></span>

<span data-ttu-id="72cb4-131">使用下面的代码来启动和停止 VPN 连接。</span><span class="sxs-lookup"><span data-stu-id="72cb4-131">Use the code below to start and stop a VPN connection.</span></span>

```csharp

  private async Task ConnectVPNProfile()
        {
            string vpnProfileName = "MyVPNProfileName";

            string[] epdg = { "MyVPN.DomainName.org" };
            VpnManagementErrorStatus status = VpnManagementErrorStatus.Ok;
            IAsyncOperation<VpnManagementErrorStatus> op;

            var vpnMa = new VpnManagementAgent();
            var vpnProfile = new VpnNativeProfile();
            vpnProfile.AlwaysOn = true;
            vpnProfile.ProfileName = vpnProfileName;
            vpnProfile.RequireVpnClientAppUI = true;
            vpnProfile.RememberCredentials = true;
            vpnProfile.RoutingPolicyType = VpnRoutingPolicyType.SplitRouting;
            vpnProfile.TunnelAuthenticationMethod = VpnAuthenticationMethod.Eap;
            vpnProfile.UserAuthenticationMethod = VpnAuthenticationMethod.Eap;
            foreach (var s in epdg)
            {
                vpnProfile.Servers.Add(s);
            }

            vpnProfile.EapConfiguration = GetEapXmlString();

            // Adds the profile using the management api.
           status = await vpnMa.AddProfileFromObjectAsync(vpnProfile);
            Debug.WriteLine($"Add profile: {status}");
            TextBlockLog.Text += $"Add profile: {status}\r\n";

            await Task.Delay(1000);

            op = vpnMa.ConnectProfileAsync(vpnProfile);
            status = await op;
            Debug.WriteLine($"Connect succeeded: {status}");
            TextBlockLog.Text += $"Connect profile: {status}\r\n";


        }


  public static string GetEapXmlString()
        {
            //string template = "<EapHostConfig xmlns=\"http://www.microsoft.com/provisioning/EapHostConfig\"><EapMethod><Type xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">25</Type><VendorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorId><VendorType xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorType><AuthorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</AuthorId></EapMethod><Config xmlns=\"http://www.microsoft.com/provisioning/EapHostConfig\"><Eap xmlns=\"http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1\"><Type>25</Type><EapType xmlns=\"http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV1\"><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames></ServerNames><TrustedRootCA>d2 d3 8e ba 60 ca a1 c1 20 55 a2 e1 c8 3b 15 ad 45 01 10 c2 </TrustedRootCA><TrustedRootCA>d1 76 97 cc 20 6e d2 6e 1a 51 f5 bb 96 e9 35 6d 6d 61 0b 74 </TrustedRootCA></ServerValidation><FastReconnect>true</FastReconnect><InnerEapOptional>false</InnerEapOptional><Eap xmlns=\"http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1\"><Type>13</Type><EapType xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1\"><CredentialsSource><CertificateStore><SimpleCertSelection>true</SimpleCertSelection></CertificateStore></CredentialsSource><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames></ServerNames><TrustedRootCA>d2 d3 8e ba 60 ca a1 c1 20 55 a2 e1 c8 3b 15 ad 45 01 10 c2 </TrustedRootCA><TrustedRootCA>d1 76 97 cc 20 6e d2 6e 1a 51 f5 bb 96 e9 35 6d 6d 61 0b 74 </TrustedRootCA></ServerValidation><DifferentUsername>false</DifferentUsername><PerformServerValidation xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">true</PerformServerValidation><AcceptServerName xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">false</AcceptServerName><TLSExtensions xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\"><FilteringInfo xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3\"><EKUMapping><EKUMap><EKUName>AAD Conditional Access</EKUName><EKUOID>1.3.6.1.4.1.311.87</EKUOID></EKUMap></EKUMapping><ClientAuthEKUList Enabled=\"true\"><EKUMapInList><EKUName>AAD Conditional Access</EKUName></EKUMapInList></ClientAuthEKUList></FilteringInfo></TLSExtensions></EapType></Eap><EnableQuarantineChecks>false</EnableQuarantineChecks><RequireCryptoBinding>true</RequireCryptoBinding><PeapExtensions><PerformServerValidation xmlns=\"http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2\">true</PerformServerValidation><AcceptServerName xmlns=\"http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2\">false</AcceptServerName></PeapExtensions></EapType></Eap></Config></EapHostConfig>";
            string template = "<EapHostConfig xmlns =\"http://www.microsoft.com/provisioning/EapHostConfig\"><EapMethod><Type xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">13</Type><VendorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorId><VendorType xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorType><AuthorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</AuthorId></EapMethod><Config xmlns=\"http://www.microsoft.com/provisioning/EapHostConfig\"><Eap xmlns=\"http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1\"><Type>13</Type><EapType xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1\"><CredentialsSource><CertificateStore><SimpleCertSelection>true</SimpleCertSelection></CertificateStore></CredentialsSource><ServerValidation><DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation><ServerNames></ServerNames><TrustedRootCA>b6 ea bf ba 48 be 09 c9 50 4f c6 ea 9b f5 74 dc a9 01 56 62 </TrustedRootCA></ServerValidation><DifferentUsername>false</DifferentUsername><PerformServerValidation xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">false</PerformServerValidation><AcceptServerName xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">false</AcceptServerName><TLSExtensions xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\"><FilteringInfo xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3\"><CAHashList Enabled=\"true\"><IssuerHash>b6 ea bf ba 48 be 09 c9 50 4f c6 ea 9b f5 74 dc a9 01 56 62 </IssuerHash></CAHashList></FilteringInfo></TLSExtensions></EapType></Eap></Config></EapHostConfig>";
            //TODO: Create propper XML here
            string result = template;

            return result;
        }
```







