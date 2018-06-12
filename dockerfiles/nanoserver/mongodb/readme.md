# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is MongoDB?

MongoDB is a document database with the scalability and flexibility that you want with the querying and indexing that you need. For more details, follow this [link](https://www.mongodb.com/what-is-mongodb).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | MongoDB Version | Dockerfile |
| -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.mongodb/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [3.6.5](https://www.mongodb.org/dl/win32/x86_64-2008plus-ssl-3.6.5) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/mongodb/sac2016-3.6.5/Dockerfile) |
| [sac2016-3.6.5](https://hub.docker.com/r/kiazhi/nanoserver.mongodb/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [3.6.5](https://www.mongodb.org/dl/win32/x86_64-2008plus-ssl-3.6.5) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/mongodb/sac2016-3.6.5/Dockerfile) |
| [sac2016-3.4.15](https://hub.docker.com/r/kiazhi/nanoserver.mongodb/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [3.4.15](https://www.mongodb.org/dl/win32/x86_64-2008plus-ssl-3.4.15) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/mongodb/sac2016-3.4.15/Dockerfile) |

# Getting Started with MongoDB on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.mongodb
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.mongodb
    ```


- Step 4 - Verify MongoDB version within the container interactively:

    ```shell
    mongo --version
    ```


- Step 5 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
