# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is 7-Zip?

7-Zip is a free and open-source file archiver, a utility used to place groups of files within compressed containers known as "archives". For more details, follow this [link](https://www.7-zip.org/).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | 7-Zip Version | Dockerfile |
| -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.rethinkdb/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [18.05](https://www.7-zip.org/download.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/rethinkdb/sac2016-18.05/Dockerfile) |
| [1709-18.05](https://hub.docker.com/r/kiazhi/nanoserver.rethinkdb/tags/) | [1709](https://hub.docker.com/r/microsoft/nanoserver/) | [18.05](https://www.7-zip.org/download.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/7-zip/1709-18.05/Dockerfile) |
| [sac2016-18.05](https://hub.docker.com/r/kiazhi/nanoserver.rethinkdb/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [18.05](https://www.7-zip.org/download.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/7-zip/sac2016-18.05/Dockerfile) |
| [1709-16.04](https://hub.docker.com/r/kiazhi/nanoserver.rethinkdb/tags/) | [1709](https://hub.docker.com/r/microsoft/nanoserver/) | [16.04](https://www.7-zip.org/download.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/7-zip/1709-16.04/Dockerfile) |
| [sac2016-16.04](https://hub.docker.com/r/kiazhi/nanoserver.rethinkdb/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [16.04](https://www.7-zip.org/download.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/7-zip/sac2016-16.04/Dockerfile) |


# Getting Started with 7-Zip on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.7-zip
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.7-zip
    ```


- Step 4 - Verify 7-Zip benchmark within the container interactively:

    ```shell
    7z b
    ```


- Step 5 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
