FROM microsoft/nanoserver:latest AS build

LABEL \
    org.label-schema.name="NanoServer.MongoDB" \
    org.label-schema.description="This image is a MongoDB on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://mongodb.com" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.mongodb:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER mongo --version" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER mongo --help" \
    org.label-schema.docker.params="MONGODB_VERSION=version number"

ARG MONGODB_VERSION=3.6.5

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
        -Uri "http://downloads.mongodb.org/win32/mongodb-win32-x86_64-2008plus-ssl-$ENV:MONGODB_VERSION.zip" \
        -OutFile "C:\Temp\mongodb-win32-x86_64-2008plus-ssl-$ENV:MONGODB_VERSION.zip" \
        -UseBasicParsing \ 
        -Verbose ; \
    \
    Expand-Archive \
        -Path "C:\Temp\mongodb-win32-x86_64-2008plus-ssl-$ENV:MONGODB_VERSION.zip" \
        -DestinationPath 'C:\\Program Files\\MongoDB\\Server' \
        -Verbose ; \
    \
    Rename-Item \
        -Path "C:\\'Program Files'\MongoDB\Server\mongodb-win32-x86_64-2008plus-ssl-$ENV:MONGODB_VERSION" \
        -NewName $ENV:MONGODB_VERSION \
        -Force \
        -Verbose ; \
    \
    New-Item \
        -Path "C:\\'Program Files'\MongoDB\Server\\$ENV:MONGODB_VERSION\\data" \
        -ItemType Directory \
        -Verbose | Out-Null ; \
    \
    New-Item \
        -Path "C:\\'Program Files'\MongoDB\Server\\$ENV:MONGODB_VERSION\\data\\db" \
        -ItemType Directory \
        -Verbose | Out-Null ; \
    \
    New-Item \
        -Path "C:\\'Program Files'\MongoDB\Server\\$ENV:MONGODB_VERSION\\data\\log" \
        -ItemType Directory \
        -Verbose | Out-Null ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';' + $(Join-Path -Path 'C:\Program Files\MongoDB\Server' -ChildPath "$ENV:MONGODB_VERSION\bin")) \
        -Verbose ;

# Create the MongoDB configuration file
RUN \
    Out-File \
        -InputObject 'systemLog:' \
        -FilePath "C:\\'Program Files'\MongoDB\Server\\$ENV:MONGODB_VERSION\\mongod.cfg" \
        -Encoding utf8 ; \
    \
    Out-File \
        -InputObject $([String]::Format('   {0}: {1}', \
            'destination', \
            'file')) \
        -FilePath "C:\\'Program Files'\MongoDB\Server\\$ENV:MONGODB_VERSION\\mongod.cfg" \
        -Encoding utf8 \
        -Append ; \
    \
    Out-File \
        -InputObject $([String]::Format('   {0}: {1}', \
            'path', \
            $(Join-Path -Path 'C:\Program Files\MongoDB\Server' -ChildPath "$ENV:MONGODB_VERSION\data\log\mongod.log"))) \
        -FilePath "C:\\'Program Files'\MongoDB\Server\\$ENV:MONGODB_VERSION\\mongod.cfg" \
        -Encoding utf8 \
        -Append ; \
    \ 
    Out-File \
        -InputObject 'storage:' \
        -FilePath "C:\\'Program Files'\MongoDB\Server\\$ENV:MONGODB_VERSION\\mongod.cfg" \
        -Encoding utf8 \
        -Append ; \
    \
    Out-File \
        -InputObject $([String]::Format('   {0}: {1}', \
            'dbPath', \
            $(Join-Path -Path 'C:\Program Files\MongoDB\Server' -ChildPath "$ENV:MONGODB_VERSION\data\db"))) \
        -FilePath "C:\\'Program Files'\MongoDB\Server\\$ENV:MONGODB_VERSION\\mongod.cfg" \
        -Encoding utf8 \
        -Append ; \
    \
    Out-File \
        -InputObject 'net:' \
        -FilePath "C:\\'Program Files'\MongoDB\Server\\$ENV:MONGODB_VERSION\\mongod.cfg" \
        -Encoding utf8 \
        -Append ; \
    \
    Out-File \
        -InputObject $([String]::Format('   {0}: {1}', \
            'bindIpAll', \
            'true')) \
        -FilePath "C:\\'Program Files'\MongoDB\Server\\$ENV:MONGODB_VERSION\\mongod.cfg" \
        -Encoding utf8 \
        -Append ;

# Test application
RUN \
    mongo \
        --version

# Set up MongoDB as a service
RUN \
    mongod \
        --config "C:\'Program Files'\MongoDB\Server\\$ENV:MONGODB_VERSION\\mongod.cfg" \
        --install

RUN \
    Start-Service \
        -Name MongoDB \
        -Verbose ;

# Remove temporary items from the build image
RUN \
    Remove-Item \
        -Path 'C:\\Temp' \
        -Recurse \
        -Verbose ;