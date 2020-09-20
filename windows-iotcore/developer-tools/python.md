---
title: Python
author: paulmon
ms.author: paulmon
ms.date: 08/13/2019
ms.topic: article
description: 了解如何在运行 Windows 10 IoT Core 的设备上安装 Python。 有关 x64、x86、ARM32 和 ARM64 的说明，请参阅。 请参阅其他 Python 开发人员资源。
keywords: windows iot, python
ms.openlocfilehash: ac8f18f21d2789b951b6577ba4e80a9ecd7f7ead
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782869"
---
# <a name="python"></a><span data-ttu-id="7b8ce-106">Python</span><span class="sxs-lookup"><span data-stu-id="7b8ce-106">Python</span></span>
<span data-ttu-id="7b8ce-107">Python 是一种脚本语言，常用于系统自动化和机器学习 (ML)。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-107">Python is a scripting language that is popular for system automation and machine learning (ML).</span></span>
<span data-ttu-id="7b8ce-108">可以在 [python.org](https://www.python.org/) 上了解有关 Python 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-108">You can learn more about Python at [python.org](https://www.python.org/).</span></span>

## <a name="using-python-on-x64-or-x86"></a><span data-ttu-id="7b8ce-109">在 x64 或 x86 上使用 Python</span><span class="sxs-lookup"><span data-stu-id="7b8ce-109">Using Python on x64 or x86</span></span>
<span data-ttu-id="7b8ce-110">若要在 Windows IoT Core 上安装 Python，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="7b8ce-110">To install Python on Windows IoT Core:</span></span>
1. <span data-ttu-id="7b8ce-111">下载 Python NuGet 包，然后使用 [PowerShell](../connect-your-device/PowerShell.md)安装这些文件。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-111">Download the Python NuGet package, and then install the files using [PowerShell](../connect-your-device/PowerShell.md).</span></span>

    ```powershell
    $python_zip = "https://globalcdn.nuget.org/packages/python.3.7.4.nupkg"
    if($env:PROCESSOR_ARCHITECTURE -ieq "x86") {
        $python_zip = "https://www.nuget.org/api/v2/package/pythonx86/3.7.4"
    }
    Invoke-WebRequest $python_zip -OutFile c:\data\python.zip
    Expand-Archive C:\data\python.zip -DestinationPath c:\python_temp
    move C:\python_temp\tools c:\python
    rd C:\python_temp -Recurse -Force
    del C:\data\python.zip
    ```

2. <span data-ttu-id="7b8ce-112">将 Python 添加到系统路径。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-112">Add Python to the system path.</span></span>

    ```powershell
    cmd /c 'setx PATH "%PATH%";c:\python;c:\python\scripts /M'
    $env:Path += ";c:\python;c:\python\scripts"
    ```

3. <span data-ttu-id="7b8ce-113">确保已安装 pip 的最新版本</span><span class="sxs-lookup"><span data-stu-id="7b8ce-113">Ensure that the current version of pip is installed</span></span>

    ```powershell
    python -m pip install --upgrade pip
    ```

## <a name="using-python-on-windows-iot-core-arm32"></a><span data-ttu-id="7b8ce-114">在 Windows IoT Core ARM32 上使用 Python</span><span class="sxs-lookup"><span data-stu-id="7b8ce-114">Using Python on Windows IoT Core ARM32</span></span>

<span data-ttu-id="7b8ce-115">若要获取适用于 Windows 的 Python，需自行生成二进制文件。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-115">To get Python for Windows, you will need to build the binaries yourself.</span></span>

1. <span data-ttu-id="7b8ce-116">生成适用于 ARM32 的 Python。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-116">Build Python for ARM32.</span></span>  <span data-ttu-id="7b8ce-117">分支必须是 3.8 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-117">The branch must be 3.8 or greater.</span></span>

    ```cmd
    git clone https://github.com/python/cpython
    cd cpython
    git checkout 3.8
    pcbuild\build.bat -p ARM --no-tkinter
    ```

2. <span data-ttu-id="7b8ce-118">为 Windows IoT Core ARM32 生成 Python .zip 文件。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-118">Build Python .zip file for Windows IoT Core ARM32.</span></span>  <span data-ttu-id="7b8ce-119">必须使用相同版本的 Python 来运行 PC/layout。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-119">The same version of Python must be used to run PC/layout.</span></span> <span data-ttu-id="7b8ce-120">此步骤生成适用于 x86 的 Python，并使用它来生成 .zip 文件。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-120">This step builds Python for x86 and uses it to build the .zip file(s).</span></span>  <span data-ttu-id="7b8ce-121">如果希望标准库测试包含在 .zip 文件中，请添加 `--include-tests` 参数。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-121">If you want the standard library tests in your .zip file add the `--include-tests` parameter.</span></span>

    ```cmd
    REM Build Python for x86 to use for building the .zip file.
    pcbuild\build.bat
    pcbuild\win32\python.exe PC/layout -vv -s "." -b ".\PCBuild\arm32" -t ".\PCBuild\temp" --preset-iot --include-venv --zip ".\PCBuild\arm32\zip\python.zip"

    net use P: \\[ip address]\c$ /user:administrator

    copy .\PCBuild\arm32\zip\python.zip P:\data
    ```

3. <span data-ttu-id="7b8ce-122">使用 [PowerShell](../connect-your-device/PowerShell.md) 提取设备上的 .zip 文件，并将 Python 添加到系统路径。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-122">Use [PowerShell](../connect-your-device/PowerShell.md) to extract the .zip file on the device and add Python to the system path.</span></span>

    ```powershell
    Expand-Archive C:\data\python.zip -DestinationPath c:\python
    cmd /c 'setx PATH "%PATH%";c:\python;c:\python\scripts /M'
    $env:Path += ";c:\python;c:\python\scripts"
    ```

4. <span data-ttu-id="7b8ce-123">验证 `print('Hello World')` 是否正常工作。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-123">Verify that `print('Hello World')` works.</span></span>

    ```powershell
    python -c "print('Hello World!');quit()"
    ```

## <a name="using-python-on-windows-iot-core-arm64"></a><span data-ttu-id="7b8ce-124">在 Windows IoT Core ARM64 上使用 Python</span><span class="sxs-lookup"><span data-stu-id="7b8ce-124">Using Python on Windows IoT Core ARM64</span></span>

<span data-ttu-id="7b8ce-125">若要获取适用于 Windows 的 Python，需自行生成二进制文件。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-125">To get Python for Windows, you will need to build the binaries yourself.</span></span>

1. <span data-ttu-id="7b8ce-126">克隆适用于 ARM32 的 Python，并运行 `get_externals`。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-126">Clone Python for ARM32 and run `get_externals`.</span></span>  <span data-ttu-id="7b8ce-127">分支必须是 3.8 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-127">The branch must be 3.8 or greater.</span></span>

    ```cmd
    git clone https://github.com/python/cpython
    cd cpython
    git checkout 3.8
    pcbuild\get_externals.bat
    cd ..
    ```

2. <span data-ttu-id="7b8ce-128">克隆并生成 libffi。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-128">Clone and build libffi.</span></span>

    ```cmd
    git clone https://github.com/libffi/libffi
    set LIBFFI_SOURCE=%CD%\libffi

    REM Visual Studio 2015 or greater with ARM64 tools installed is required to build Python
    REM the location of VCVARSALL may differ on your machine
    set VCVARSALL="C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\VC\Auxiliary\Build\vcvarsall.bat"

    cd cpython
    if exist c:\cygwin\bin\sh.exe (
        call pcbuild\prepare_libffi.bat -arm64
    ) else (
        call pcbuild\prepare_libffi.bat -arm64 --install-cygwin
    )
    if not exist externals\libffi\arm64\libffi-7.dll echo ERROR: libffi not built! & exit /b 1
    ```

3. <span data-ttu-id="7b8ce-129">生成适用于 ARM64 的 Python。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-129">Build Python for ARM64.</span></span>

    ```cmd
    pcbuild\build.bat -p ARM64 --no-tkinter
    ```

4. <span data-ttu-id="7b8ce-130">为 Windows IoT Core ARM64 生成 Python .zip 文件。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-130">Build Python .zip file for Windows IoT Core ARM64.</span></span>  <span data-ttu-id="7b8ce-131">必须使用相同版本的 Python 来运行 PC/layout。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-131">The same version of Python must be used to run PC/layout.</span></span> <span data-ttu-id="7b8ce-132">此步骤生成适用于 x86 的 Python，并使用它来生成 .zip 文件。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-132">This step builds Python for x86 and uses it to build the .zip file(s).</span></span>  <span data-ttu-id="7b8ce-133">如果希望标准库测试包含在 .zip 文件中，请添加 `--include-tests` 参数。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-133">If you want the standard library tests in your .zip file add the `--include-tests` parameter.</span></span>

    ```cmd
    REM Build Python for x86 to use for building the .zip file.
    pcbuild\build.bat

    REM Map drive to device and copy files using PC/layout
    net use P: \\[ip address]\c$ /user:administrator
    pcbuild\win32\python.exe PC/layout -vv -s "." -b ".\PCBuild\arm64" -t ".\PCBuild\temp" --preset-iot --include-venv --copy P:\python
    ```

3. <span data-ttu-id="7b8ce-134">将 Python 添加到系统路径。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-134">Add Python to the system path.</span></span>

    ```cmd
    setx PATH "%PATH%";c:\python;c:\python\scripts /M
    set PATH=%PATH%;c:\python;c:\python\scripts
    ```

4. <span data-ttu-id="7b8ce-135">验证 `print('Hello World')` 是否正常工作。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-135">Verify that `print('Hello World')` works.</span></span>

    ```cmd
    python -c "print('Hello World!');quit()"
    ```

## <a name="try-out-azure-iot-hub-python-sdks-v2---preview"></a><span data-ttu-id="7b8ce-136">试用 [Azure IoT 中心 Python SDK v2 - 预览版](https://github.com/Azure/azure-iot-sdk-python-preview)</span><span class="sxs-lookup"><span data-stu-id="7b8ce-136">Try out [Azure IoT Hub Python SDKs v2 - PREVIEW](https://github.com/Azure/azure-iot-sdk-python-preview)</span></span>

1. <span data-ttu-id="7b8ce-137">首先安装 SDK。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-137">First install the SDK.</span></span>

    ```cmd
    python -m pip install azure-iot-device
    ```

<span data-ttu-id="7b8ce-138">在 `pip install` 的输出中可能有错误：`Download error on https://pypi.org/simple/pbr/`。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-138">In the output for the `pip install` there may be errors: `Download error on https://pypi.org/simple/pbr/`.</span></span> <span data-ttu-id="7b8ce-139">如果出现此错误，请继续执行下面的步骤，否则请跳到 `Set up an IoT Hub and create a Device Identity`：</span><span class="sxs-lookup"><span data-stu-id="7b8ce-139">If you see this then, otherwise skip to `Set up an IoT Hub and create a Device Identity`:</span></span>

2. <span data-ttu-id="7b8ce-140">在你喜爱的浏览器中导航到 `https://pypi.org/simple/pbr/`。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-140">Navigate to `https://pypi.org/simple/pbr/` in your favorite browser.</span></span> <span data-ttu-id="7b8ce-141">检查网站的证书并注意到它是由 `DigiCert` 颁发的。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-141">Inspect the web site's certificate and noticed that it issued by `DigiCert`.</span></span>

3. <span data-ttu-id="7b8ce-142">创建名为 `c:\test` 的目录。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-142">Create a directory named `c:\test`.</span></span>

4. <span data-ttu-id="7b8ce-143">在桌面 Windows 计算机上从命令提示符运行 `certmgr.msc`。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-143">Run `certmgr.msc` from a command prompt on a desktop Windows machine.</span></span>  

5. <span data-ttu-id="7b8ce-144">在树视图中导航到 `Trusted Root Certification Authorities`。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-144">Navigate to `Trusted Root Certification Authorities` in the treeview.</span></span>  <span data-ttu-id="7b8ce-145">展开该节点，然后选择 `Certificates`。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-145">Expand the node and choose `Certificates`.</span></span>

6. <span data-ttu-id="7b8ce-146">在右窗格中找到 `DigiCert High Assurance EV Root`，右键单击并选择“`All Tasks`” > “`Export`”。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-146">In the right pane find the `DigiCert High Assurance EV Root`, right-click and select `All Tasks` > `Export`.</span></span>  <span data-ttu-id="7b8ce-147">请注意，有多个 `DigiCert` 证书，请通过尝试每个证书（一次一个）来识别此证书。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-147">Note that there are multiple `DigiCert` certs and I identified this one by trying each one, one at a time.</span></span>

7. <span data-ttu-id="7b8ce-148">在弹出的对话框中，单击 `Next`。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-148">In the dialog that pops up click `Next`.</span></span>

8. <span data-ttu-id="7b8ce-149">选择 `DER encoded binary X.509 (.CER)`（这应该是默认值），然后单击 `Next`。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-149">Select `DER encoded binary X.509 (.CER)` (this should be the default) and click `Next`.</span></span>

9. <span data-ttu-id="7b8ce-150">在 `File name:` 编辑框中键入 `c:\test\DigiCert High Assurance EV Root.cer`</span><span class="sxs-lookup"><span data-stu-id="7b8ce-150">In the `File name:` edit box type `c:\test\DigiCert High Assurance EV Root.cer`</span></span>

![证书导出向导](../media/Python/global_sign_cert.png)

10. <span data-ttu-id="7b8ce-152">单击 `Next`。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-152">Click `Next`.</span></span>

11. <span data-ttu-id="7b8ce-153">单击 `Finish`。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-153">Click `Finish`.</span></span>

12. <span data-ttu-id="7b8ce-154">在台式计算机上运行以下命令以将 `c:\test\DigiCert High Assurance EV Root.cer` 复制到设备：</span><span class="sxs-lookup"><span data-stu-id="7b8ce-154">Copy `c:\test\DigiCert High Assurance EV Root.cer` to the device by running the following command on your desktop machine:</span></span>

    ```cmd
    net use X: \\host\c$ /user:host\administrator
    md X:\test
    copy "c:\test\GlobalSign Root CA.cer" X:\test
    ```

13. <span data-ttu-id="7b8ce-155">在设备上，使用 [PowerShell](../connect-your-device/PowerShell.md)将证书导入根存储。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-155">On the device, import the certificate into the root store using [PowerShell](../connect-your-device/PowerShell.md).</span></span>

    ```cmd
    certmgr -add "c:\test\DigiCert High Assurance EV Root.cer" -s root -r localMachine -c
    certmgr -add "c:\test\GlobalSign Root CA.cer" -s root -r localMachine -c
    ```

14. <span data-ttu-id="7b8ce-156">再次尝试安装 `azure-iot-device`</span><span class="sxs-lookup"><span data-stu-id="7b8ce-156">Try to install the `azure-iot-device` again</span></span>

    ``` cmd
    python -m pip install azure-iot-device --no-color
    ```

15.  <span data-ttu-id="7b8ce-157">在 `pip install` 的输出中可能有错误：`Download error for https://files.pythonhosted.org/`。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-157">In the output for the `pip install` there may be errors: `Download error for https://files.pythonhosted.org/`.</span></span>  <span data-ttu-id="7b8ce-158">如果看不到此，请跳到 `Set up an IoT Hub and create a Device Identity`</span><span class="sxs-lookup"><span data-stu-id="7b8ce-158">If you don't see this, then skip to `Set up an IoT Hub and create a Device Identity`</span></span>

16. <span data-ttu-id="7b8ce-159">在你喜爱的浏览器中导航到 `https://files.pythonhosted.org/`。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-159">Navigate to `https://files.pythonhosted.org/` in your favorite browser.</span></span> <span data-ttu-id="7b8ce-160">检查网站的证书并注意到它是由 `GlobalSign` 颁发的。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-160">Inspect the web site's certificate and noticed that it issued by `GlobalSign`.</span></span>

17. <span data-ttu-id="7b8ce-161">重复上述步骤，以便从桌面计算机中导出 `GlobalSign Root CA` 证书，并将其导入到设备。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-161">Repeat the steps to export the `GlobalSign Root CA` certificate from your desktop machine and import it on the device.</span></span>

18. <span data-ttu-id="7b8ce-162">再次尝试安装 `azure-iot-device`。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-162">Try to install the `azure-iot-device` again.</span></span>

### <a name="set-up-an-iot-hub-and-create-a-device-identity"></a><span data-ttu-id="7b8ce-163">设置 IoT 中心并创建设备标识</span><span class="sxs-lookup"><span data-stu-id="7b8ce-163">Set up an IoT Hub and create a Device Identity</span></span>

19. <span data-ttu-id="7b8ce-164">安装 [Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)（或使用 [Azure Cloud Shell](https://shell.azure.com/)）并使用它来创建 [Azure IoT 中心](https://docs.microsoft.com/cli/azure/iot/hub?view=azure-cli-latest#az-iot-hub-create)。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-164">Install the [Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) (or use the [Azure Cloud Shell](https://shell.azure.com/)) and use it to [create an Azure IoT Hub](https://docs.microsoft.com/cli/azure/iot/hub?view=azure-cli-latest#az-iot-hub-create).</span></span>

    ```powershell
    az iot hub create --resource-group <your resource group> --name <your IoT Hub name>
    ```
    * <span data-ttu-id="7b8ce-165">请注意，此操作可能需要几分钟的时间。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-165">Note that this operation may take a few minutes.</span></span>

20. <span data-ttu-id="7b8ce-166">将 IoT 扩展添加到 Azure CLI，然后[注册设备标识](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-create)</span><span class="sxs-lookup"><span data-stu-id="7b8ce-166">Add the IoT Extension to the Azure CLI, and then [register a device identity](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-create)</span></span>

    ```powershell
    az extension add --name azure-cli-iot-ext
    az iot hub device-identity create --hub-name <your IoT Hub name> --device-id <your device id>
    ```

21. <span data-ttu-id="7b8ce-167">使用 Azure CLI [检索设备连接字符串](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-show-connection-string)</span><span class="sxs-lookup"><span data-stu-id="7b8ce-167">[Retrieve your Device Connection String](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-show-connection-string) using the Azure CLI</span></span>

    ```powershell
    az iot hub device-identity show-connection-string --device-id <your device id> --hub-name <your IoT Hub name>
    ```

    <span data-ttu-id="7b8ce-168">它应采用以下格式：</span><span class="sxs-lookup"><span data-stu-id="7b8ce-168">It should be in the format:</span></span>
    ```
    HostName=<your IoT Hub name>.azure-devices.net;DeviceId=<your device id>;SharedAccessKey=<some value>
    ```

### <a name="send-a-simple-telemetry-message"></a><span data-ttu-id="7b8ce-169">发送简单的遥测消息</span><span class="sxs-lookup"><span data-stu-id="7b8ce-169">Send a simple telemetry message</span></span>

22. <span data-ttu-id="7b8ce-170">使用 Azure CLI [开始监视 IoT 中心上的遥测数据](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-monitor-events)</span><span class="sxs-lookup"><span data-stu-id="7b8ce-170">[Begin monitoring for telemetry](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-monitor-events) on your IoT Hub using the Azure CLI</span></span>

    ```powershell
    az iot hub monitor-events --hub-name <your IoT Hub name> --output table
    ```

23. <span data-ttu-id="7b8ce-171">在设备上，将设备连接字符串设置为名为的环境变量 `IOTHUB_DEVICE_CONNECTION_STRING` 。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-171">On your device, set the Device Connection String as an environment variable called `IOTHUB_DEVICE_CONNECTION_STRING`.</span></span>

    ```cmd
    REM NOTE: there are no quotes
    set IOTHUB_DEVICE_CONNECTION_STRING=<your connection string here>
    ```

24. <span data-ttu-id="7b8ce-172">复制 simple_send_d2c_message py 并在设备上运行它。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-172">Copy simple_send_d2c_message.py and run it on the device.</span></span>

    ```cmd
    cmd /c "if not exist c:\test md c:\test"
    REM copy simple_send_d2c_message.py from https://github.com/Azure/azure-iot-sdk-python-preview/blob/master/azure-iot-device/samples/simple_send_d2c_message.py to c:\test on the device
    python c:\test\simple_send_d2c_message.py
    ```

## <a name="using-python-in-an-x64-docker-container-on-windows-iot-core"></a><span data-ttu-id="7b8ce-173">在 Windows IoT Core 上的 x64 docker 容器中使用 Python</span><span class="sxs-lookup"><span data-stu-id="7b8ce-173">Using Python in an x64 docker container on Windows IoT Core</span></span>

1. <span data-ttu-id="7b8ce-174">下载最新的 docker，并安装文件。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-174">Download the newest docker, and install files.</span></span>

    ```powershell
    Invoke-WebRequest https://master.dockerproject.org/windows/x86_64/docker.zip -OutFile c:\data\docker.zip
    Expand-Archive c:\data\docker.zip -DestinationPath c:\data
    move c:\data\docker\docker*exe c:\windows\system32
    Remove-Item c:\data\docker -Recurse -Force
    dockerd --register-service
    net start docker
    ```

2.  <span data-ttu-id="7b8ce-175">创建 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="7b8ce-175">Create Dockerfile</span></span>
    ```
    # escape = `
    FROM mcr.microsoft.com/windows/nanoserver:1809-amd64

    # Get Python
    ADD "https://globalcdn.nuget.org/packages/python.3.7.4.nupkg" .\temp\py.zip

    COPY test test
    COPY certmgr.exe c:\windows\system32

    # need admin for setx and certmgr
    USER ContainerAdministrator

    # Extract Python
    RUN tar -xf c:\temp\py.zip -C c:\temp && `
        move c:\temp\tools c:\ && `
        ren tools python && `
        RD c:\temp /s/q && `
        setx PATH "%PATH%";c:\python;c:\python\scripts /M

    RUN dir c:\test\*.cer /s/b > c:\test\certs.txt && `
        for /f "delims==" %i in (c:\test\certs.txt) do certmgr -add "%i" -s root -r localMachine -c < c:\test\1.txt

    USER ContainerUser

    RUN python -m pip install --upgrade pip && `
        python -m pip install azure-iot-device

    CMD cmd /k c:\test\start.cmd
    ```

3. <span data-ttu-id="7b8ce-176">将 Dockerfile 复制到设备上的 c:\docker。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-176">Copy Dockerfile to c:\docker on device.</span></span> <span data-ttu-id="7b8ce-177">此外，将所有证书复制到 P:\docker\test。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-177">Also copy any certificates to P:\docker\test.</span></span>  <span data-ttu-id="7b8ce-178">1.txt 是一个文件，其中包含数字1和回车符。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-178">1.txt is a file with the number 1 and a carriage return.</span></span>

    ```cmd
    net use P: \\[device IP address]\c$ /user:administrator
    md P:\docker\test
    copy Dockerfile P:\docker
    copy AppCertificates\*.cer P:\docker\test
    copy 1.txt P:\docker\test
    ```

4.  <span data-ttu-id="7b8ce-179">使用 SSH 连接到设备。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-179">Connect to the device using SSH.</span></span>  <span data-ttu-id="7b8ce-180">远程 PowerShell 对于交互式 docker 会话不起作用。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-180">Remote PowerShell will not work for an interactive docker session.</span></span>

    ```powershell
    docker build --isolation==process . -t python
    docker run --isolation==process python
    ```

5. <span data-ttu-id="7b8ce-181">输出 hello world</span><span class="sxs-lookup"><span data-stu-id="7b8ce-181">Print hello world</span></span>

    ```
    python -c "print('Hello Python in Containers!')"
    ```

6. <span data-ttu-id="7b8ce-182">请参阅上面的 Azure IoT SDK 指导内容以便测试云到设备的消息。</span><span class="sxs-lookup"><span data-stu-id="7b8ce-182">See Azure IoT SDK directions above to test cloud to device messages.</span></span>

## <a name="additional-python-developer-resources"></a><span data-ttu-id="7b8ce-183">其他 Python 开发人员资源</span><span class="sxs-lookup"><span data-stu-id="7b8ce-183">Additional Python Developer Resources</span></span>
- [<span data-ttu-id="7b8ce-184">Python 开发人员指南</span><span class="sxs-lookup"><span data-stu-id="7b8ce-184">Python Developer's Guide</span></span>](https://devguide.python.org/setup/#setup)
- [<span data-ttu-id="7b8ce-185">在 Windows 上生成 CPython</span><span class="sxs-lookup"><span data-stu-id="7b8ce-185">Build CPython on Windows</span></span>](https://cpython-core-tutorial.readthedocs.io/en/latest/build_cpython_windows.html)

