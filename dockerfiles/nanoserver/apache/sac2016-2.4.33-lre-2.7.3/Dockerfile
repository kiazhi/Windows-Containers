FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.Apache" \
    org.label-schema.description="This image is a Apache on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="http://httpd.apache.org" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.apache:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER httpd -v" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER httpd -h" \
    org.label-schema.docker.params="APACHE_VERSION=version number,SSL_VERSION=openssl/libressl version number"

ARG APACHE_VERSION=2.4.33

ARG SSL_VERSION=lre-2.7.3

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
        -Uri "http://www.apachehaus.com/downloads/httpd-$ENV:APACHE_VERSION-$ENV:SSL_VERSION-x64-vc14-r3.zip" \
        -OutFile "C:\\Temp\\httpd-$ENV:APACHE_VERSION-$ENV:SSL_VERSION-x64-vc14-r3.zip" \
        -UseBasicParsing \
        -Verbose ; \
    \
    Expand-Archive \
        -Path "C:\\Temp\\httpd-$ENV:APACHE_VERSION-$ENV:SSL_VERSION-x64-vc14-r3.zip" \
        -DestinationPath 'C:\\' \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';C:\Apache24\bin') \
        -Verbose ;

# Test application
RUN httpd \
       -V

RUN \
    httpd \
        -k install \
        -n "Apache$($ENV:APACHE_VERSION.SubString(0,3))"

RUN \
    httpd \
        -n "Apache$($ENV:APACHE_VERSION.SubString(0,3))" \
        -t

RUN \
    Start-Service \
        -Name "Apache$($ENV:APACHE_VERSION.SubString(0,3))" \
        -Verbose ;

# Remove temporary items from the build image
RUN \
    Remove-Item \
        -Path 'C:\Temp' \
        -Recurse \
        -Verbose ;