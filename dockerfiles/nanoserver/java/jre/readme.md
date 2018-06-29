<!-- Docker Hub Stars and Pulls Counter -->
![Docker Stars](https://img.shields.io/docker/stars/kiazhi/nanoserver.java.jre.svg) ![Docker Pulls](https://img.shields.io/docker/pulls/kiazhi/nanoserver.java.jre.svg)
<!-- Docker Hub Stars and Pulls Counter -->

# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is (Java) JRE?

The Java Runtime Environment (JRE) is a set of software tools for development of Java applications. It combines the Java Virtual Machine (JVM), platform core classes and supporting libraries. For more details, follow this [link](https://blogs.oracle.com/java-platform-group/understanding-the-server-jre).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | Distro | Java Version | Dockerfile |
| -- | -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.java.jre/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [Oracle](http://www.oracle.com/technetwork/java/javase/overview/index.html) | [10.0.1](http://www.oracle.com/technetwork/java/javase/downloads/sjre10-downloads-4417025.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/java/jre/sac2016-oracle-10.0.1/Dockerfile) |
| [sac2016-oracle-10.0.1](https://hub.docker.com/r/kiazhi/nanoserver.java.jre/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [Oracle](http://www.oracle.com/technetwork/java/javase/overview/index.html) | [10.0.1](http://www.oracle.com/technetwork/java/javase/downloads/sjre10-downloads-4417025.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/java/jre/sac2016-oracle-10.0.1/Dockerfile) |
| [sac2016-oracle-8u172](https://hub.docker.com/r/kiazhi/nanoserver.java.jre/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [Oracle](http://www.oracle.com/technetwork/java/javase/overview/index.html) | [8u172](http://www.oracle.com/technetwork/java/javase/downloads/server-jre8-downloads-2133154.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/java/jre/sac2016-oracle-8u172/Dockerfile) |
| [sac2016-oracle-8u171](https://hub.docker.com/r/kiazhi/nanoserver.java.jre/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [Oracle](http://www.oracle.com/technetwork/java/javase/overview/index.html) | [8u171](http://www.oracle.com/technetwork/java/javase/downloads/server-jre8-downloads-2133154.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/java/jre/sac2016-oracle-8u171/Dockerfile) |

# Getting Started with (Java) JRE on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.java.jre
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.java.jre
    ```


- Step 4 - Verify Java version within the container interactively:

    ```shell
    java -version
    ```


- Step 5 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
