# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is MariaDB?

MariaDB Server is one of the most popular database servers in the world. It’s made by the original developers of MariaDB and guaranteed to stay open source. For more details, follow this [link](http://mariadb.org/about/).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | MariaDB Version | Dockerfile |
| -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.mariadb/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [10.3.7](https://downloads.mariadb.org/mariadb/10.3.7/#os_group=windows&file_type=zip) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/sac2016/mariadb/10.3.x/Dockerfile) |
| [sac2016-10.3.7](https://hub.docker.com/r/kiazhi/nanoserver.mariadb/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [10.3.7](https://downloads.mariadb.org/mariadb/10.3.7/#os_group=windows&file_type=zip) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/sac2016/mariadb/10.3.x/Dockerfile) |
| [sac2016-10.2.15](https://hub.docker.com/r/kiazhi/nanoserver.mariadb/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [10.2.15](https://downloads.mariadb.org/mariadb/10.2.15/#os_group=windows&file_type=zip) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/sac2016/mariadb/10.2.x/Dockerfile) |
| [sac2016-10.1.33](https://hub.docker.com/r/kiazhi/nanoserver.mariadb/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [10.1.33](https://downloads.mariadb.org/mariadb/10.1.33/#os_group=windows&file_type=zip) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/sac2016/mariadb/10.1.x/Dockerfile) |
| [sac2016-10.0.35](https://hub.docker.com/r/kiazhi/nanoserver.mariadb/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [10.0.35](https://downloads.mariadb.org/mariadb/10.0.35/#os_group=windows&file_type=zip) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/sac2016/mariadb/10.0.x/Dockerfile) |
| [sac2016-5.5.60](https://hub.docker.com/r/kiazhi/nanoserver.mariadb/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [5.5.60](https://downloads.mariadb.org/mariadb/5.5.60/#os_group=windows&file_type=zip) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/sac2016/mariadb/5.5.x/Dockerfile) |

# Getting Started with MariaDB on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.mariadb
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.mariadb
    ```


- Step 4 - Verify MariaDB version within the container interactively:

    ```shell
    mysql --version
    ```


- Step 5 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
