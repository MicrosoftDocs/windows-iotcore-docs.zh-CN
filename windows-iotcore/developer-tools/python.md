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
# <a name="python"></a>Python
Python 是一种脚本语言，常用于系统自动化和机器学习 (ML)。
可以在 [python.org](https://www.python.org/) 上了解有关 Python 的详细信息。

## <a name="using-python-on-x64-or-x86"></a>在 x64 或 x86 上使用 Python
若要在 Windows IoT Core 上安装 Python，请执行以下操作：
1. 下载 Python NuGet 包，然后使用 [PowerShell](../connect-your-device/PowerShell.md)安装这些文件。

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

2. 将 Python 添加到系统路径。

    ```powershell
    cmd /c 'setx PATH "%PATH%";c:\python;c:\python\scripts /M'
    $env:Path += ";c:\python;c:\python\scripts"
    ```

3. 确保已安装 pip 的最新版本

    ```powershell
    python -m pip install --upgrade pip
    ```

## <a name="using-python-on-windows-iot-core-arm32"></a>在 Windows IoT Core ARM32 上使用 Python

若要获取适用于 Windows 的 Python，需自行生成二进制文件。

1. 生成适用于 ARM32 的 Python。  分支必须是 3.8 版或更高版本。

    ```cmd
    git clone https://github.com/python/cpython
    cd cpython
    git checkout 3.8
    pcbuild\build.bat -p ARM --no-tkinter
    ```

2. 为 Windows IoT Core ARM32 生成 Python .zip 文件。  必须使用相同版本的 Python 来运行 PC/layout。 此步骤生成适用于 x86 的 Python，并使用它来生成 .zip 文件。  如果希望标准库测试包含在 .zip 文件中，请添加 `--include-tests` 参数。

    ```cmd
    REM Build Python for x86 to use for building the .zip file.
    pcbuild\build.bat
    pcbuild\win32\python.exe PC/layout -vv -s "." -b ".\PCBuild\arm32" -t ".\PCBuild\temp" --preset-iot --include-venv --zip ".\PCBuild\arm32\zip\python.zip"

    net use P: \\[ip address]\c$ /user:administrator

    copy .\PCBuild\arm32\zip\python.zip P:\data
    ```

3. 使用 [PowerShell](../connect-your-device/PowerShell.md) 提取设备上的 .zip 文件，并将 Python 添加到系统路径。

    ```powershell
    Expand-Archive C:\data\python.zip -DestinationPath c:\python
    cmd /c 'setx PATH "%PATH%";c:\python;c:\python\scripts /M'
    $env:Path += ";c:\python;c:\python\scripts"
    ```

4. 验证 `print('Hello World')` 是否正常工作。

    ```powershell
    python -c "print('Hello World!');quit()"
    ```

## <a name="using-python-on-windows-iot-core-arm64"></a>在 Windows IoT Core ARM64 上使用 Python

若要获取适用于 Windows 的 Python，需自行生成二进制文件。

1. 克隆适用于 ARM32 的 Python，并运行 `get_externals`。  分支必须是 3.8 版或更高版本。

    ```cmd
    git clone https://github.com/python/cpython
    cd cpython
    git checkout 3.8
    pcbuild\get_externals.bat
    cd ..
    ```

2. 克隆并生成 libffi。

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

3. 生成适用于 ARM64 的 Python。

    ```cmd
    pcbuild\build.bat -p ARM64 --no-tkinter
    ```

4. 为 Windows IoT Core ARM64 生成 Python .zip 文件。  必须使用相同版本的 Python 来运行 PC/layout。 此步骤生成适用于 x86 的 Python，并使用它来生成 .zip 文件。  如果希望标准库测试包含在 .zip 文件中，请添加 `--include-tests` 参数。

    ```cmd
    REM Build Python for x86 to use for building the .zip file.
    pcbuild\build.bat

    REM Map drive to device and copy files using PC/layout
    net use P: \\[ip address]\c$ /user:administrator
    pcbuild\win32\python.exe PC/layout -vv -s "." -b ".\PCBuild\arm64" -t ".\PCBuild\temp" --preset-iot --include-venv --copy P:\python
    ```

3. 将 Python 添加到系统路径。

    ```cmd
    setx PATH "%PATH%";c:\python;c:\python\scripts /M
    set PATH=%PATH%;c:\python;c:\python\scripts
    ```

4. 验证 `print('Hello World')` 是否正常工作。

    ```cmd
    python -c "print('Hello World!');quit()"
    ```

## <a name="try-out-azure-iot-hub-python-sdks-v2---preview"></a>试用 [Azure IoT 中心 Python SDK v2 - 预览版](https://github.com/Azure/azure-iot-sdk-python-preview)

1. 首先安装 SDK。

    ```cmd
    python -m pip install azure-iot-device
    ```

在 `pip install` 的输出中可能有错误：`Download error on https://pypi.org/simple/pbr/`。 如果出现此错误，请继续执行下面的步骤，否则请跳到 `Set up an IoT Hub and create a Device Identity`：

2. 在你喜爱的浏览器中导航到 `https://pypi.org/simple/pbr/`。 检查网站的证书并注意到它是由 `DigiCert` 颁发的。

3. 创建名为 `c:\test` 的目录。

4. 在桌面 Windows 计算机上从命令提示符运行 `certmgr.msc`。  

5. 在树视图中导航到 `Trusted Root Certification Authorities`。  展开该节点，然后选择 `Certificates`。

6. 在右窗格中找到 `DigiCert High Assurance EV Root`，右键单击并选择“`All Tasks`” > “`Export`”。  请注意，有多个 `DigiCert` 证书，请通过尝试每个证书（一次一个）来识别此证书。

7. 在弹出的对话框中，单击 `Next`。

8. 选择 `DER encoded binary X.509 (.CER)`（这应该是默认值），然后单击 `Next`。

9. 在 `File name:` 编辑框中键入 `c:\test\DigiCert High Assurance EV Root.cer`

![证书导出向导](../media/Python/global_sign_cert.png)

10. 单击 `Next`。

11. 单击 `Finish`。

12. 在台式计算机上运行以下命令以将 `c:\test\DigiCert High Assurance EV Root.cer` 复制到设备：

    ```cmd
    net use X: \\host\c$ /user:host\administrator
    md X:\test
    copy "c:\test\GlobalSign Root CA.cer" X:\test
    ```

13. 在设备上，使用 [PowerShell](../connect-your-device/PowerShell.md)将证书导入根存储。

    ```cmd
    certmgr -add "c:\test\DigiCert High Assurance EV Root.cer" -s root -r localMachine -c
    certmgr -add "c:\test\GlobalSign Root CA.cer" -s root -r localMachine -c
    ```

14. 再次尝试安装 `azure-iot-device`

    ``` cmd
    python -m pip install azure-iot-device --no-color
    ```

15.  在 `pip install` 的输出中可能有错误：`Download error for https://files.pythonhosted.org/`。  如果看不到此，请跳到 `Set up an IoT Hub and create a Device Identity`

16. 在你喜爱的浏览器中导航到 `https://files.pythonhosted.org/`。 检查网站的证书并注意到它是由 `GlobalSign` 颁发的。

17. 重复上述步骤，以便从桌面计算机中导出 `GlobalSign Root CA` 证书，并将其导入到设备。

18. 再次尝试安装 `azure-iot-device`。

### <a name="set-up-an-iot-hub-and-create-a-device-identity"></a>设置 IoT 中心并创建设备标识

19. 安装 [Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)（或使用 [Azure Cloud Shell](https://shell.azure.com/)）并使用它来创建 [Azure IoT 中心](https://docs.microsoft.com/cli/azure/iot/hub?view=azure-cli-latest#az-iot-hub-create)。

    ```powershell
    az iot hub create --resource-group <your resource group> --name <your IoT Hub name>
    ```
    * 请注意，此操作可能需要几分钟的时间。

20. 将 IoT 扩展添加到 Azure CLI，然后[注册设备标识](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-create)

    ```powershell
    az extension add --name azure-cli-iot-ext
    az iot hub device-identity create --hub-name <your IoT Hub name> --device-id <your device id>
    ```

21. 使用 Azure CLI [检索设备连接字符串](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-show-connection-string)

    ```powershell
    az iot hub device-identity show-connection-string --device-id <your device id> --hub-name <your IoT Hub name>
    ```

    它应采用以下格式：
    ```
    HostName=<your IoT Hub name>.azure-devices.net;DeviceId=<your device id>;SharedAccessKey=<some value>
    ```

### <a name="send-a-simple-telemetry-message"></a>发送简单的遥测消息

22. 使用 Azure CLI [开始监视 IoT 中心上的遥测数据](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-monitor-events)

    ```powershell
    az iot hub monitor-events --hub-name <your IoT Hub name> --output table
    ```

23. 在设备上，将设备连接字符串设置为名为的环境变量 `IOTHUB_DEVICE_CONNECTION_STRING` 。

    ```cmd
    REM NOTE: there are no quotes
    set IOTHUB_DEVICE_CONNECTION_STRING=<your connection string here>
    ```

24. 复制 simple_send_d2c_message py 并在设备上运行它。

    ```cmd
    cmd /c "if not exist c:\test md c:\test"
    REM copy simple_send_d2c_message.py from https://github.com/Azure/azure-iot-sdk-python-preview/blob/master/azure-iot-device/samples/simple_send_d2c_message.py to c:\test on the device
    python c:\test\simple_send_d2c_message.py
    ```

## <a name="using-python-in-an-x64-docker-container-on-windows-iot-core"></a>在 Windows IoT Core 上的 x64 docker 容器中使用 Python

1. 下载最新的 docker，并安装文件。

    ```powershell
    Invoke-WebRequest https://master.dockerproject.org/windows/x86_64/docker.zip -OutFile c:\data\docker.zip
    Expand-Archive c:\data\docker.zip -DestinationPath c:\data
    move c:\data\docker\docker*exe c:\windows\system32
    Remove-Item c:\data\docker -Recurse -Force
    dockerd --register-service
    net start docker
    ```

2.  创建 Dockerfile
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

3. 将 Dockerfile 复制到设备上的 c:\docker。 此外，将所有证书复制到 P:\docker\test。  1.txt 是一个文件，其中包含数字1和回车符。

    ```cmd
    net use P: \\[device IP address]\c$ /user:administrator
    md P:\docker\test
    copy Dockerfile P:\docker
    copy AppCertificates\*.cer P:\docker\test
    copy 1.txt P:\docker\test
    ```

4.  使用 SSH 连接到设备。  远程 PowerShell 对于交互式 docker 会话不起作用。

    ```powershell
    docker build --isolation==process . -t python
    docker run --isolation==process python
    ```

5. 输出 hello world

    ```
    python -c "print('Hello Python in Containers!')"
    ```

6. 请参阅上面的 Azure IoT SDK 指导内容以便测试云到设备的消息。

## <a name="additional-python-developer-resources"></a>其他 Python 开发人员资源
- [Python 开发人员指南](https://devguide.python.org/setup/#setup)
- [在 Windows 上生成 CPython](https://cpython-core-tutorial.readthedocs.io/en/latest/build_cpython_windows.html)

