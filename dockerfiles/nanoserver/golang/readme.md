<!-- Docker Hub Stars and Pulls Counter -->
![Docker Stars](https://img.shields.io/docker/stars/kiazhi/nanoserver.golang.svg) ![Docker Pulls](https://img.shields.io/docker/pulls/kiazhi/nanoserver.golang.svg)
<!-- Docker Hub Stars and Pulls Counter -->

# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is Golang?

Go is an open source programming language developed by a team at Google and many contributors from the open source community that makes it easy to build simple, reliable, and efficient software. For more details, follow this [link](https://golang.org/).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | Golang Version | Dockerfile |
| -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.golang/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [1.10.3](https://golang.org/dl/#go1.10.3) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/golang/sac2016-1.10.3/Dockerfile) |
| [sac2016-1.10.3](https://hub.docker.com/r/kiazhi/nanoserver.golang/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [1.10.3](https://golang.org/dl/#go1.10.3) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/golang/sac2016-1.10.3/Dockerfile) |
| [sac2016-1.9.7](https://hub.docker.com/r/kiazhi/nanoserver.golang/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [1.9.7](https://golang.org/dl/#go1.9.7) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/golang/sac2016-1.9.7/Dockerfile) |

# Getting Started with Golang on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.golang
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.golang
    ```


- Step 4 - Verify Go version within the container interactively:

    ```shell
    go version
    ```


- Step 5 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
