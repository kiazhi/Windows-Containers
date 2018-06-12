# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is Nodejs?

Node.js® is a JavaScript runtime built on [Chrome's V8 JavaScript engine](https://developers.google.com/v8/) that uses an event-driven, non-blocking I/O model that makes it lightweight and efficient. With Node.js' package ecosystem, [npm](https://www.npmjs.com/), is the largest ecosystem of open source libraries in the world. For more details, follow this [link](https://nodejs.org/en/about/).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | Nodejs Version | Dockerfile |
| -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.nodejs/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [10.3.0](https://nodejs.org/dist/v10.3.0/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/nodejs/sac2016-10.3.0/Dockerfile) |
| [sac2016-10.3.0](https://hub.docker.com/r/kiazhi/nanoserver.nodejs/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [10.3.0](https://nodejs.org/dist/v10.3.0/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/nodejs/sac2016-10.3.0/Dockerfile) |
| [sac2016-8.11.2](https://hub.docker.com/r/kiazhi/nanoserver.nodejs/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [8.11.2](https://nodejs.org/dist/v8.11.2/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/nodejs/sac2016-8.11.2/Dockerfile) |

# Getting Started with Nodejs on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.nodejs
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.nodejs
    ```


- Step 4 - Verify Nodejs version within the container interactively:

    ```shell
    node --version
    ```


- Step 5 - Verify Nodejs Package Manager (NPM) version within the container interactively:

    ```shell
    npm --version
    ```


- Step 6 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
