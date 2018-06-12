FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.PHP" \
    org.label-schema.description="This image is a PHP on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="http://php.net" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.php:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER php --version" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER php --help" \
    org.label-schema.docker.params="PHP_VERSION=version number"

ARG PHP_VERSION=7.0.30

SHELL ["powershell", "-Command"]

COPY vcruntime140.dll /Windows/System32/

RUN \
    if(!(Test-Path -Path 'C:\Temp')) \
    { \
        New-Item \
            -Path 'C:\Temp' \
            -ItemType Directory \
            -Verbose | Out-Null ; \
    } ; \
    Invoke-WebRequest \
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
    Invoke-WebRequest \
        -Uri "http://windows.php.net/downloads/releases/php-$ENV:PHP_VERSION-nts-Win32-VC14-x64.zip" \ 
        -OutFile "C:\Temp\php-$ENV:PHP_VERSION-nts-Win32-VC14-x64.zip" \
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
    Start-Process \
        -FilePath 'C:\Windows\System32\Dism.exe' \
        -ArgumentList '/online', '/enable-feature', '/featureName:IIS-CGI', '/all' \
        -NoNewWindow \
        -Wait ; \
    \
    Expand-Archive \
        -Path "C:\Temp\php-$ENV:PHP_VERSION-nts-Win32-VC14-x64.zip" \
        -DestinationPath 'C:\Program Files\PHP' \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';C:\Program Files\PHP') \
        -Verbose ;

RUN \
    Import-Module \
        -Name IISAdministration ; \
    \
    Get-IISConfigSection \
        -SectionPath 'system.webServer/defaultDocument' | Get-IISConfigElement \
            -ChildElementName 'files' | Get-IISConfigCollection | New-IISConfigCollectionElement \
                -ConfigAttribute @{'value'='index.php'} ; \
    \
    Get-IISConfigSection \
        -SectionPath 'system.webServer/fastCgi' | Get-IISConfigCollection | New-IISConfigCollectionElement \
          -ConfigAttribute @{'fullPath'='C:\Program Files\PHP\PHP-CGI.EXE';'maxInstances'=0;'instanceMaxRequests'=10000} ; \
    \
    Get-IISConfigSection \
        -SectionPath 'system.webServer/fastCgi' | Get-IISConfigCollection | Get-IISConfigCollectionElement \
            -ConfigAttribute @{'fullPath'='C:\Program Files\PHP\PHP-CGI.EXE'} | Get-IISConfigElement \
                    -ChildElementName 'environmentVariables' | Get-IISConfigCollection | New-IISConfigCollectionElement \
                        -ConfigAttribute @{'name'='PHP_FCGI_MAX_REQUESTS';'value'='10000'} ;  \
    \
    Get-IISConfigSection \
        -SectionPath 'system.webServer/fastCgi' | Get-IISConfigCollection | Get-IISConfigCollectionElement \
            -ConfigAttribute @{'fullPath'='C:\Program Files\PHP\PHP-CGI.EXE'} | Get-IISConfigElement \
                -ChildElementName 'environmentVariables' | Get-IISConfigCollection | New-IISConfigCollectionElement \
                    -ConfigAttribute @{'name'='PHPRC';'value'='C:\Program Files\PHP'} ; \
    \
    Get-IISConfigSection \
        -SectionPath 'system.webServer/handlers' | Get-IISConfigCollection | New-IISConfigCollectionElement \
            -ConfigAttribute @{'name'='PHP-iisfcgi';'path'='*.php';'verb'='GET,HEAD,POST';'modules'='FastCgiModule';'scriptProcessor'='C:\Program Files\PHP\PHP-CGI.EXE';'resourceType'='Either';'requireAccess'='Script'} \
            -AddAt 0 ; \
    \
    Get-ChildItem \
        -Path C:\inetpub\wwwroot \
        -File | Remove-Item \
            -Force \
            -Verbose ; \
    \
    '<? phpinfo(); ?>' | Out-File \
        -PSPath 'C:\inetpub\wwwroot\index.php' \
        -Encoding utf8 ; \
    \
    Start-Service \
        -Name WAS \
        -Verbose ; \
    \
    Start-Service \
        -Name W3SVC \
        -Verbose ;

# Test application
RUN php \
        --version

# Remove environment variables from the build image
RUN \
    Remove-Item \
        -Path 'C:\Temp' \
        -Recurse \
        -Verbose ;