<!-- Docker Hub Stars and Pulls Counter -->
![Docker Stars](https://img.shields.io/docker/stars/kiazhi/nanoserver.postgresql.svg) ![Docker Pulls](https://img.shields.io/docker/pulls/kiazhi/nanoserver.postgresql.svg)
<!-- Docker Hub Stars and Pulls Counter -->

# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is PostgreSQL?

PostgreSQL is a powerful, open source object-relational database system that uses and extends the SQL language combined with many features that safely store and scale the most complicated data workloads. The origins of PostgreSQL date back to 1986 as part of the POSTGRES project at the University of California at Berkeley and has more than 30 years of active development on the core platform. For more details, follow this [link](https://www.postgresql.org/about/).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | PostgreSQL Version | Dockerfile |
| -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.postgresql/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [10.4](https://www.enterprisedb.com/download-postgresql-binaries) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/postgresql/sac2016-10.4/Dockerfile) |
| [sac2016-10.4](https://hub.docker.com/r/kiazhi/nanoserver.postgresql/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [10.4](https://www.enterprisedb.com/download-postgresql-binaries) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/postgresql/sac2016-10.4/Dockerfile) |
| [sac2016-9.6.9](https://hub.docker.com/r/kiazhi/nanoserver.postgresql/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [9.6.9](https://www.enterprisedb.com/download-postgresql-binaries) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/postgresql/sac2016-9.6.9/Dockerfile) |
| [sac2016-9.5.13](https://hub.docker.com/r/kiazhi/nanoserver.postgresql/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [9.5.13](https://www.enterprisedb.com/download-postgresql-binaries) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/postgresql/sac2016-9.5.13/Dockerfile) |
| [sac2016-9.4.18](https://hub.docker.com/r/kiazhi/nanoserver.postgresql/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [9.4.18](https://www.enterprisedb.com/download-postgresql-binaries) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/postgresql/sac2016-9.4.18/Dockerfile) |

# Getting Started with PostgreSQL on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.postgresql
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.postgresql
    ```


- Step 4 - Verify PostgreSQL version within the container interactively:

    ```shell
    postgres --version
    ```


- Step 5 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
