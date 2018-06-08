FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.MariaDB" \
    org.label-schema.description="This image is a MariaDB on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://mariadb.org" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.mariadb:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER node --version" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER node --help" \
    org.label-schema.docker.params="MARIADB_VERSION=version number"

ARG MARIADB_VERSION=10.3.7

SHELL ["powershell", "-Command"]

RUN \
    if(!(Test-Path -Path 'C:\Temp')) \
    { \
        New-Item \
            -Path 'C:\Temp' \
            -ItemType Directory \
            -Verbose | Out-Null ; \
    } ; \
    \
    Invoke-WebRequest \
        -Uri "http://mariadb.melbourneitmirror.net//mariadb-$ENV:MARIADB_VERSION/winx64-packages/mariadb-$ENV:MARIADB_VERSION-winx64.zip" \
        -OutFile "C:\Temp\mariadb-$ENV:MARIADB_VERSION-winx64.zip" \
        -UseBasicParsing \ 
        -Verbose ; \
    \
    Expand-Archive \
        -Path "C:\Temp\mariadb-$ENV:MARIADB_VERSION-winx64.zip" \
        -DestinationPath 'C:\\Program Files' \
        -Verbose ; \
    \
    Rename-Item \
        -Path "C:\\'Program Files'\\mariadb-$ENV:MARIADB_VERSION-winx64" \
        -NewName $('MariaDB ' + $ENV:MARIADB_VERSION) \
        -Force \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';C:\Program Files\MariaDB ' + $ENV:MARIADB_VERSION + '\bin') \
        -Verbose ;

# Test application
RUN \
    mysql \
        --version

RUN \
    mysqld \
        --install MariaDB

RUN \
    Start-Service \
        -Name MariaDB \
        -Verbose ;

# Remove temporary items from the build image
RUN \
    Remove-Item \
        -Path 'C:\\Temp' \
        -Recurse \
        -Verbose ;