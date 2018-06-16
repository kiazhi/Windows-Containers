FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.Java.OpenJDK" \
    org.label-schema.description="This image is an OpenJDK (Java) from Java on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="http://openjdk.java.net/" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.java.openjdk:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER java -version" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER java -help" \
    org.label-schema.docker.params="OPENJDK_VERSION=version number"

ARG OPENJDK_VERSION=10

SHELL ["powershell", "-Command"]

RUN \
    if(!(Test-Path -Path 'C:\Temp')) \
    { \
        New-Item \
            -Path 'C:\Temp' \
            -ItemType Directory \
            -Verbose | Out-Null ; \
    } ; 

# NOTE:
# Due to GitHub large file limit (http://git.io/iEPt8g), the 
# openjdk-10_windows-x64_bin.tar.gz file is not included in this repository 
# folder.
#
# Download the package from https://download.java.net/java/GA/jdk10/10/binaries/openjdk-10_windows-x64_bin.tar.gz
# into this Dockerfile folder without changing the file name.

ADD openjdk-10_windows-x64_bin.tar.gz /Temp

RUN \
    New-Item \
        -Path 'C:\Program Files\Java' \
        -ItemType Directory \
        -Verbose | Out-Null ; \
    \
    Move-Item \
        -Path "C:\Temp\jdk-$ENV:OPENJDK_VERSION" \
        -Destination $(Join-Path -Path 'C:\Program Files\Java' -ChildPath "jdk-$ENV:OPENJDK_VERSION") \
        -Force \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'JAVA_HOME' \
        -Value $('C:\Program Files\Java\jdk-' + $ENV:OPENJDK_VERSION) \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';C:\Program Files\Java\jdk-' + $ENV:OPENJDK_VERSION + '\bin') \
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