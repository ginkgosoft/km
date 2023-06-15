# Install alfresco with docker-compose.yml

```dockercompose
# This docker-compose.yml file is used to spin up an Alfresco Content Services (ACS) trial cluster on a local host or on a server and it requires a minimum of 16GB Memory to distribute among containers.

# To use this file to create a local installation of Alfresco Content Services, you need to have Docker Compose installed [https://docs.docker.com/compose/install/].
# Navigate to the folder where this file is located, and issue the following commands:
#
#     docker login quay.io -u="alfresco+acs_v6_trial" -p="MDF9RNGUJPKZ83KK8UVGUVWO9AYKUZ0VN6WG5VOOCUT6BX19JJLU5ZL0HKU7N20C"
#     docker-compose up
#

# For additional information about using this docker-compose file, please see:
# https://github.com/Alfresco/acs-deployment/blob/master/docs/docker-compose-deployment.md

# You may wish to limit container memory and assign a certain percentage to JVM. There are couple of ways to allocate JVM Memory for ACS Containers
# For example: 'JAVA_OPTS: "$JAVA_OPTS -XX:+PrintFlagsFinal -XX:+UnlockExperimentalVMOptions -XX:+UseCGroupMemoryLimitForHeap"'
# If container memory is not explicitly set, then the above flags will default max heap to 1/4th of container's memory.
# CATALINA_OPTS: "-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005"
version: "2"

services:
    alfresco:
        image: quay.io/alfresco/alfresco-content-repository:7.3.0
        mem_limit: 1900m
        depends_on:
            - gks-identity-service
            - postgres
        environment:
            JAVA_TOOL_OPTIONS: -Dencryption.keystore.type=JCEKS -Dencryption.cipherAlgorithm=DESede/CBC/PKCS5Padding -Dencryption.keyAlgorithm=DESede -Dencryption.keystore.location=/usr/local/tomcat/shared/classes/alfresco/extension/keystore/keystore -Dmetadata-keystore.password=mp6yc0UD9e -Dmetadata-keystore.aliases=metadata -Dmetadata-keystore.metadata.password=oKIWzVdEdA -Dmetadata-keystore.metadata.algorithm=DESede
            JAVA_OPTS: "-Ddb.driver=org.postgresql.Driver
                -Ddb.username=alfresco
                -Ddb.password=alfresco
                -Ddb.url=jdbc:postgresql://postgres:5432/alfresco
                -Dsolr.host=solr6
                -Dsolr.port=8983
                -Dsolr.secureComms=secret
                -Dsolr.sharedSecret=secret
                -Dsolr.base.url=/solr
                -Dindex.subsystem.name=solr6
                -Dshare.host=127.0.0.1
                -Dshare.port=8080
                -Dalfresco.host=localhost
                -Dalfresco.port=8080
                -Daos.baseUrlOverwrite=http://localhost:8080/alfresco/aos
                -Dmessaging.broker.url=\"failover:(nio://activemq:61616)?timeout=3000&jms.useCompression=true\"
                -Ddeployment.method=DOCKER_COMPOSE
                -Dtransform.service.enabled=true
                -Dtransform.service.url=http://transform-router:8095
                -Dsfs.url=http://shared-file-store:8099/
                -DlocalTransform.core-aio.url=http://transform-core-aio:8090/
                -Dcsrf.filter.enabled=false
                -Ddsync.service.uris=http://localhost:9090/alfresco
                -DtrialUid=id759203
                -XX:MinRAMPercentage=50
                -XX:MaxRAMPercentage=80
                -Dauthentication.chain=identity-service1:identity-service
                -Didentity-service.enable-basic-auth=true
                -Didentity-service.auth-server-url=https://api.asgardeo.io/t/squidroll/oauth2/authorize
                -Didentity-service.realm=alfresco
                -Didentity-service.resource=alfresco"
                
    transform-router:
        mem_limit: 512m
        image: quay.io/alfresco/alfresco-transform-router:2.0.0
        environment:
            JAVA_OPTS: " -XX:MinRAMPercentage=50 -XX:MaxRAMPercentage=80"
            ACTIVEMQ_URL: "nio://activemq:61616"
            CORE_AIO_URL: "http://transform-core-aio:8090"
            FILE_STORE_URL: "http://shared-file-store:8099/alfresco/api/-default-/private/sfs/versions/1/file"
        ports:
            - "8095:8095"
        links:
            - activemq

    transform-core-aio:
        image: alfresco/alfresco-transform-core-aio:3.0.0
        mem_limit: 1536m
        environment:
            JAVA_OPTS: " -XX:MinRAMPercentage=50 -XX:MaxRAMPercentage=80"
            ACTIVEMQ_URL: "nio://activemq:61616"
            FILE_STORE_URL: "http://shared-file-store:8099/alfresco/api/-default-/private/sfs/versions/1/file"
        ports:
            - "8090:8090"
        links:
            - activemq

    shared-file-store:
        image: quay.io/alfresco/alfresco-shared-file-store:2.0.0
        mem_limit: 512m
        environment:
            JAVA_OPTS: " -XX:MinRAMPercentage=50 -XX:MaxRAMPercentage=80"
            scheduler.content.age.millis: 86400000
            scheduler.cleanup.interval: 86400000
        ports:
            - "8099:8099"
        volumes:
            - shared-file-store-volume:/tmp/Alfresco/sfs

    share:
        image: quay.io/alfresco/alfresco-share:7.3.0
        mem_limit: 1g
        environment:
            REPO_HOST: "alfresco"
            REPO_PORT: "8080"
            JAVA_OPTS: -XX:MinRAMPercentage=50 -XX:MaxRAMPercentage=80 -Dalfresco.host=localhost -Dalfresco.port=8080 -Dalfresco.context=alfresco -Dalfresco.protocol=http
    postgres:
        image: postgres:14.4
        mem_limit: 512m
        environment:
            - POSTGRES_PASSWORD=alfresco
            - POSTGRES_USER=alfresco
            - POSTGRES_DB=alfresco
        command: postgres -c max_connections=300 -c log_min_messages=LOG
        ports:
            - "5432:5432"

    gks-identity-service:
        image: jboss/keycloak:16.1.1
        environment: 
            KEYCLOAK_USER: admin
            KEYCLOAK_PASSWORD: admin
            POSTGRES_PORT_5432_TCP_ADDR: postgres
            POSTGRES_PORT_5432_TCP_PORT: "5432"
            POSTGRES_DATABASE: keycloak
            POSTGRES_USER: alfresco
            POSTGRES_PASSWORD: alfresco
            ports:
                - "8080:8080"
        depends_on:
             - postgres

    solr6:
        image: alfresco/alfresco-search-services:2.0.5
        mem_limit: 2g
        environment:
      # Solr needs to know how to register itself with Alfresco
            SOLR_ALFRESCO_HOST: "alfresco"
            SOLR_ALFRESCO_PORT: "8080"
      # Alfresco needs to know how to call solr
            SOLR_SOLR_HOST: "solr6"
            SOLR_SOLR_PORT: "8983"
      # Create the default alfresco and archive cores
            SOLR_CREATE_ALFRESCO_DEFAULTS: "alfresco,archive"
      # HTTPS or SECRET
            ALFRESCO_SECURE_COMMS: "secret"
      # SHARED SECRET VALUE
            JAVA_TOOL_OPTIONS: -Dalfresco.secureComms.secret=secret
        ports:
            - "8083:8983" # Browser port

    activemq:
        image: alfresco/alfresco-activemq:5.17.1-jre11-rockylinux8
        mem_limit: 1g
        ports:
            - "8161:8161" # Web Console
            - "5672:5672" # AMQP
            - "61616:61616" # OpenWire
            - "61613:61613" # STOMP

    digital-workspace:
        image: quay.io/alfresco/alfresco-digital-workspace:3.1.0
        mem_limit: 128m
        environment:
            APP_CONFIG_AUTH_TYPE: "BASIC"
            BASE_PATH: ./
            APP_BASE_SHARE_URL: "http://localhost:8080/workspace/#/preview/s"

    control-center:
        image: quay.io/alfresco/alfresco-admin-app:7.6.0
        mem_limit: 128m
        environment:
            APP_CONFIG_PROVIDER: "ECM"
            APP_CONFIG_AUTH_TYPE: "BASIC"
            BASE_PATH: ./

    proxy:
        image: alfresco/alfresco-acs-nginx:3.4.2
        mem_limit: 128m
        depends_on:
            - alfresco
            - digital-workspace
            - control-center
        ports:
            - "8080:8080"
        links:
            - digital-workspace
            - alfresco
            - share
            - control-center

    sync-service:
        image: quay.io/alfresco/service-sync:3.8.0
        mem_limit: 1g
        environment:
            JAVA_OPTS: -Dsql.db.driver=org.postgresql.Driver -Dsql.db.url=jdbc:postgresql://postgres:5432/alfresco -Dsql.db.username=alfresco -Dsql.db.password=alfresco -Dmessaging.broker.host=activemq -Drepo.hostname=alfresco -Drepo.port=8080 -Ddw.server.applicationConnectors[0].type=http -XX:MinRAMPercentage=50 -XX:MaxRAMPercentage=80
        ports:
            - "9090:9090"

volumes:
    shared-file-store-volume:
        driver_opts:
            type: tmpfs
            device: tmpfs

```
