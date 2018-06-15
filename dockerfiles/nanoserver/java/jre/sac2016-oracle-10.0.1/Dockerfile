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

ARG JRE_VERSION=10.0.1

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
# serverjre-10.0.1_windows-x64_bin.tar.gz file is not included in this repository 
# folder.
#
# Download the package from http://download.oracle.com/otn-pub/java/jdk/10.0.1+10/fb4372174a714e6b8c52526dc134031e/serverjre-10.0.1_windows-x64_bin.tar.gz
# into this Dockerfile folder without changing the file name.

ADD serverjre-10.0.1_windows-x64_bin.tar.gz /Temp

RUN \
    New-Item \
        -Path 'C:\Program Files\Java' \
        -ItemType Directory \
        -Verbose | Out-Null ; \
    \
    Move-Item \
        -Path "C:\Temp\jdk-$ENV:JRE_VERSION" \
        -Destination $(Join-Path -Path 'C:\Program Files\Java' -ChildPath "jre-$ENV:JRE_VERSION") \
        -Force \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'JAVA_HOME' \
        -Value $('C:\Program Files\Java\jre-' + $ENV:JRE_VERSION) \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';C:\Program Files\Java\jre-' + $ENV:JRE_VERSION + '\bin') \
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