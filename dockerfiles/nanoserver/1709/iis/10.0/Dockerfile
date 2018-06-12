FROM microsoft/nanoserver:1709 AS build

LABEL \
    org.label-schema.name="NanoServer.IIS" \
    org.label-schema.description="This image is an IIS on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://www.iis.net" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.iis:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER powershell /c 'Import-Module -Name IISAdministration ; Get-IISSite ;'" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER 'Import-Module -Name IISAdministration ; Get-Command -Module IISAdministration ;'" \
    org.label-schema.docker.params=""

SHELL ["powershell", "-Command"]

RUN \
    if(!(Test-Path -Path 'C:\\Temp')) \
    { \
        Get-ChildItem ;\
        New-Item \
            -Path 'C:\\Temp' \
            -ItemType Directory \
            -Verbose | Out-Null ; \
    } ; 
RUN    Invoke-WebRequest \
        -Uri 'https://az880830.vo.msecnd.net/nanoserver-ga-2016/Microsoft-NanoServer-IIS-Package_base_10-0-14393-0.cab' \ 
        -OutFile 'C:\Temp\Microsoft-NanoServer-IIS-Package_base_10-0-14393-0.cab' \
        -UseBasicParsing \
        -Verbose ; \
    \
    Invoke-WebRequest \
        -Uri 'https://az880830.vo.msecnd.net/nanoserver-ga-2016/Microsoft-NanoServer-IIS-Package_English_10-0-14393-0.cab' \ 
        -OutFile 'C:\Temp\Microsoft-NanoServer-IIS-Package_English_10-0-14393-0.cab' \
        -UseBasicParsing \
        -Verbose ; \
    \
    Start-Process \
        -FilePath 'C:\Windows\System32\Dism.exe' \
        -ArgumentList '/online', '/add-package', '/packagepath:c:\Temp\Microsoft-NanoServer-IIS-Package_base_10-0-14393-0.cab' \
        -NoNewWindow \
        -Wait ; \
    \
    Start-Process \
        -FilePath 'C:\Windows\System32\Dism.exe' \
        -ArgumentList '/online', '/add-package', '/packagepath:c:\Temp\Microsoft-NanoServer-IIS-Package_English_10-0-14393-0.cab' \
        -NoNewWindow \
        -Wait ; \
    \
    Start-Process \
        -FilePath 'C:\Windows\System32\Dism.exe' \
        -ArgumentList '/online', '/add-package', '/packagepath:c:\Temp\Microsoft-NanoServer-IIS-Package_base_10-0-14393-0.cab' \
        -NoNewWindow \
        -Wait ; \
    \
    Get-ItemProperty \
        -Path 'HKLM:\SOFTWARE\Microsoft\InetStp' \
        -Name 'ProductString', 'InstallPath', 'PathWWWRoot', 'SetupString', 'VersionString' ; \
    \
    Start-Service \
        -Name WAS \
        -Verbose ; \
    \
    Start-Service \
        -Name W3SVC \
        -Verbose ;

# Test application
RUN \
    Import-Module \
        -Name IISAdministration \
        -Verbose ; \
    \
    Get-IISSite ;

# Remove environment variables from the build image
RUN \
    Remove-Item \
        -Path 'C:\\Temp' \
        -Recurse \
        -Verbose ;