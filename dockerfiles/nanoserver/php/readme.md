<!-- Docker Hub Stars and Pulls Counter -->
![Docker Stars](https://img.shields.io/docker/stars/kiazhi/nanoserver.php.svg) ![Docker Pulls](https://img.shields.io/docker/pulls/kiazhi/nanoserver.php.svg)
<!-- Docker Hub Stars and Pulls Counter -->

# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is PHP?

PHP (recursive acronym for PHP: Hypertext Preprocessor) is a widely-used open source general-purpose scripting language that is especially suited for web development and can be embedded into HTML. For more details, follow this [link](http://php.net/manual/en/intro-whatis.php).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | PHP Version | Dockerfile |
| -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.php/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [7.2.6](https://windows.php.net/downloads/releases/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/php/sac2016-7.2.6/Dockerfile) |
| [sac2016-7.2.6](https://hub.docker.com/r/kiazhi/nanoserver.php/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [7.2.6](https://windows.php.net/downloads/releases/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/php/sac2016-7.2.6/Dockerfile) |
| [sac2016-7.1.18](https://hub.docker.com/r/kiazhi/nanoserver.php/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [7.1.18](https://windows.php.net/downloads/releases/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/php/sac2016-7.1.18/Dockerfile) |
| [sac2016-7.0.30](https://hub.docker.com/r/kiazhi/nanoserver.php/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [7.0.30](https://windows.php.net/downloads/releases/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/php/sac2016-7.0.30/Dockerfile) |

# Getting Started with PHP on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.php
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.php
    ```


- Step 4 - Verify PHP version within the container interactively:

    ```shell
    php --version
    ```


- Step 5 - Verify PHP configuration within the container interactively:

    ```shell
    php --info
    ```


- Step 6 - Verify PHP is serve by IIS using PowerShell within the container interactively:

    ```powershell
    Invoke-WebRequest `
        -Uri localhost | `
            Select-Object `
                -Expand RawContent ;
    ```


- Step 6 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
