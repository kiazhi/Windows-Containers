# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is NanoServerAPIScan?

NanoServerApiScan.exe scans a directory containing your binaries and reports an error if it finds an API that is not available in Nano Server. It even provides replacement API suggestions in many cases. NanoServerApiScan.exe requires .NET Framework version 4.0 or higher. For more details, follow this [link](https://blogs.technet.microsoft.com/nanoserver/2016/04/27/nanoserverapiscan-exe-updated-for-tp5/).

For a list of available Nano Server APIs, please kindly refer to this [link](https://msdn.microsoft.com/en-us/library/mt588480(v=vs.85).aspx).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | Windows SDK Version | Dockerfile |
| -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.apiscan/tags/) | [sac2016](https://hub.docker.com/r/microsoft/windowsservercore/tags/) | [10.0.17134.0](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/apiscan/sac2016-10.0.17134.0/Dockerfile) |
| [1709-10.0.17134.0](https://hub.docker.com/r/kiazhi/nanoserver.apiscan/tags/) | [1709](https://hub.docker.com/r/microsoft/windowsservercore/tags/) | [10.0.17134.0](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/apiscan/1709-10.0.17134.0/Dockerfile) |
| [sac2016-10.0.17134.0](https://hub.docker.com/r/kiazhi/nanoserver.apiscan/tags/) | [sac2016](https://hub.docker.com/r/microsoft/windowsservercore/tags/) | [10.0.17134.0](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/apiscan/sac2016-10.0.17134.0/Dockerfile) |
| [1709-10.0.16299.91](https://hub.docker.com/r/kiazhi/nanoserver.apiscan/tags/) | [1709](https://hub.docker.com/r/microsoft/windowsservercore/tags/) | [10.0.16299.91](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/apiscan/1709-10.0.16299.91/Dockerfile) |
| [sac2016-10.0.16299.91](https://hub.docker.com/r/kiazhi/nanoserver.apiscan/tags/) | [sac2016](https://hub.docker.com/r/microsoft/windowsservercore/tags/) | [10.0.16299.91](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/apiscan/sac2016-10.0.16299.91/Dockerfile) |
| [1709-10.0.15063.468](https://hub.docker.com/r/kiazhi/nanoserver.apiscan/tags/) | [1709](https://hub.docker.com/r/microsoft/windowsservercore/tags/) | [10.0.15063.468](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/apiscan/1709-10.0.15063.468/Dockerfile) |
| [sac2016-10.0.15063.468](https://hub.docker.com/r/kiazhi/nanoserver.apiscan/tags/) | [sac2016](https://hub.docker.com/r/microsoft/windowsservercore/tags/) | [10.0.15063.468](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/apiscan/sac2016-10.0.15063.468/Dockerfile) |
| [1709-10.0.14393.795](https://hub.docker.com/r/kiazhi/nanoserver.apiscan/tags/) | [1709](https://hub.docker.com/r/microsoft/windowsservercore/tags/) | [10.0.14393.795](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/apiscan/1709-10.0.14393.795/Dockerfile) |
| [sac2016-10.0.14393.795](https://hub.docker.com/r/kiazhi/nanoserver.apiscan/tags/) | [sac2016](https://hub.docker.com/r/microsoft/windowsservercore/tags/) | [10.0.14393.795](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/apiscan/sac2016-10.0.14393.795/Dockerfile) |


# Getting Started with NanoServerAPIScan for Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.apiscan
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.apiscan
    ```


- Step 4 - Verify NanoServerApiScan help documentation within the container interactively:

    ```shell
    NanoServerApiScan /?
    ```


- Step 5 - Exit from the container:

    ```shell
    exit
    ```

- Step 6 - Copy files that will be assessed by NanoServerApiScan within the container interactively:

    - Create a container using the `kiazhi\nanoserver.apiscan` image
    - Copy those local binary files to container C:\NanoServerAPIScan\Binary folder
    - Start the container interactively

    ```shell
    docker create --name NanoServerAPIScan -t -i nanoserver.apiscan
    docker cp /BinaryFilesFolderForScanning NanoServerAPIScan:/NanoServerAPIScan/Binary
    docker start -a -i NanoServerAPIScan

    ```
    
    - Execute the `NanoServerApiScan.exe` executable against 
    `C:\NanoServerAPIScan\Binary` folder using the Windows Kits

    ```shell
    NanoServerApiScan /BinaryPath:. /WindowsKitsPath:..\WindowsKits
    ```


- Step 7 - Exit from the container after assessment:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
