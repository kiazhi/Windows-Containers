ARG 7ZIP_VERSION=1805

FROM microsoft/windowsservercore:latest AS download

ARG 7ZIP_VERSION

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
        -Uri $('https://www.7-zip.org/a/7z' + $ENV:7ZIP_VERSION + '-x64.exe') \
        -OutFile $('C:\Temp\7z' + $ENV:7ZIP_VERSION + '-x64.exe') \
        -UseBasicParsing \ 
        -Verbose ; \
    \
    Start-Process \
        -FilePath $('C:\Temp\7z' + $ENV:7ZIP_VERSION + '-x64.exe') \
        -ArgumentList '/S' \
        -NoNewWindow \
        -Wait \
        -Verbose ; 

FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.7-Zip" \
    org.label-schema.description="This image is a 7-Zip on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://www.7-zip.org/" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.7-zip:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER 7z b" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER 7z" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER 7z -h" \
    org.label-schema.docker.params="7ZIP_VERSION=version number"

ARG 7ZIP_VERSION

COPY --from=download ["/Program Files/7-Zip", "/Program Files/7-Zip"]

RUN SETX PATH "%ProgramFiles%\7-Zip;%PATH%"

# Test application
RUN \
    7z \
        b