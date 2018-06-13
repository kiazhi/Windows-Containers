FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.Nodejs" \
    org.label-schema.description="This image is a Nodejs on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://nodejs.org" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.nodejs:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER node --version" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER node --help" \
    org.label-schema.docker.params="NODEJS_VERSION=version number"

ARG NODEJS_VERSION=v8.11.2

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
        -Uri "https://nodejs.org/dist/$ENV:NODEJS_VERSION/node-$ENV:NODEJS_VERSION-win-x64.zip" \
        -OutFile "C:\\Temp\\node-$ENV:NODEJS_VERSION-win-x64.zip" \
        -UseBasicParsing \
        -Verbose ; \
    \
    Invoke-WebRequest \
        -Uri "https://nodejs.org/dist/$ENV:NODEJS_VERSION/SHASUMS256.txt" \
        -OutFile "C:\\Temp\\node-$ENV:NODEJS_VERSION-SHASUMS256.txt" \
        -UseBasicParsing \
        -Verbose ; \
    \
    if((Get-FileHash \
            -Path "C:\\Temp\\node-$ENV:NODEJS_VERSION-win-x64.zip").Hash \
        -match \
        ((Select-String \
            -Path "C:\\Temp\\node-$ENV:NODEJS_VERSION-SHASUMS256.txt" \
            -Pattern "node-$ENV:NODEJS_VERSION-win-x64.zip").Line).SubString(0,64)) \
        { \
            Expand-Archive \
                -Path "C:\\Temp\\node-$ENV:NODEJS_VERSION-win-x64.zip" \
                -DestinationPath 'C:\\Program Files' \
                -Verbose ; \
            \
            Rename-Item \
                -Path "C:\\'Program Files'\\node-$ENV:NODEJS_VERSION-win-x64" \
                -NewName 'nodejs' \
                -Force \
                -Verbose ; \
    } ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';C:\Program Files\nodejs') \
        -Verbose ;

# Test application
RUN node \
        --version

RUN npm \
        --version

# Remove temporary items from the build image
RUN \
    Remove-Item \
        -Path 'C:\\Temp' \
        -Recurse \
        -Verbose ;