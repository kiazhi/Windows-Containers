FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.MySQL" \
    org.label-schema.description="This image is a MySQL on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://mysql.com" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.mysql:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER mysql --version" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER mysql --help" \
    org.label-schema.docker.params="MYSQL_VERSION=version number"

ARG MYSQL_VERSION=8.0.11

SHELL ["powershell", "-Command"]

COPY msvcp140.dll /Windows/System32/

COPY vcruntime140.dll /Windows/System32/

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
        -Uri "https://dev.mysql.com/get/Downloads/MySQL-$($ENV:MYSQL_VERSION.Substring(0,3))/mysql-$ENV:MYSQL_VERSION-winx64.zip" \
        -OutFile "C:\Temp\mysql-$ENV:MYSQL_VERSION-winx64.zip" \
        -UseBasicParsing \ 
        -Verbose ; \
    \
    Expand-Archive \
        -Path "C:\Temp\mysql-$ENV:MYSQL_VERSION-winx64.zip" \
        -DestinationPath 'C:\\Program Files\\MySQL' \
        -Verbose ; \
    \
    Rename-Item \
        -Path "C:\\'Program Files'\\MySQL\\mysql-$ENV:MYSQL_VERSION-winx64" \
        -NewName $('MySQL Server ' + $ENV:MYSQL_VERSION.Substring(0,3)) \
        -Force \
        -Verbose ; \
    \
    New-Item \
        -Path $('C:\Program Files\MySQL\MySQL Server ' + $($ENV:MYSQL_VERSION.Substring(0,3)) + '\data') \
        -ItemType Directory \
        -Verbose | Out-Null ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';C:\Program Files\MySQL\MySQL Server ' + $($ENV:MYSQL_VERSION.Substring(0,3)) + '\bin') \
        -Verbose ;

# Test application
RUN \
    mysql \
        --version

# Set up MySQL as a service
RUN \
    mysqld \
        --initialize-insecure

RUN \
    mysqld \
        --install

RUN \
    Start-Service \
        -Name MySQL \
        -Verbose ;

# Remove temporary items from the build image
RUN \
    Remove-Item \
        -Path 'C:\\Temp' \
        -Recurse \
        -Verbose ;