FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.RethinkDB" \
    org.label-schema.description="This image is a RethinkDB on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://rethinkdb.com" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.rethinkdb:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER rethinkdb --version" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER rethinkdb --help" \
    org.label-schema.docker.params="RETHINKDB_VERSION=version number"

ARG RETHINKDB_VERSION=2.3.6

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
        -Uri "https://download.rethinkdb.com/windows/rethinkdb-$ENV:RETHINKDB_VERSION.zip" \
        -OutFile "C:\Temp\rethinkdb-$ENV:RETHINKDB_VERSION.zip" \
        -UseBasicParsing \ 
        -Verbose ; \
    \
    Expand-Archive \
        -Path "C:\Temp\rethinkdb-$ENV:RETHINKDB_VERSION.zip" \
        -DestinationPath 'C:\\Program Files\\RethinkDB\\Server' \
        -Verbose ; \
    \
    Rename-Item \
        -Path "C:\\'Program Files'\RethinkDB\Server\rethinkdb-$ENV:RETHINKDB_VERSION" \
        -NewName $ENV:RETHINKDB_VERSION \
        -Force \
        -Verbose ; \
    \
    New-Item \
        -Path "C:\\'Program Files'\RethinkDB\Server\\$ENV:RETHINKDB_VERSION\\data" \
        -ItemType Directory \
        -Verbose | Out-Null ; \
    \
    New-Item \
        -Path "C:\\'Program Files'\RethinkDB\Server\\$ENV:RETHINKDB_VERSION\\log" \
        -ItemType Directory \
        -Verbose | Out-Null ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';' + $(Join-Path -Path 'C:\Program Files\RethinkDB\Server' -ChildPath "$ENV:RETHINKDB_VERSION")) \
        -Verbose ;

# Test application
RUN \
    rethinkdb \
        --version

# Remove temporary items from the build image
RUN \
    Remove-Item \
        -Path 'C:\\Temp' \
        -Recurse \
        -Verbose ;