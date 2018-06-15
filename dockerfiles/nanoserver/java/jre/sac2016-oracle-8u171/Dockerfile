FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.Java.JRE" \
    org.label-schema.description="This image is an JRE (Java) from Oracle on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="http://www.oracle.com/technetwork/java/javase/overview/index.html" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.java.jre:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER java -version" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER java -help" \
    org.label-schema.docker.params="JRE_VERSION=version number"

ARG JRE_VERSION=8u171

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
# server-jre-8u171-windows-x64.tar.gz file is not included in this repository 
# folder.
#
# Download the package from http://download.oracle.com/otn-pub/java/jdk/8u171-b11/512cd62ec5174c3487ac17c61aaa89e8/server-jre-8u171-windows-x64.tar.gz
# into this Dockerfile folder without changing the file name.

ADD server-jre-8u171-windows-x64.tar.gz /Temp

RUN \
    New-Item \
        -Path 'C:\Program Files\Java' \
        -ItemType Directory \
        -Verbose | Out-Null ; \
    \
    Move-Item \
        -Path "C:\Temp\jdk1.8.0_171" \
        -Destination $(Join-Path -Path 'C:\Program Files\Java' -ChildPath "jre-$ENV:JRE_VERSION") \
        -Force \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';C:\Program Files\Java\jre-' + $ENV:JRE_VERSION + '\jre\bin') \
        -Verbose ;

# Test application
RUN java \
       -version

# Remove temporary items from the build image
RUN \
    Remove-Item \
        -Path 'C:\Temp' \
        -Recurse \
        -Verbose ;