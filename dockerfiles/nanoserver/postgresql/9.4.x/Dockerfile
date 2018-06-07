FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.postgresql" \
    org.label-schema.description="This image is a PostgreSQL on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://www.postgresql.org" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.postgresql:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER node --version" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER node --help" \
    org.label-schema.docker.params="POSTGRESQL_VERSION=version number"

ARG POSTGRESQL_VERSION=9.4.18

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
        -Uri "https://get.enterprisedb.com/postgresql/postgresql-$ENV:POSTGRESQL_VERSION-1-windows-x64-binaries.zip" \
        -OutFile "C:\Temp\postgresql-$ENV:POSTGRESQL_VERSION-1-windows-x64-binaries.zip" \
        -UseBasicParsing \ 
        -Verbose ; \
    \
    Expand-Archive \
        -Path "C:\Temp\postgresql-$ENV:POSTGRESQL_VERSION-1-windows-x64-binaries.zip" \
        -DestinationPath 'C:\\Program Files' \
        -Verbose ; \
    \
    New-Item \
        -Path $('C:\Program Files\pgsql\data') \
        -ItemType Directory \
        -Verbose | Out-Null ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';C:\Program Files\pgsql\bin') \
        -Verbose ;

# Test application
RUN \
    postgres \
        --version

# Set up PostgresSQL as a service
RUN \
    pg_ctl \
        -D 'C:\Program Files\pgsql\data' \
        initdb

RUN \
    regsvr32 \
        'C:\Program Files\pgsql\lib\pgevent.dll'

RUN \
    pg_ctl \
        register \
        -N 'PostgreSQL' \
        -D 'C:\Program Files\pgsql\data' \
        -l logfile

RUN \
    Start-Service \
        -Name PostgreSQL \
        -Verbose ; \
    \
    pg_ctl \
        status \
        -D 'C:\Program Files\pgsql\data'

# Remove temporary items from the build image
RUN \
    Remove-Item \
        -Path 'C:\\Temp' \
        -Recurse \
        -Verbose ;