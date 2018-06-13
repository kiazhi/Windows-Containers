# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is Apache HTTP Server?

The Apache HTTP Server Project is an effort to develop and maintain an open-source HTTP server for modern operating systems including UNIX and Windows. The goal of this project is to provide a secure, efficient and extensible server that provides HTTP services in sync with the current HTTP standards. For more details, follow this [link](https://httpd.apache.org/).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | HTTPD Version | SSL Type/Version | Dockerfile |
| -- | -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.apache/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [2.4.33](https://httpd.apache.org/download.cgi#apache24) | [OpenSSL 1.1.0h](https://www.apachehaus.com/cgi-bin/download.plx) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/apache/sac2016-2.4.33-o110h/Dockerfile) |
| [sac2016-2.4.33-o110h](https://hub.docker.com/r/kiazhi/nanoserver.apache/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [2.4.33](https://httpd.apache.org/download.cgi#apache24) | [OpenSSL 1.1.0h](https://www.apachehaus.com/cgi-bin/download.plx) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/apache/sac2016-2.4.33-o110h/Dockerfile) |
| [sac2016-2.4.33-o102o](https://hub.docker.com/r/kiazhi/nanoserver.apache/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [2.4.33](https://httpd.apache.org/download.cgi#apache24) | [OpenSSL 1.0.2o](https://www.apachehaus.com/cgi-bin/download.plx) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/apache/sac2016-2.4.33-o102o/Dockerfile) |
| [sac2016-2.4.33-lre-2.7.3](https://hub.docker.com/r/kiazhi/nanoserver.apache/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [2.4.33](https://httpd.apache.org/download.cgi#apache24) | [LibreSSL 2.7.3](https://www.apachehaus.com/cgi-bin/download.plx) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/apache/sac2016-2.4.33-lre-2.7.3/Dockerfile) |

# Getting Started with Apache on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.apache
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.apache
    ```


- Step 4 - Verify Apache version within the container interactively:

    ```shell
    httpd -v
    ```


- Step 5 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
