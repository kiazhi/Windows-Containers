# What is Nano Server?

Windows Server 2016 offers a new installation option: Nano Server. Nano Server is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. For more details, follow this [link](https://docs.microsoft.com/en-us/windows-server/get-started/getting-started-with-nano-server).

# What is ElasticSearch?

Elasticsearch is a distributed, RESTful search and analytics engine capable of solving a growing number of use cases. As the heart of the Elastic Stack, it centrally stores your data so you can discover the expected and uncover the unexpected.. For more details, follow this [link](https://www.elastic.co/products/elasticsearch).

# Releases Tag

This is a brief example on how the image is tagged and does not represent every currently available tags.

| Tag | OS Version | ElasticSearch Version | Dockerfile |
| -- | -- | -- | -- |
| [latest](https://hub.docker.com/r/kiazhi/nanoserver.elastic.elasticsearch/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [6.3.0](https://www.elastic.co/downloads/elasticsearch) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/elasticsearch/sac2016-6.3.0/Dockerfile) |
| [sac2016-6.3.0](https://hub.docker.com/r/kiazhi/nanoserver.elastic.elasticsearch/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [6.3.0](https://www.elastic.co/downloads/past-releases/elasticsearch-6-3-0) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/elasticsearch/sac2016-6.3.0/Dockerfile) |
| [sac2016-6.2.4](https://hub.docker.com/r/kiazhi/nanoserver.elastic.elasticsearch/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [6.2.4](https://www.elastic.co/downloads/past-releases/elasticsearch-6-2-4) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/elasticsearch/sac2016-6.2.4/Dockerfile) |
| [sac2016-5.6.9](https://hub.docker.com/r/kiazhi/nanoserver.elastic.elasticsearch/tags/) | [sac2016](https://hub.docker.com/r/microsoft/nanoserver/) | [5.6.9](https://www.elastic.co/downloads/past-releases/elasticsearch-5-6-10) | [Dockerfile](https://github.com/kiazhi/Windows-Containers/tree/master/dockerfiles/nanoserver/elasticsearch/sac2016-5.6.9/Dockerfile) |


# Getting Started with RethinkDB on Nano Server

- Step 1 - Switch to Windows container:
    - [Docker Docs - Switch between Windows and Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)


- Step 2 - Pull the docker image using Docker CLI:

    ```shell
    docker pull kiazhi/nanoserver.elastic.elasticsearch
    ```


- Step 3 - Inspect the container interactively using Docker CLI:

    ```shell
    docker run --rm -it kiazhi/nanoserver.elastic.elasticsearch
    ```


- Step 4 - Verify ElasticSearch version within the container interactively:

    ```shell
    elasticsearch --version
    ```


- Step 5 - To start ElasticSearch Server within the container interactively:

    ```shell
    elasticsearch
    ```


- Step 6 - To exit from the container:

    ```shell
    exit
    ```


# DISCLAIMER

EXCEPT AS REPRESENTED IN THIS AGREEMENT, ALL WORK PRODUCT BY DEVELOPER IS PROVIDED "AS-IS". OTHER THAN AS PROVIDED IN THIS AGREEMENT, DEVELOPER MAKES NO OTHER WARRANTIES, EXPRESS OR IMPLIED, AND HEREBY DISCLAIMS ALL IMPLIED WARRANTIES, INCLUDING ANY WARRANTY OF MERCHANTABILITY AND WARRANTY OF FITNESS FOR A PARTICULAR PURPOSE.
