FROM kiazhi/nanoserver.java.jre:sac2016-oracle-8u172 AS build

LABEL \
    org.label-schema.name="NanoServer.elastic.elasticsearch" \
    org.label-schema.description="This image is an ElasticSearch from Elastic on NanoServer image." \
    org.label-schema.version="1.0.0" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.vendor="Ryen Kia Zhi Tang" \
    org.label-schema.url="https://www.elastic.co/products/elasticsearch" \
    org.label-schema.maintainer.name="Ryen Kia Zhi Tang" \
    org.label-schema.vcs-url="https://github.com/kiazhi/Windows-Containers"\
    org.label-schema.docker.cmd="docker run --name $CONTAINER -t -d nanoserver.elastic.elasticsearch:latest" \
    org.label-schema.docker.cmd.test="docker exec $CONTAINER elasticsearch --version" \
    org.label-schema.docker.cmd.debug="docker exec -it $CONTAINER powershell" \
    org.label-schema.docker.docker.cmd.help="docker exec $CONTAINER elasticsearch --help" \
    org.label-schema.docker.params="ELASTICSEARCH_VERSION=version number"

ARG ELASTICSEARCH_VERSION=6.2.4

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
        -Uri "https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-$ENV:ELASTICSEARCH_VERSION.zip" \
        -OutFile "C:\\Temp\\elasticsearch-$ENV:ELASTICSEARCH_VERSION.zip" \
        -UseBasicParsing \
        -Verbose ; \
    \
    Expand-Archive \
        -Path "C:\\Temp\\elasticsearch-$ENV:ELASTICSEARCH_VERSION.zip" \
        -DestinationPath $ENV:ProgramFiles \
        -Verbose ; \
    \
    (Get-Content \
        -Path $($ENV:ProgramFiles + '\elasticsearch-' + $ENV:ELASTICSEARCH_VERSION + '\config\jvm.options') \
        -Verbose) \
            -replace '-Xms1g','-Xms200m' | Set-Content \
                -Path $($ENV:ProgramFiles + '\elasticsearch-' + $ENV:ELASTICSEARCH_VERSION + '\config\jvm.options') \
                -Verbose ; \
    \
    (Get-Content \
        -Path $($ENV:ProgramFiles + '\elasticsearch-' + $ENV:ELASTICSEARCH_VERSION + '\config\jvm.options') \
        -Verbose) \
        -replace '-Xmx1g','-Xmx200m' | Set-Content \
            -Path $($ENV:ProgramFiles + '\elasticsearch-' + $ENV:ELASTICSEARCH_VERSION + '\config\jvm.options') \
            -Verbose ; \
    \
    (Get-Content \
        -Path $($ENV:ProgramFiles + '\elasticsearch-' + $ENV:ELASTICSEARCH_VERSION + '\config\elasticsearch.yml') \
        -Verbose) \
            -replace '#network.host: 192.168.0.1','network.host: 0.0.0.0' | Set-Content \
                -Path $($ENV:ProgramFiles + '\elasticsearch-' + $ENV:ELASTICSEARCH_VERSION + '\config\elasticsearch.yml') \
                -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'ES_HOME' \
        -Value $($ENV:ProgramFiles + '\elasticsearch-' + $ENV:ELASTICSEARCH_VERSION) \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'ES_PATH_CONF' \
        -Value $($ENV:ProgramFiles + '\elasticsearch-' + $ENV:ELASTICSEARCH_VERSION +'\config') \
        -Verbose ; \
    \
    Set-ItemProperty \
        -Path 'HKLM:\\SYSTEM\\CurrentControlSet\\Control\\Session Manager\\Environment' \
        -Name 'Path' \
        -Value $($ENV:Path + ';' + $ENV:ProgramFiles + '\elasticsearch-' + $ENV:ELASTICSEARCH_VERSION + '\bin') \
        -Verbose ;

# Test application
RUN elasticsearch \
       --version

# Remove temporary items from the build image
RUN \
    Remove-Item \
        -Path 'C:\Temp' \
        -Recurse \
        -Verbose ;