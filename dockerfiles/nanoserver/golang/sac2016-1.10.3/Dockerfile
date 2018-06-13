FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.Golang" \
    org.label-schema.description="This image is a Golang on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://golang.org" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.golang:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER go version" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER go help" \
    org.label-schema.docker.params="GOLANG_VERSION=version number"

SHELL ["powershell", "-Command"]

ARG GOLANG_VERSION=1.10.3

# Download, extract and configure application binary
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
        -Uri "https://dl.google.com/go/go$ENV:GOLANG_VERSION.windows-amd64.zip" \
        -OutFile "C:\\Temp\\go$ENV:GOLANG_VERSION.windows-amd64.zip" \
        -UseBasicParsing \
        -Verbose ; \
    \
    Expand-Archive \
        -Path "C:\\Temp\\go$ENV:GOLANG_VERSION.windows-amd64.zip" \
        -DestinationPath 'C:\Program Files' \
        -Verbose ; \
    \
    New-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'GOROOT' \
        -Value 'C:\Program Files\go' \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';C:\Program Files\go\bin') \
        -Verbose ;

# Test application
RUN go \
       version

# Remove temporary items from the build image
RUN \
    Remove-Item \
        -Path 'C:\Temp' \
        -Recurse \
        -Verbose ;