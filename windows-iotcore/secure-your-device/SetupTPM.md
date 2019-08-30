---
title: 在建议的平台上设置 TPM
author: saraclay
ms.author: saclayt
ms.date: 09/05/17
ms.topic: article
description: 在建议的平台上设置 TPM 后, 了解如何使设备安全。
keywords: windows iot, 安全性, 安装程序, 受信任的平台模块, TPM, 加密, 密钥
ms.openlocfilehash: cc82262e3f800195b460bfe1113ec7c075d36b9a
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170125"
---
# <a name="setting-up-tpm-on-suggested-platforms"></a><span data-ttu-id="a54d7-104">在建议的平台上设置 TPM</span><span class="sxs-lookup"><span data-stu-id="a54d7-104">Setting up TPM on Suggested Platforms</span></span>

## <a name="setup-firmware-tpm-ftpm"></a><span data-ttu-id="a54d7-105">设置固件 TPM (fTPM)</span><span class="sxs-lookup"><span data-stu-id="a54d7-105">Setup firmware TPM (fTPM)</span></span>
<span data-ttu-id="a54d7-106">固件 TPM (fTPM) 需要特殊处理器/SoC 支持，因此，fTPM 当前在 Raspberry Pi2 上无法实现。</span><span class="sxs-lookup"><span data-stu-id="a54d7-106">Firmware TPM (fTPM) requires special Processor/SoC support and whence fTPM is not currently implemented on Raspberry Pi2.</span></span>

1. <span data-ttu-id="a54d7-107">必须使用内含版本 0.80 或更高版本的 UEFI 的 MBM。</span><span class="sxs-lookup"><span data-stu-id="a54d7-107">You must have MBM with UEFI version 0.80 or above.</span></span>
2. <span data-ttu-id="a54d7-108">通过更改以下 UEFI 设置来启用 fTPM：</span><span class="sxs-lookup"><span data-stu-id="a54d7-108">Enable fTPM by changing the following UEFI settings:</span></span>

        Device Manager -> System Setup -> Security Configuration -> PTT = <Enable>

3. <span data-ttu-id="a54d7-109">确保没有用于 sTPM/dTPM 的 C:\Windows\System32\ACPITABL.dat（解决冲突/删除不需要的文件）。</span><span class="sxs-lookup"><span data-stu-id="a54d7-109">Ensure you do not have C:\Windows\System32\ACPITABL.dat for sTPM/dTPM (resolve the conflict/delete the file if not needed).</span></span>
4. <span data-ttu-id="a54d7-110">验证是否已启用正确的 TPM 版本 - 在 Windows IoT 核心版设备上运行 [TPM 2.0 工具](https://github.com/ms-iot/security/tree/master/Urchin/T2T)。</span><span class="sxs-lookup"><span data-stu-id="a54d7-110">Verify you have the right TPM version enabled - run the [TPM 2.0 Tool](https://github.com/ms-iot/security/tree/master/Urchin/T2T) on the Windows IoT Core device.</span></span>

        C:\>t2t.exe -cap

        TBS detected 2.0 firmware TPM (fTPM) using Intel TEE.
        Capabilities:
        PT_FIXED:
        TPM_PT_FAMILY_INDICATOR = '2.0'
        TPM_PT_LEVEL = 0 (0x00000000)
        TPM_PT_REVISION = 0.93
        TPM_PT_DAY_OF_YEAR = 283 (0x0000011b)
        TPM_PT_YEAR = 2012 (0x000007dc)
        TPM_PT_MANUFACTURER = 'INTC'
        TPM_PT_VENDOR_STRING = 'Intel'
        TPM_PT_VENDOR_TPM_TYPE = 3 (0x00000003)
        TPM_PT_FIRMWARE_VERSION_1 = 1.0 (0x1.0x0)
        TPM_PT_FIRMWARE_VERSION_2 = 2.1060 (0x2.0x424)
        TPM_PT_INPUT_BUFFER = 1024 (0x00000400)
        TPM_PT_HR_TRANSIENT_MIN = 3 (0x00000003)
        TPM_PT_HR_PERSISTENT_MIN = 2 (0x00000002)
        TPM_PT_HR_LOADED_MIN = 3 (0x00000003)
        TPM_PT_ACTIVE_SESSIONS_MAX = 64 (0x00000040)
        TPM_PT_PCR_COUNT = 24 (0x00000018)
        TPM_PT_PCR_SELECT_MIN = 3 (0x00000003)
        TPM_PT_CONTEXT_GAP_MAX = 65535 (0x0000ffff)
        TPM_PT_NV_COUNTERS_MAX = 16 (0x00000010)
        TPM_PT_NV_INDEX_MAX = 2048 (0x00000800)
        TPM_PT_MEMORY = sharedNV objectCopiedToRam
        TPM_PT_CLOCK_UPDATE = 4096ms
        TPM_PT_CONTEXT_HASH = TPM_ALG_SHA256
        TPM_PT_CONTEXT_SYM = TPM_ALG_AES
        TPM_PT_CONTEXT_SYM_SIZE = 128 (0x00000080)
        TPM_PT_ORDERLY_COUNT = 255 (0x000000ff)
        TPM_PT_MAX_COMMAND_SIZE = 3968 (0x00000f80)
        TPM_PT_MAX_RESPONSE_SIZE = 3968 (0x00000f80)
        TPM_PT_MAX_DIGEST = 32 (0x00000020)
        TPM_PT_MAX_OBJECT_CONTEXT = 924 (0x0000039c)
        TPM_PT_MAX_SESSION_CONTEXT = 244 (0x000000f4)
        TPM_PT_PS_FAMILY_INDICATOR = TPM_PS_MAIN
        TPM_PT_PS_LEVEL = 0 (0x00000000)
        TPM_PT_PS_REVISION = 0
        TPM_PT_PS_DAY_OF_YEAR = 0 (0x00000000)
        TPM_PT_PS_YEAR = 0 (0x00000000)
        TPM_PT_SPLIT_MAX = 0 (0x00000000)
        TPM_PT_TOTAL_COMMANDS = 70 (0x00000046)
        TPM_PT_LIBRARY_COMMANDS = 70 (0x00000046)
        TPM_PT_VENDOR_COMMANDS = 0 (0x00000000)

        PT_VAR:
        TPM_PT_PERMANENT = lockoutAuthSet tpmGeneratedEPS
        TPM_PT_STARTUP_CLEAR = phEnable shEnable ehEnable
        TPM_PT_HR_NV_INDEX = 2 (0x00000002)
        TPM_PT_HR_LOADED = 0 (0x00000000)
        TPM_PT_HR_LOADED_AVAIL = 3 (0x00000003)
        TPM_PT_HR_ACTIVE = 0 (0x00000000)
        TPM_PT_HR_ACTIVE_AVAIL = 64 (0x00000040)
        TPM_PT_HR_TRANSIENT_AVAIL = 3 (0x00000003)
        TPM_PT_HR_PERSISTENT = 3 (0x00000003)
        TPM_PT_HR_PERSISTENT_AVAIL = 18 (0x00000012)
        TPM_PT_NV_COUNTERS = 2 (0x00000002)
        TPM_PT_NV_COUNTERS_AVAIL = 14 (0x0000000e)
        TPM_PT_ALGORITHM_SET = 0 (0x00000000)
        TPM_PT_LOADED_CURVES = 0 (0x00000000)
        TPM_PT_LOCKOUT_COUNTER = 0 (0x00000000)
        TPM_PT_MAX_AUTH_FAIL = 10 (0x0000000a)
        TPM_PT_LOCKOUT_INTERVAL = 2h 0" 0'
        TPM_PT_LOCKOUT_RECOVERY = 2h 0" 0'
        TPM_PT_AUDIT_COUNTER = 0

        c:\>

5. <span data-ttu-id="a54d7-111">验证 fTPM 是否正常工作 - 在 Windows IoT 核心版设备上运行 [Urchin 单元测试](https://github.com/ms-iot/security/tree/master/Urchin/UrchinTest)。</span><span class="sxs-lookup"><span data-stu-id="a54d7-111">Verify fTPM is functioning - run the [Urchin Unit Tests](https://github.com/ms-iot/security/tree/master/Urchin/UrchinTest) on the Windows IoT Core device.</span></span>  
   <span data-ttu-id="a54d7-112">应查看多个通过测试（请注意，某些功能并不受 fTPM 支持，因此预计会出现多个错误代码）：</span><span class="sxs-lookup"><span data-stu-id="a54d7-112">You should see several PASS tests (note that some of the functionality is not supported by the fTPM, so a few error codes are expected):</span></span>

        C:\>urchintest.exe
        ---SETUP----------------------------------------
        PASS...........CreateAuthorities()
        PASS...........CreateEkObject()
        PASS...........CreateSrkObject()
        (0x80280400)...CreateAndLoadAikObject()
        PASS...........CreateAndLoadKeyObject()

        ---TESTS----------------------------------------
        PASS...........TestGetCapability()
        PASS...........TestGetEntropy()
        PASS...........TestPolicySession()
        PASS...........TestSignWithPW()
        PASS...........TestSignHMAC()
        PASS...........TestSignBound()
        PASS...........TestSignSalted()
        PASS...........TestSignSaltedAndBound()
        PASS...........TestSignParameterEncryption()
        PASS...........TestSignParameterDecryption()
        PASS...........TestReadPcrWithEkSeededSession()
        (0x80280400)...TestCreateHashAndHMAC()
        (0x80280400)...TestCreateHashAndHMACSequence()
        (0x80280400)...TestSymKeyImport()
        PASS...........TestRsaKeyImport()
        (0x00000184)...TestCredentialActivation()
        PASS...........TestKeyExport()
        (0x80280400)...TestSymEncryption()
        (0x80280400)...TestCertifiedMigration()
        (0x0000014b)...TestNVIndexReadWrite()
        (0x80280400)...TestVirtualization()
        PASS...........TestObjectChangeAuth()
        PASS...........TestUnseal()
        PASS...........TestDynamicPolicies()
        (0x80280400)...TestRSADecrypt()
        (0x000002ca)...TestECDSASign()
        (0x00000184)...TestKeyAttestation()
        (0x00000184)...TestPlatformAttestation()

        ---CLEANUP--------------------------------------
        (0x000001c4)...UnloadKeyObjects()

        C:\>

## <a name="setup-discrete-tpm-dtpm"></a><span data-ttu-id="a54d7-113">设置离散 TPM (dTPM)</span><span class="sxs-lookup"><span data-stu-id="a54d7-113">Setup discrete TPM (dTPM)</span></span>
<span data-ttu-id="a54d7-114">以下说明适用于 MBM、RPi2 或 RPi3 上受支持的任何 dTPM 模块。</span><span class="sxs-lookup"><span data-stu-id="a54d7-114">These instructions are applicable for any dTPM module supported on MBM, RPi2, or RPi3.</span></span>

1. <span data-ttu-id="a54d7-115">获取一个离散 TPM 模块，并将其附加到 MBM/RPi2/RPi3。</span><span class="sxs-lookup"><span data-stu-id="a54d7-115">Get a discrete TPM module and attach it to the MBM/RPi2/RPi3.</span></span>
2. <span data-ttu-id="a54d7-116">（适用于 MBM）通过更改以下 UEFI 设置来禁用 fTPM：</span><span class="sxs-lookup"><span data-stu-id="a54d7-116">(Applies to MBM) Disable fTPM by changing the following UEFI settings:</span></span>

        Device Manager -> System Setup -> Security Configuration -> PTT = <Disable>

3. <span data-ttu-id="a54d7-117">（适用于 MBM）通过更改以下 UEFI 设置来启用 dTPM：</span><span class="sxs-lookup"><span data-stu-id="a54d7-117">(Applies to MBM) Enable dTPM by changing the following UEFI settings:</span></span>

        Device Manager -> System Setup -> Security Configuration -> Discrete TPM = <Enable>

4. <span data-ttu-id="a54d7-118">根据选择的离散 TPM 模块，在[此处](https://github.com/ms-iot/security/tree/master/TPM-ACPITABL)标记其匹配的 ACPI 表。</span><span class="sxs-lookup"><span data-stu-id="a54d7-118">Based on your discrete TPM module of choice, identify its matching ACPI table [here](https://github.com/ms-iot/security/tree/master/TPM-ACPITABL).</span></span>
5. <span data-ttu-id="a54d7-119">将该 ACPI 表复制到 MBM/RPi2/RPi3 _C:\Windows\System32\ACPITABL.dat_。</span><span class="sxs-lookup"><span data-stu-id="a54d7-119">Copy that ACPI table to MBM/RPi2/RPi3 _C:\Windows\System32\ACPITABL.dat_.</span></span>
6. <span data-ttu-id="a54d7-120">启用设备上的 testsigning：</span><span class="sxs-lookup"><span data-stu-id="a54d7-120">Enable testsigning on the device:</span></span>

        bcdedit /set {current} integrityservices disable
        bcdedit /set testsigning on

7. <span data-ttu-id="a54d7-121">重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="a54d7-121">Reboot the device.</span></span>
8. <span data-ttu-id="a54d7-122">验证是否已启用正确的 TPM 版本 - 在 Windows IoT 核心版设备上运行 [TPM 2.0 工具](https://github.com/ms-iot/security/tree/master/Urchin/T2T)。</span><span class="sxs-lookup"><span data-stu-id="a54d7-122">Verify you have the right TPM version enabled - run the [TPM 2.0 Tool](https://github.com/ms-iot/security/tree/master/Urchin/T2T) on the Windows IoT Core device.</span></span>

        C:\>t2t.exe -cap

        TBS detected 2.0 discrete TPM (dTPM) using TIS on SPB.
        Capabilities:
        PT_FIXED:
        TPM_PT_FAMILY_INDICATOR = '2.0'
        TPM_PT_LEVEL = 0 (0x00000000)
        TPM_PT_REVISION = 1.16
        TPM_PT_DAY_OF_YEAR = 303 (0x0000012f)
        TPM_PT_YEAR = 2014 (0x000007de)
        TPM_PT_MANUFACTURER = 'NTZ'
        TPM_PT_VENDOR_STRING = 'NTZ'
        TPM_PT_VENDOR_TPM_TYPE = 17 (0x00000011)
        TPM_PT_FIRMWARE_VERSION_1 = 4.31 (0x4.0x1f)
        TPM_PT_FIRMWARE_VERSION_2 = 5378.4617 (0x1502.0x1209)
        TPM_PT_INPUT_BUFFER = 2220 (0x000008ac)
        TPM_PT_HR_TRANSIENT_MIN = 4 (0x00000004)
        TPM_PT_HR_PERSISTENT_MIN = 7 (0x00000007)
        TPM_PT_HR_LOADED_MIN = 4 (0x00000004)
        TPM_PT_ACTIVE_SESSIONS_MAX = 64 (0x00000040)
        TPM_PT_PCR_COUNT = 24 (0x00000018)
        TPM_PT_PCR_SELECT_MIN = 3 (0x00000003)
        TPM_PT_CONTEXT_GAP_MAX = 65535 (0x0000ffff)
        TPM_PT_NV_COUNTERS_MAX = 0 (0x00000000)
        TPM_PT_NV_INDEX_MAX = 1639 (0x00000667)
        TPM_PT_MEMORY = objectCopiedToRam
        TPM_PT_CLOCK_UPDATE = 4096000ms
        TPM_PT_CONTEXT_HASH = TPM_ALG_SHA256
        TPM_PT_CONTEXT_SYM = TPM_ALG_AES
        TPM_PT_CONTEXT_SYM_SIZE = 128 (0x00000080)
        TPM_PT_ORDERLY_COUNT = 255 (0x000000ff)
        TPM_PT_MAX_COMMAND_SIZE = 2220 (0x000008ac)
        TPM_PT_MAX_RESPONSE_SIZE = 2220 (0x000008ac)
        TPM_PT_MAX_DIGEST = 32 (0x00000020)
        TPM_PT_MAX_SESSION_CONTEXT = 244 (0x000000f4)
        TPM_PT_PS_FAMILY_INDICATOR = TPM_PS_PDA
        TPM_PT_PS_LEVEL = 0 (0x00000000)
        TPM_PT_PS_REVISION = 25600
        TPM_PT_PS_DAY_OF_YEAR = 0 (0x00000000)
        TPM_PT_PS_YEAR = 0 (0x00000000)
        TPM_PT_SPLIT_MAX = 128 (0x00000080)
        TPM_PT_TOTAL_COMMANDS = 101 (0x00000065)
        TPM_PT_LIBRARY_COMMANDS = 99 (0x00000063)
        TPM_PT_VENDOR_COMMANDS = 2 (0x00000002)
        TPM_PT_NV_BUFFER_MAX = 1639 (0x00000667)

        PT_VAR:
        TPM_PT_STARTUP_CLEAR = phEnable shEnable ehEnable ehEnableNV
        TPM_PT_HR_NV_INDEX = 2 (0x00000002)
        TPM_PT_HR_LOADED = 0 (0x00000000)
        TPM_PT_HR_LOADED_AVAIL = 4 (0x00000004)
        TPM_PT_HR_ACTIVE = 0 (0x00000000)
        TPM_PT_HR_ACTIVE_AVAIL = 64 (0x00000040)
        TPM_PT_HR_TRANSIENT_AVAIL = 4 (0x00000004)
        TPM_PT_HR_PERSISTENT = 3 (0x00000003)
        TPM_PT_HR_PERSISTENT_AVAIL = 4 (0x00000004)
        TPM_PT_NV_COUNTERS = 2 (0x00000002)
        TPM_PT_NV_COUNTERS_AVAIL = 30 (0x0000001e)
        TPM_PT_ALGORITHM_SET = 0 (0x00000000)
        TPM_PT_LOADED_CURVES = 3 (0x00000003)
        TPM_PT_LOCKOUT_COUNTER = 0 (0x00000000)
        TPM_PT_MAX_AUTH_FAIL = 32 (0x00000020)
        TPM_PT_LOCKOUT_INTERVAL = 2h 0" 0'
        TPM_PT_LOCKOUT_RECOVERY = 24h 0" 0'
        TPM_PT_NV_WRITE_RECOVERY = 0ms
        TPM_PT_AUDIT_COUNTER = 0

        C:\>

9. <span data-ttu-id="a54d7-123">验证 dTPM 是否正常工作 - 在 Windows IoT 核心版设备上运行 [Urchin 单元测试](https://github.com/ms-iot/security/tree/master/Urchin/UrchinTest)。</span><span class="sxs-lookup"><span data-stu-id="a54d7-123">Verify dTPM is functioning - run the [Urchin Unit Tests](https://github.com/ms-iot/security/tree/master/Urchin/UrchinTest) on the Windows IoT Core device.</span></span>  
    <span data-ttu-id="a54d7-124">应查看多个通过测试（请注意，某些功能可能不受 dTPM 支持，因此预计会出现多个错误代码）：</span><span class="sxs-lookup"><span data-stu-id="a54d7-124">You should see several PASS tests (note that some of the functionality may not be supported by the dTPM, so a few error codes are expected):</span></span>

        C:\>urchintest.exe

        ---SETUP----------------------------------------
        PASS...........CreateAuthorities()
        PASS...........CreateEkObject()
        PASS...........CreateSrkObject()
        PASS...........CreateAndLoadAikObject()
        PASS...........CreateAndLoadKeyObject()

        ---TESTS----------------------------------------
        PASS...........TestGetCapability()
        PASS...........TestGetEntropy()
        PASS...........TestPolicySession()
        PASS...........TestSignWithPW()
        PASS...........TestSignHMAC()
        PASS...........TestSignBound()
        PASS...........TestSignSalted()
        PASS...........TestSignSaltedAndBound()
        (0xc000000d)...TestSignParameterEncryption()
        PASS...........TestSignParameterDecryption()
        PASS...........TestReadPcrWithEkSeededSession()
        PASS...........TestCreateHashAndHMAC()
        PASS...........TestCreateHashAndHMACSequence()
        PASS...........TestSymKeyImport()
        (0xc000000d)...TestRsaKeyImport()
        PASS...........TestCredentialActivation()
        PASS...........TestKeyExport()
        (0x00000182)...TestSymEncryption()
        PASS...........TestCertifiedMigration()
        PASS...........TestNVIndexReadWrite()
        (0x80280400)...TestVirtualization()
        PASS...........TestObjectChangeAuth()
        PASS...........TestUnseal()
        PASS...........TestDynamicPolicies()
        PASS...........TestRSADecrypt()
        PASS...........TestECDSASign()
        (0xc000000d)...TestKeyAttestation()
        (0xc000000d)...TestPlatformAttestation()

        ---CLEANUP--------------------------------------
        PASS...........UnloadKeyObjects()

        C:\>

## <a name="enable-and-verify-software-tpm-stpm"></a><span data-ttu-id="a54d7-125">启用和验证软件 TPM (sTPM)</span><span class="sxs-lookup"><span data-stu-id="a54d7-125">Enable and verify software TPM (sTPM)</span></span>  
<span data-ttu-id="a54d7-126">请注意，**sTPM 仅用于开发目的，并不提供任何切实的安全优势**。</span><span class="sxs-lookup"><span data-stu-id="a54d7-126">Note that **sTPM is intended for development purposes only and does not provide any real security benefits**.</span></span>

1. <span data-ttu-id="a54d7-127">（适用于 MBM）通过更改以下 UEFI 设置来禁用 fTPM：</span><span class="sxs-lookup"><span data-stu-id="a54d7-127">(Applies to MBM) Disable fTPM by changing the following UEFI settings:</span></span>

        Device Manager -> System Setup -> Security Configuration -> PTT = <Disable>

2. <span data-ttu-id="a54d7-128">（适用于 MBM）通过更改以下 UEFI 设置来启用 dTPM：</span><span class="sxs-lookup"><span data-stu-id="a54d7-128">(Applies to MBM) Enable dTPM by changing the following UEFI settings:</span></span>

        Device Manager -> System Setup -> Security Configuration -> Discrete TPM = <Enable>

3. <span data-ttu-id="a54d7-129">启用设备上的 testsigning：</span><span class="sxs-lookup"><span data-stu-id="a54d7-129">Enable testsigning on the device:</span></span>

        bcdedit /set {current} integrityservices disable
        bcdedit /set testsigning on

4. <span data-ttu-id="a54d7-130">将 ACPI 表从[此处](https://github.com/ms-iot/security/tree/master/TPM-ACPITABL/fTPMSim)复制到 MBM/RPi2/RPi3 _C:\Windows\System32\ACPITABL.dat_。</span><span class="sxs-lookup"><span data-stu-id="a54d7-130">Copy the ACPI table from [here](https://github.com/ms-iot/security/tree/master/TPM-ACPITABL/fTPMSim) to MBM/RPi2/RPi3 _C:\Windows\System32\ACPITABL.dat_.</span></span>
5. <span data-ttu-id="a54d7-131">重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="a54d7-131">Reboot the device.</span></span>
6. <span data-ttu-id="a54d7-132">验证是否已启用正确的 TPM 版本 - 在 Windows IoT 核心版设备上运行 [TPM 2.0 工具](https://github.com/ms-iot/security/tree/master/Urchin/T2T)。</span><span class="sxs-lookup"><span data-stu-id="a54d7-132">Verify you have the right TPM version enabled - run the [TPM 2.0 Tool](https://github.com/ms-iot/security/tree/master/Urchin/T2T) on the Windows IoT Core device.</span></span>

        C:\>t2t.exe -cap
        TBS detected 2.0 simulated TPM (sTPM).
        Capabilities:
        PT_FIXED:
        TPM_PT_FAMILY_INDICATOR = '2.0'
        TPM_PT_LEVEL = 0 (0x00000000)  
        TPM_PT_REVISION = 1.15
        TPM_PT_DAY_OF_YEAR = 163 (0x000000a3)
        TPM_PT_YEAR = 2014 (0x000007de)
        TPM_PT_MANUFACTURER = 'MSFT'
        TPM_PT_VENDOR_STRING = 'IoT Software TPM'
        TPM_PT_VENDOR_TPM_TYPE = 1 (0x00000001)
        TPM_PT_FIRMWARE_VERSION_1 = 8213.275 (0x2015.0x113)
        TPM_PT_FIRMWARE_VERSION_2 = 21.18466 (0x15.0x4822)
        TPM_PT_INPUT_BUFFER = 1024 (0x00000400)
        TPM_PT_HR_TRANSIENT_MIN = 3 (0x00000003)
        TPM_PT_HR_PERSISTENT_MIN = 2 (0x00000002)
        TPM_PT_HR_LOADED_MIN = 3 (0x00000003)
        TPM_PT_ACTIVE_SESSIONS_MAX = 64 (0x00000040)
        TPM_PT_PCR_COUNT = 24 (0x00000018)
        TPM_PT_PCR_SELECT_MIN = 3 (0x00000003)
        TPM_PT_CONTEXT_GAP_MAX = 65535 (0x0000ffff)
        TPM_PT_NV_COUNTERS_MAX = 0 (0x00000000)
        TPM_PT_NV_INDEX_MAX = 2048 (0x00000800)
        TPM_PT_MEMORY = sharedNV objectCopiedToRam
        TPM_PT_CLOCK_UPDATE = 4096ms
        TPM_PT_CONTEXT_HASH = TPM_ALG_SHA256
        TPM_PT_CONTEXT_SYM = TPM_ALG_AES
        TPM_PT_CONTEXT_SYM_SIZE = 256 (0x00000100)
        TPM_PT_ORDERLY_COUNT = 255 (0x000000ff)
        TPM_PT_MAX_COMMAND_SIZE = 4096 (0x00001000)
        TPM_PT_MAX_RESPONSE_SIZE = 4096 (0x00001000)
        TPM_PT_MAX_DIGEST = 48 (0x00000030)
        TPM_PT_MAX_OBJECT_CONTEXT = 1520 (0x000005f0)
        TPM_PT_MAX_SESSION_CONTEXT = 308 (0x00000134)
        TPM_PT_PS_FAMILY_INDICATOR = TPM_PS_MAIN
        TPM_PT_PS_LEVEL = 0 (0x00000000)
        TPM_PT_PS_REVISION = 0
        TPM_PT_PS_DAY_OF_YEAR = 0 (0x00000000)
        TPM_PT_PS_YEAR = 0 (0x00000000)
        TPM_PT_SPLIT_MAX = 128 (0x00000080)
        TPM_PT_TOTAL_COMMANDS = 106 (0x0000006a)
        TPM_PT_LIBRARY_COMMANDS = 105 (0x00000069)
        TPM_PT_VENDOR_COMMANDS = 1 (0x00000001)

        PT_VAR:
        TPM_PT_PERMANENT = lockoutAuthSet tpmGeneratedEPS
        TPM_PT_STARTUP_CLEAR = phEnable shEnable ehEnable ehEnableNV
        TPM_PT_HR_NV_INDEX = 2 (0x00000002)
        TPM_PT_HR_LOADED = 0 (0x00000000)
        TPM_PT_HR_LOADED_AVAIL = 3 (0x00000003)
        TPM_PT_HR_ACTIVE = 0 (0x00000000)
        TPM_PT_HR_ACTIVE_AVAIL = 64 (0x00000040)
        TPM_PT_HR_TRANSIENT_AVAIL = 3 (0x00000003)
        TPM_PT_HR_PERSISTENT = 3 (0x00000003)
        TPM_PT_HR_PERSISTENT_AVAIL = 5 (0x00000005)
        TPM_PT_NV_COUNTERS = 2 (0x00000002)
        TPM_PT_NV_COUNTERS_AVAIL = 31 (0x0000001f)
        TPM_PT_ALGORITHM_SET = 0 (0x00000000)
        TPM_PT_LOADED_CURVES = 3 (0x00000003)
        TPM_PT_LOCKOUT_COUNTER = 3 (0x00000003)
        TPM_PT_MAX_AUTH_FAIL = 32 (0x00000020)
        TPM_PT_LOCKOUT_INTERVAL = 2h 0" 0'
        TPM_PT_LOCKOUT_RECOVERY = 24h 0" 0'
        TPM_PT_AUDIT_COUNTER = 0

        C:\>

7. <span data-ttu-id="a54d7-133">验证 sTPM 是否正常工作 - 在 Windows IoT 核心版设备上运行 [Urchin 单元测试](https://github.com/ms-iot/security/tree/master/Urchin/UrchinTest)。</span><span class="sxs-lookup"><span data-stu-id="a54d7-133">Verify sTPM is functioning - run the [Urchin Unit Tests](https://github.com/ms-iot/security/tree/master/Urchin/UrchinTest) on the Windows IoT Core device.</span></span>  
   <span data-ttu-id="a54d7-134">应查看多个通过测试（请注意，某些功能并不受 sTPM 支持，因此预计会出现多个错误代码）：</span><span class="sxs-lookup"><span data-stu-id="a54d7-134">You should see several PASS tests (note that some of the functionality is not supported by the sTPM, so a few error codes are expected):</span></span>

        C:\>urchintest.exe
        ---SETUP----------------------------------------
        PASS...........CreateAuthorities()
        PASS...........CreateEkObject()
        PASS...........CreateSrkObject()
        PASS...........CreateAndLoadAikObject()
        PASS...........CreateAndLoadKeyObject()

        ---TESTS----------------------------------------
        PASS...........TestGetCapability()
        PASS...........TestGetEntropy()
        PASS...........TestPolicySession()
        PASS...........TestSignWithPW()
        PASS...........TestSignHMAC()
        PASS...........TestSignBound()
        PASS...........TestSignSalted()
        PASS...........TestSignSaltedAndBound()
        (0xc000000d)...TestSignParameterEncryption()
        PASS...........TestSignParameterDecryption()
        PASS...........TestReadPcrWithEkSeededSession()
        PASS...........TestCreateHashAndHMAC()
        PASS...........TestCreateHashAndHMACSequence()
        PASS...........TestSymKeyImport()
        (0xc000000d)...TestRsaKeyImport()
        PASS...........TestCredentialActivation()
        PASS...........TestKeyExport()
        (0x00000182)...TestSymEncryption()
        PASS...........TestCertifiedMigration()
        PASS...........TestNVIndexReadWrite()
        (0x80280400)...TestVirtualization()
        PASS...........TestObjectChangeAuth()
        PASS...........TestUnseal()
        PASS...........TestDynamicPolicies()
        PASS...........TestECDSASign())
        PASS........
        (0xc000000d)...TestKeyAttestation()
        (0xc000000d)...TestPlatformAttestation()

        ---CLEANUP--------------------------------------
        PASS...........UnloadKeyObjects()

        C:\>
