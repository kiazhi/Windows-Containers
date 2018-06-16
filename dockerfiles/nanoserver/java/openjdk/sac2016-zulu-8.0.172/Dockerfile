FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.Java.OpenJDK" \
    org.label-schema.description="This image is an OpenJDK (Java) from Azul Systems® Zulu on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://www.azul.com/" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.java.openjdk:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER java -version" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER java -help" \
    org.label-schema.docker.params="OPENJDK_VERSION=version number"

ARG OPENJDK_VERSION=8.0.172

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
        -Uri "https://cdn.azul.com/zulu/bin/zulu8.30.0.1-jdk$ENV:OPENJDK_VERSION-win_x64.zip" \
        -OutFile "C:\\Temp\\zulu8.30.0.1-jdk$ENV:OPENJDK_VERSION-win_x64.zip" \
        -UseBasicParsing \
        -Verbose ; \
    \
    Expand-Archive \
        -Path "C:\\Temp\\zulu8.30.0.1-jdk$ENV:OPENJDK_VERSION-win_x64.zip" \
        -DestinationPath 'C:\Program Files\Zulu' \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'JAVA_HOME' \
        -Value $('C:\Program Files\Zulu\zulu8.30.0.1-jdk' + $ENV:OPENJDK_VERSION + '-win_x64') \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';C:\Program Files\Zulu\zulu8.30.0.1-jdk' + $ENV:OPENJDK_VERSION + '-win_x64\bin') \
        -Verbose ;

# Test application
RUN java \
       -version

RUN javac \
        -version

# Remove temporary items from the build image
RUN \
    Remove-Item \
        -Path 'C:\Temp' \
        -Recurse \
        -Verbose ;