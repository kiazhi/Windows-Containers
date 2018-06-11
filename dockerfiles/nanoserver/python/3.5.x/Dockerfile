FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.Python" \
    org.label-schema.description="This image is a Python on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://python.org" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.python:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER python --version" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER python --help" \
    org.label-schema.docker.params="PYTHON_VERSION=version number"

ARG PYTHON_VERSION=3.5.4

SHELL ["powershell", "-Command"]

RUN \
    if(!(Test-Path -Path 'C:\\Temp')) \
    { \
        New-Item \
            -Path 'C:\\Temp' \
            -ItemType Directory \
            -Verbose | Out-Null ; \
    } ; \
    \
    Invoke-WebRequest \
        -Uri "https://www.python.org/ftp/python/$ENV:PYTHON_VERSION/python-$ENV:PYTHON_VERSION-embed-amd64.zip" \ 
        -OutFile "C:\Temp\python-$ENV:PYTHON_VERSION-embed-amd64.zip" \
        -UseBasicParsing \
        -Verbose ; \ 
    \
    Expand-Archive \
        -Path "C:\Temp\python-$ENV:PYTHON_VERSION-embed-amd64.zip" \
        -DestinationPath 'C:\Program Files\Python' \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';C:\Program Files\Python') \
        -Verbose ;

# Test application
RUN python \
        --version

# Remove environment variables from the build image
RUN \
    Remove-Item \
        -Path 'C:\\Temp' \
        -Recurse \
        -Verbose ;