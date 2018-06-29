<!-- Docker Hub Stars and Pulls Counter -->
![Docker Stars](https://img.shields.io/docker/stars/kiazhi/nanoserver.powershell.svg) ![Docker Pulls](https://img.shields.io/docker/pulls/kiazhi/nanoserver.powershell.svg)
<!-- Docker Hub Stars and Pulls Counter -->

# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is PowerShell?

PowerShell is a task automation and configuration management framework that comes in a form of a command line that is cross-platform (Windows, macOS, and Linux), open-source, and built for heterogeneous environments and the hybrid cloud. For more details, follow this [link](https://github.com/PowerShell/Powershell).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | PowerShell Version | Dockerfile |
| -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.powershell/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [6.0.2](https://download.rethinkdb.com/windows/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/powershell/sac2016-6.0.2/Dockerfile) |
| [latest-preview](https://hub.docker.com/r/kiazhi/nanoserver.powershell/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [6.1.0-preview.1](https://github.com/PowerShell/PowerShell/releases/tag/v6.1.0-preview.1) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/powershell/sac2016-6.1.0-preview.1/Dockerfile) |
| [1803-6.1.0-preview.1](https://hub.docker.com/r/kiazhi/nanoserver.powershell/tags/) | [1803](https://hub.docker.com/r/microsoft/nanoserver/) | [6.1.0-preview.1](https://github.com/PowerShell/PowerShell/releases/tag/v6.1.0-preview.1) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/powershell/1803-6.1.0-preview.1/Dockerfile) |
| [1709-6.1.0-preview.1](https://hub.docker.com/r/kiazhi/nanoserver.powershell/tags/) | [1709](https://hub.docker.com/r/microsoft/nanoserver/) | [6.1.0-preview.1](https://github.com/PowerShell/PowerShell/releases/tag/v6.1.0-preview.1) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/powershell/1709-6.1.0-preview.1/Dockerfile) |
| [sac2016-6.1.0-preview.1](https://hub.docker.com/r/kiazhi/nanoserver.powershell/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [6.1.0-preview.1](https://github.com/PowerShell/PowerShell/releases/tag/v6.1.0-preview.1) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/powershell/sac2016-6.1.0-preview.1/Dockerfile) |
| [1803-6.0.2](https://hub.docker.com/r/kiazhi/nanoserver.powershell/tags/) | [1803](https://hub.docker.com/r/microsoft/nanoserver/) | [6.0.2](https://github.com/PowerShell/PowerShell/releases/tag/v6.0.2) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/powershell/1803-6.0.2/Dockerfile) |
| [1709-6.0.2](https://hub.docker.com/r/kiazhi/nanoserver.powershell/tags/) | [1709](https://hub.docker.com/r/microsoft/nanoserver/) | [6.0.2](https://github.com/PowerShell/PowerShell/releases/tag/v6.0.2) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/powershell/1709-6.0.2/Dockerfile) |
| [sac2016-6.0.2](https://hub.docker.com/r/kiazhi/nanoserver.powershell/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [6.0.2](https://github.com/PowerShell/PowerShell/releases/tag/v6.0.2) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/powershell/sac2016-6.0.2/Dockerfile) |
| [1803-6.0.1](https://hub.docker.com/r/kiazhi/nanoserver.powershell/tags/) | [1803](https://hub.docker.com/r/microsoft/nanoserver/) | [6.0.1](https://github.com/PowerShell/PowerShell/releases/tag/v6.0.1) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/powershell/1803-6.0.1/Dockerfile) |
| [1709-6.0.1](https://hub.docker.com/r/kiazhi/nanoserver.powershell/tags/) | [1709](https://hub.docker.com/r/microsoft/nanoserver/) | [6.0.1](https://github.com/PowerShell/PowerShell/releases/tag/v6.0.1) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/powershell/1709-6.0.1/Dockerfile) |
| [sac2016-6.0.1](https://hub.docker.com/r/kiazhi/nanoserver.powershell/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [6.0.1](https://github.com/PowerShell/PowerShell/releases/tag/v6.0.1) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/powershell/sac2016-6.0.1/Dockerfile) |
| [1803-6.0.0](https://hub.docker.com/r/kiazhi/nanoserver.powershell/tags/) | [1803](https://hub.docker.com/r/microsoft/nanoserver/) | [6.0.0](https://github.com/PowerShell/PowerShell/releases/tag/v6.0.0) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/powershell/1803-6.0.0/Dockerfile) |
| [1709-6.0.0](https://hub.docker.com/r/kiazhi/nanoserver.powershell/tags/) | [1709](https://hub.docker.com/r/microsoft/nanoserver/) | [6.0.0](https://github.com/PowerShell/PowerShell/releases/tag/v6.0.0) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/powershell/1709-6.0.0/Dockerfile) |
| [sac2016-6.0.0](https://hub.docker.com/r/kiazhi/nanoserver.powershell/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [6.0.0](https://github.com/PowerShell/PowerShell/releases/tag/v6.0.0) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/powershell/sac2016-6.0.0/Dockerfile) |


# Getting Started with PowerShell on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.powershell
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.powershell
    ```


- Step 4 - Verify PowerShell version within the container interactively:

    ```powershell
    $PSVersionTable
    ```


- Step 6 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
