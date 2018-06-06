# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is MySQL?

MySQL, the most popular Open Source SQL database management system, is developed, distributed, and supported by Oracle Corporation. For more details, follow this [link](https://dev.mysql.com/doc/refman/8.0/en/what-is-mysql.html).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | MySQL Version | Dockerfile |
| -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.mysql/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [8.0.11](https://dev.mysql.com/downloads/mysql/8.0.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/mysql/8.0.x/Dockerfile) |
| [sac2016-8.0.11](https://hub.docker.com/r/kiazhi/nanoserver.mysql/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [8.0.11](https://dev.mysql.com/downloads/mysql/8.0.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/mysql/8.0.x/Dockerfile) |
| [sac2016-5.7.22](https://hub.docker.com/r/kiazhi/nanoserver.mysql/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [5.7.22](https://dev.mysql.com/downloads/mysql/5.7.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/mysql/5.7.x/Dockerfile) |
| [sac2016-5.6.40](https://hub.docker.com/r/kiazhi/nanoserver.mysql/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [5.6.40](https://dev.mysql.com/downloads/mysql/5.6.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/mysql/5.6.x/Dockerfile) |
| [sac2016-5.5.60](https://hub.docker.com/r/kiazhi/nanoserver.mysql/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [5.5.60](https://dev.mysql.com/downloads/mysql/5.5.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/mysql/5.5.x/Dockerfile) |

# Getting Started with MySQL on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.mysql
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.mysql
    ```


- Step 4 - Verify MySQL version within the container interactively:

    ```shell
    mysql --version
    ```


- Step 5 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
