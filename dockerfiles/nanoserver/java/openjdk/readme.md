# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is (Java) OpenJDK?

OpenJDK (Open Java Development Kit) is a free and open source implementation of the Java Platform, Standard Edition (Java SE). For more details, follow this [link](http://openjdk.java.net/).

# List of available OpenJDK distro

- Oracle's Java OpenJDK is a free and open source implementation of the Java Platform, Standard Edition. It is the result of an effort Sun Microsystems began in 2006. For more details, follow this [link](http://openjdk.java.net/faq/).

- Zulu is an enterprise quality, certified build of OpenJDK that can be deployed on multiple platforms. It is a Java platform that makes sense. For more details, follow this [link](https://www.azul.com/products/zulu-and-zulu-enterprise/).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | Distro | Java Version | Dockerfile |
| -- | -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.java.openjdk/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [Java](http://jdk.java.net/10/) | [10.0.1](http://jdk.java.net/10/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/java/openjdk/sac2016-java-10.0.1/Dockerfile) |
| [sac2016-java-10.0.1](https://hub.docker.com/r/kiazhi/nanoserver.java.openjdk/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [Java](http://jdk.java.net/10/) | [10.0.1](http://jdk.java.net/10/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/java/openjdk/sac2016-java-10.0.1/Dockerfile) |
| [sac2016-zulu-10.0.1](https://hub.docker.com/r/kiazhi/nanoserver.java.openjdk/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [Zulu](https://www.azul.com/products/zulu-and-zulu-enterprise/) | [10.0.1](https://www.azul.com/downloads/zulu/zulu-windows/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/java/openjdk/sac2016-zulu-10.0.1/Dockerfile) |
| [sac2016-java-10](https://hub.docker.com/r/kiazhi/nanoserver.java.openjdk/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [Zulu](https://www.azul.com/products/zulu-and-zulu-enterprise/) | [10.0](http://jdk.java.net/archive/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/java/openjdk/sac2016-java-10/Dockerfile) |
| [sac2016-zulu-10](https://hub.docker.com/r/kiazhi/nanoserver.java.openjdk/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [Java](http://jdk.java.net/10/) | [10.0](https://www.azul.com/downloads/zulu/zulu-windows/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/java/openjdk/sac2016-zulu-10/Dockerfile) |
| [sac2016-zulu-9.0.7](https://hub.docker.com/r/kiazhi/nanoserver.java.openjdk/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [Zulu](https://www.azul.com/products/zulu-and-zulu-enterprise/) | [9.0.7](https://www.azul.com/downloads/zulu/zulu-windows/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/java/openjdk/sac2016-zulu-9.0.7/Dockerfile) |
| [sac2016-java-9.0.4](https://hub.docker.com/r/kiazhi/nanoserver.java.openjdk/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [Java](http://jdk.java.net/9/) | [9.0.4](http://jdk.java.net/archive/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/java/openjdk/sac2016-java-9.0.4/Dockerfile) |
| [sac2016-zulu-8.0.172](https://hub.docker.com/r/kiazhi/nanoserver.java.openjdk/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [Zulu](https://www.azul.com/products/zulu-and-zulu-enterprise/) | [8.0.172](https://www.azul.com/downloads/zulu/zulu-windows/) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/java/openjdk/sac2016-zulu-8.0.172/Dockerfile) |

# Getting Started with (Java) OpenJDK on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.java.openjdk
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.java.openjdk
    ```


- Step 4 - Verify Java version within the container interactively:

    ```shell
    java -version
    ```


- Step 4 - Verify Java Complier version within the container interactively:

    ```shell
    javac -version
    ```


- Step 6 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
