<!-- Docker Hub Stars and Pulls Counter -->
![Docker Stars](https://img.shields.io/docker/stars/kiazhi/nanoserver.iis.svg) ![Docker Pulls](https://img.shields.io/docker/pulls/kiazhi/nanoserver.iis.svg)
<!-- Docker Hub Stars and Pulls Counter -->

# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is IIS?

Internet Information Services (IIS) for Windows® Server is a flexible, secure and manageable Web server for hosting anything on the Web. From media streaming to web applications, IIS’s scalable and open architecture is ready to handle the most demanding tasks. For more details, follow this [link](https://www.iis.net/overview).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | IIS Version | Dockerfile |
| -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.iis/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [10.0](https://github.com/OneGet/NanoServerPackage) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/iis/sac2016-10.0/Dockerfile) |
| [sac2016-2.3.6](https://hub.docker.com/r/kiazhi/nanoserver.iis/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [10.0](https://github.com/OneGet/NanoServerPackage) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/iis/sac2016-10.0/Dockerfile) |


# Getting Started with RethinkDB on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.iis
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.iis
    ```


- Step 4 - Verify IIS version within the container interactively:

    ```powershell
    Get-ItemProperty `
        -Path 'HKLM:\SOFTWARE\Microsoft\InetStp' `
        -Name 'ProductString', `
                'InstallPath', `
                'PathWWWRoot', `
                'SetupString', `
                'VersionString' ;
    ```


- Step 5 - To get IIS Sites within the container interactively:

    ```powershell
    Import-Module `
        -Name IISAdministration ;
        
    Get-IISSite ;
    ```


- Step 6 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
