FROM microsoft/windowsservercore:latest AS build

LABEL \
    org.label-schema.name="NanoServer.APIScan" \
    org.label-schema.description="This image contains NanoServerApiScan with a subset of Windows Kits on Windows Server Core image to analyze applications compatibility on Nano Server." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://msdn.microsoft.com/en-us/library/mt588480(v=vs.85).aspx" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.apiscan:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER NanoServerApiScan /BinaryPath:. /WindowsKitsPath:..\WindowsKits" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER NanoServerApiScan /BinaryPath:. /WindowsKitsPath:..\WindowsKits" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER NanoServerApiScan /?" \
    org.label-schema.docker.params="SDK_LINKID=link id number for go.microsoft.com"

ARG SDK_LINKID=870807

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
        -Uri 'https://msdnshared.blob.core.windows.net/media/2016/04/NanoServerApiScan.zip' \
        -OutFile 'C:\Temp\NanoServerApiScan.zip' \
        -UseBasicParsing \ 
        -Verbose ; \
    \
    New-Item \
        -Path 'C:\NanoServerApiScan\Binary' \
        -ItemType Directory \
        -Force \
        -Verbose | Out-Null ; \
    \
    Expand-Archive \
        -Path 'C:\Temp\NanoServerApiScan.zip' \
        -DestinationPath 'C:\NanoServerApiScan\bin' \
        -Force \
        -Verbose ; \
    \
    Invoke-WebRequest \
        -Uri $('https://go.microsoft.com/fwlink/p/?linkid=' + $ENV:SDK_LINKID) \
        -OutFile 'C:\Temp\winsdksetup.exe' \
        -UseBasicParsing \ 
        -Verbose ; \
    \
    Start-Process \
        -FilePath 'C:\Temp\winsdksetup.exe' \
        -ArgumentList '/installpath', 'C:\NanoServerApiScan\WindowsKits\10', '/features', '+', '/q' \
        -NoNewWindow \
        -Wait \
        -Verbose ; \
    \
    Get-ChildItem \
        -Path 'C:\NanoServerApiScan\WindowsKits' \
        -File \
        -Recurse | Where-Object \
            { \
                ($_.FullName -notlike '*\WindowsKits\10\Lib\*\ucrt\x64\*') \
                -and \
                ($_.FullName -notlike '*\WindowsKits\10\Lib\*\um\x64\*') \
            } | ForEach-Object \
                { \
                    $_.FullName | Remove-Item \
                        -Verbose ; \
                } ; \
    \
    Get-ChildItem \
        -Path 'C:\NanoServerApiScan\WindowsKits' \
        -Directory \
        -Recurse | Where-Object { \
            !($_.GetFiles('*','AllDirectories')) \
            } | Remove-Item \
                -Recurse \
                -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';C:\NanoServerApiScan\bin') \
        -Verbose ;

WORKDIR /NanoServerApiScan/Binary

# Test application
RUN \
    NanoServerApiScan \
        /?

# Remove temporary items from the build image
RUN \
    Remove-Item \
        -Path 'C:\Temp' \
        -Recurse \
        -Verbose ;

# How use multi-stage build to test the binary deployed in Nano Server?
# UNCOMMENT, MODIFY source path and stage name, COPY and PASTE the codes below to the bottom of your Dockerfile
#FROM kiazhi/nanoserver.apiscan:latest AS test
#COPY --from=download ["/Program Files/SOURCE_PATH", "/NanoServerApiScan/Binary"]
#RUN NanoServerApiScan.exe /BinaryPath:. /WindowsKitsPath:..\WindowsKits