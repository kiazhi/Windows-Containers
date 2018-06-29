<!-- Docker Hub Stars and Pulls Counter -->
![Docker Stars](https://img.shields.io/docker/stars/kiazhi/nanoserver.perl.svg) ![Docker Pulls](https://img.shields.io/docker/pulls/kiazhi/nanoserver.perl.svg)
<!-- Docker Hub Stars and Pulls Counter -->

# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is Perl?

Perl 5 is a highly capable, feature-rich programming language with over 30 years of development. Perl 5 runs on over 100 platforms from portables to mainframes and is suitable for both rapid prototyping and large scale development projects.

"Perl" is a family of languages, "Perl 6" is part of the family, but it is a separate language which has its own development team. Its existence has no significant impact on the continuing development of "Perl 5". For more details, follow this [link](https://www.perl.org/about.html).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | Perl Version | Dockerfile |
| -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.perl/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [5.26.2.1](http://strawberryperl.com/releases.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/perl/sac2016-5.26.2.1/Dockerfile) |
| [sac2016-5.26.2.1](https://hub.docker.com/r/kiazhi/nanoserver.perl/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [5.26.2.1](http://strawberryperl.com/releases.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/perl/sac2016-5.26.2.1/Dockerfile) |
| [sac2016-5.24.4.1](https://hub.docker.com/r/kiazhi/nanoserver.perl/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [5.24.4.1](http://strawberryperl.com/releases.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/perl/sac2016-5.24.4.1/Dockerfile) |
| [sac2016-5.22.3.1](https://hub.docker.com/r/kiazhi/nanoserver.perl/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [5.22.3.1](http://strawberryperl.com/releases.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/perl/sac2016-5.22.3.1/Dockerfile) |
| [sac2016-5.20.3.3](https://hub.docker.com/r/kiazhi/nanoserver.perl/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [5.20.3.3](http://strawberryperl.com/releases.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/perl/sac2016-5.20.3.3/Dockerfile) |
| [sac2016-5.18.4.1](https://hub.docker.com/r/kiazhi/nanoserver.perl/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [5.18.4.1](http://strawberryperl.com/releases.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/perl/sac2016-5.18.4.1/Dockerfile) |
| [sac2016-5.16.3.1](https://hub.docker.com/r/kiazhi/nanoserver.perl/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [5.16.3.1](http://strawberryperl.com/releases.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/perl/sac2016-5.16.3.1/Dockerfile) |
| [sac2016-5.14.4.1](https://hub.docker.com/r/kiazhi/nanoserver.perl/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [5.14.4.1](http://strawberryperl.com/releases.html) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/perl/sac2016-5.14.4.1/Dockerfile) |

# Getting Started with Perl on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.perl
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.perl
    ```


- Step 4 - Verify Perl version within the container interactively:

    ```shell
    perl -v
    ```


- Step 5 - Exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
