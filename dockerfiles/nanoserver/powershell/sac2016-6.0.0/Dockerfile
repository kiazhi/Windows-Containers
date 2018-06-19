FROM microsoft/nanoserver:latest AS download

LABEL \
    org.label-schema.name="NanoServer.PowerShell" \
    org.label-schema.description="This image is a PowerShell Core on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://github.com/PowerShell/PowerShell" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.powershell:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER pwsh -v" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER pwsh" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER pwsh -h" \
    org.label-schema.docker.params="PWSH_VERSION=version number"

ARG PWSH_VERSION=6.0.0

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
        -Uri $('https://github.com/PowerShell/PowerShell/releases/download/v' + $ENV:PWSH_VERSION + '/PowerShell-' + $ENV:PWSH_VERSION + '-win-x64.zip') \
        -OutFile $('C:\Temp\PowerShell-' + $ENV:PWSH_VERSION + '-win-x64.zip') \
        -UseBasicParsing \ 
        -Verbose ; \
    \
    Expand-Archive \
        -Path $('C:\Temp\PowerShell-' + $ENV:PWSH_VERSION + '-win-x64.zip') \
        -DestinationPath $(Join-Path -Path "$ENV:ProgramFiles\PowerShell" -ChildPath $ENV:PWSH_VERSION) \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';' + $(Join-Path -Path "$ENV:ProgramFiles\PowerShell" -ChildPath $ENV:PWSH_VERSION)) \
        -Verbose ;

# Test application
RUN \
    pwsh \
        -v

# Remove temporary items from the build image
RUN \
    Remove-Item \
        -Path 'C:\Temp' \
        -Recurse \
        -Verbose ;

CMD ["pwsh"]