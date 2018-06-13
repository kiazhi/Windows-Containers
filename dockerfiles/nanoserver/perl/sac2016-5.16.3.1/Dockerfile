FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.Perl" \
    org.label-schema.description="This image is a Perl on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://perl.org" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.perl:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER perl -v" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER perl -h" \
    org.label-schema.docker.params="PERL_VERSION=version number"

SHELL ["powershell", "-Command"]

ARG PERL_VERSION=5.16.3.1

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
        -Uri "http://strawberryperl.com/download/$ENV:PERL_VERSION/strawberry-perl-$ENV:PERL_VERSION-64bit.zip" \
        -OutFile "C:\\Temp\\strawberry-perl-$ENV:PERL_VERSION-64bit.zip" \
        -UseBasicParsing \
        -Verbose ; \
    \
    Expand-Archive \
        -Path "C:\\Temp\\strawberry-perl-$ENV:PERL_VERSION-64bit.zip" \
        -DestinationPath 'C:\Program Files\Perl' \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';C:\Program Files\Perl\perl\bin;C:\Program Files\Perl\perl\site\bin;C:\Program Files\Perl\c\bin') \
        -Verbose ;

# Test application
RUN perl \
       -v

# Remove temporary items from the build image
RUN \
    Remove-Item \
        -Path 'C:\Temp' \
        -Recurse \
        -Verbose ;