# Sample YAML with Identity Service

```
// Some code
# This is a YAML-formatted file.
# Declare variables to be passed into your templates.
global:
  keycloak:
    url: "http://alfresco-identity-service.REPLACEME.nip.io/auth"

alfresco-infrastructure:
  persistence:
    storageClass:
      enabled: true
      name: "hostpath"
  alfresco-identity-service:
    keycloak:
      postgresql:
        postgresPassword: "keycloak" #Setting this password is only needed for 1.5.0 chart version

alfresco-content-services:
  alfresco-digital-workspace:
    APP_CONFIG_OAUTH2_HOST: "http://alfresco-identity-service.REPLACEME.nip.io/auth/realms/alfresco"
  repository:
    environment:
      IDENTITY_SERVICE_URI: "http://alfresco-identity-service.REPLACEME.nip.io/auth"
      JAVA_OPTS: " -Dsolr.base.url=/solr
        -Dsolr.secureComms=none
        -Dindex.subsystem.name=solr6
        -Dalfresco.cluster.enabled=true
        -Ddeployment.method=HELM_CHART
        -Xms1200M -Xmx1200M
        -Ddsync.service.uris=\"$SYNC_SERVICE_URI\"
        -Dauthentication.chain=identity-service1:identity-service,alfrescoNtlm1:alfrescoNtlm
        -Didentity-service.enable-basic-auth=true
        -Didentity-service.authentication.validation.failure.silent=false
        -Didentity-service.auth-server-url=\"$IDENTITY_SERVICE_URI\"
        -Didentity-service.realm=alfresco
        -Didentity-service.resource=alfresco
        -Dlocal.transform.service.enabled=false
        -Dtransform.service.enabled=false"
    replicaCount: 1
    livenessProbe:
      initialDelaySeconds: 460
    readynessProbe:
      initialDelaySeconds: 500
    resources:
      requests:
        memory: "1200Mi"
  alfresco-search:
    livenessProbe:
      initialDelaySeconds: 450
  transformrouter:
    replicaCount: 1
  transformmisc:
    replicaCount: 1
    resources:
      requests:
        memory: "512Mi"
      limits:
        memory: "512Mi"
  imagemagick:
    replicaCount: 1
    livenessProbe:
      initialDelaySeconds: 450
    resources:
      requests:
        memory: "512Mi"
      limits:
        memory: "512Mi"
  libreoffice:
    replicaCount: 1
    livenessProbe:
      initialDelaySeconds: 450
  pdfrenderer:
    replicaCount: 1
    livenessProbe:
      initialDelaySeconds: 450
    resources:
      requests:
        memory: "512Mi"
      limits:
        memory: "512Mi"
  tika:
    replicaCount: 1
    livenessProbe:
      initialDelaySeconds: 450
    resources:
      requests:
        memory: "512Mi"
      limits:
        memory: "512Mi"
  share:
    environment:
      JAVA_OPTS: " -Daims.enabled=true
        -Daims.realm=alfresco
        -Daims.resource=alfresco
        -Daims.publicClient=true
        -Daims.authServerUrl=\"https://alfresco-identity-service.REPLACEME.nip.io/auth\""
    replicaCount: 1
    resources:
      requests:
        memory: "1000Mi"
      limits:
        memory: "1000Mi"
  filestore:
    livenessProbe:
      initialDelaySeconds: 450
    resources:
      requests:
        memory: "512Mi"
      limits:
        memory: "512Mi"
  externalHost: "alfresco-cs-repository.REPLACEME.nip.io"

alfresco-process-services:
  ingress:
    protocol: http
    hostName: 'alfresco-process.REPLACEME.nip.io'
  processEngine:
    environment:
      IDENTITY_SERVICE_AUTH: "http://alfresco-identity-service.REPLACEME.nip.io/auth"
  resources:
    requests:
      memory: "1000Mi"
    limits:
      memory: "1000Mi"
  processWorkspace:
    environment:
      APP_CONFIG_BPM_HOST: "http://alfresco-process.REPLACEME.nip.io"
      APP_CONFIG_ECM_HOST: "http://alfresco-cs-repository.REPLACEME.nip.io"
      APP_CONFIG_OAUTH2_HOST: "http://alfresco-identity-service.REPLACEME.nip.io/auth/realms/alfresco"
      APP_CONFIG_OAUTH2_REDIRECT_SILENT_IFRAME_URI: "http://alfresco-process.REPLACEME.nip.io/process-workspace/assets/silent-refresh.html"
```
