# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is RethinkDB?

RethinkDB is the first open-source, scalable JSON database built from the ground up for the realtime web. It inverts the traditional database architecture by exposing an exciting new access model – instead of polling for changes, the developer can tell RethinkDB to continuously push updated query results to applications in realtime. RethinkDB’s realtime push architecture dramatically reduces the time and effort necessary to build scalable realtime apps. For more details, follow this [link](https://www.rethinkdb.com/faq/).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | RethinkDB Version | Dockerfile |
| -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.rethinkdb/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [2.3.6](https://download.rethinkdb.com/windows/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/rethinkdb/sac2016-2.3.6/Dockerfile) |
| [sac2016-2.3.6](https://hub.docker.com/r/kiazhi/nanoserver.rethinkdb/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [2.3.6](https://download.rethinkdb.com/windows/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/rethinkdb/sac2016-2.3.6/Dockerfile) |


# Getting Started with RethinkDB on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.rethinkdb
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.rethinkdb
    ```


- Step 4 - Verify RethinkDB version within the container interactively:

    ```shell
    rethinkdb --version
    ```


- Step 5 - To start RethinkDB Server within the container interactively:

    ```shell
    rethinkdb --directory "C:\Program Files\RethinkDB\Server\2.3.6\data" --log-file "C:\Program Files\RethinkDB\Server\2.3.6\log\log_file"
    ```


- Step 6 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
