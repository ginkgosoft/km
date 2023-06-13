# Install using Docker Compose

Use this information to quickly start up Content Services using Docker Compose.

> **Note:** While Docker Compose is often used for production deployments, the Docker Compose file provided is recommended for development and test environments only. Customers are expected to adapt this file to their own requirements, if they intend to use Docker Compose to deploy a production environment.

To deploy Content Services using Docker Compose, download and install [Docker](https://docs.docker.com/install/), then follow the steps below. Make sure that you’ve reviewed the prerequisites before continuing.

1.  Download the `docker-compose.yml` file by accessing the Content Services [Download Trial](https://www.alfresco.com/platform/content-services-ecm/trial/download) page, which will give you a 30-day license.

    If you already have a valid license file for Content Services 7.3, you can apply it directly to the running system. See Uploading a new license for more details.

    > **Note:** Make sure that exposed ports are open on your host computer. Check the `docker-compose.yml` file to determine the exposed ports - refer to the `host:container` port definitions. You’ll see they include 5432, 8080, 8083 and others.

    > **Note:** The Download Trial is usually updated for _major.minor_ versions of Content Services. The latest published version on our website is labelled _Version 7.3 - December 2022)_.
2.  Save the `docker-compose.yml` file in a local folder.

    For example, you can create a folder `acs-trial`.
3. Change directory to the location of your `docker-compose.yml` file.
4.  Log in to Quay.io using your credentials:

    ```
     docker login quay.io
    ```

    Alfresco customers can request Quay.io credentials by logging a ticket with [Alfresco Support](https://support.alfresco.com/). These credentials are required to pull private (Enterprise-only) Docker images from Quay.io.
5.  Deploy Content Services, including the repository, Share, Postgres database, Search Services, etc.:

    ```
     docker-compose up
    ```

    This downloads the images, fetches all the dependencies, creates each container, and then starts the system:

    ```
     ...
     Creating network "acs-trial_default" with the default driver
     Creating volume "acs-trial_shared-file-store-volume" with default driver
     Creating acs-trial_control-center_1     ... done
     Creating acs-trial_activemq_1           ... done
     Creating acs-trial_sync-service_1       ... done
     Creating acs-trial_solr6_1              ... done
     Creating acs-trial_digital-workspace_1  ... done
     Creating acs-trial_share_1              ... done
     Creating acs-trial_postgres_1           ... done
     Creating acs-trial_alfresco_1           ... done
     Creating acs-trial_shared-file-store_1  ... done
     Creating acs-trial_proxy_1              ... done
     Creating acs-trial_transform-router_1   ... done
     Creating acs-trial_transform-core-aio_1 ... done
     Attaching to acs-trial_postgres_1, acs-trial_control-center_1, acs-trial_sync-service_1, acs-trial_share_1, acs-trial_digital-workspace_1, acs-trial_alfresco_1, acs-trial_solr6_1,    acs-trial_activemq_1, acs-trial_shared-file-store_1, acs-trial_proxy_1, acs-trial_transform-router_1, acs-trial_transform-core-aio_1
     ...
    ```

    Note that the name of each container begins with the folder name you created in step 2.

    As an alternative, you can also start the containers in the background by running `docker-compose up -d`.
6.  Wait for the logs to complete, showing messages:

    ```
     ...
     alfresco_1 | 2022-12-14 14:00:50,707  INFO  ... Starting 'Transformers' subsystem, ID: [Transformers, default]
     alfresco_1 | 2022-12-14 14:00:50,874  INFO  ... Startup of 'Transformers' subsystem, ID: [Transformers, default] complete
     ...
    ```

    See [Troubleshooting](broken-reference) if you encounter errors whilst the system is starting up.
7.  Open your browser and check everything starts up correctly:

    | Service                        | Endpoint                                            | Comment                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | ------------------------------ | --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | Administration and REST APIs   | `http://localhost:8080/alfresco`                    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | Share                          | `http://localhost:8080/share`                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | Digital Workspace              | `http://localhost:8080/workspace`                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | Search Services administration | `http://localhost:8083/solr`                        | <p>To get to the Solr Admin UI it’s necessary to add a header with a secret.</p><p><em>For Safari:</em></p><p>1. Go to <strong>Develop -> Show Web Inspector -> Sources</strong>.<br>2. Click on the <strong>+</strong> next to <em>Local Overrides</em> and select <strong>Local Overrides…</strong>.<br>3. Configure URL with regular expression, using Solr host and port (e.g <code>http://localhost:8983/solr/*</code>) and add the <code>X-Alfresco-Search-Secret</code> header with the secret value.</p><p><em>For Chrome, FireFox, Opera, and Edge</em>:</p><p>1. Install the ModHeader extension.<br>2. Add the <code>X-Alfresco-Search-Secret</code> header with the secret value, as seen in the image.</p> |
    | Sync Service health check      | `http://localhost:9090/alfresco/healthcheck`        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | Admin Console                  | `http://localhost:8080/alfresco/s/enterprise/admin` |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

    If Docker is running on your local machine, the IP address will be just `localhost`.

    If you’re still using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox\_install\_windows/), you’ll need to switch to [Docker Desktop](https://docs.docker.com/install/) as Docker Toolbox is deprecated.
8. Log in as the `admin` user. Enter the default administrator password `admin`.

### Check system start up <a href="#check-system-start-up" id="check-system-start-up"></a>

Use this information to verify that the system started correctly, and to clean up the deployment.

1. Open a new terminal window.
2. Change directory to the `docker-compose` folder that you created in the deployment steps.
3.  Verify that all the services started correctly.

    1.  List the images and additional details:

        ```
         docker-compose images
        ```

        You should see a list of the services defined in your `docker-compose.yml` file (below are the tags used in the latest 7.3.0 release):

        ```
         Container                        Repository                                     Tag                       Image Id       Size
         ---------------------------------------------------------------------------------------------------------------------------------
         acs-trial_activemq_1              alfresco/alfresco-activemq                     5.17.1-jre11-rockylinux8  0cd1a9629a85   631.6 MB
         acs-trial_alfresco_1              quay.io/alfresco/alfresco-content-repository   7.3.0                     13fbb0267e48   1.349 GB
         acs-trial_control-center_1        quay.io/alfresco/alfresco-admin-app            7.6.0                     f64bca8ae242   44.64 MB
         acs-trial_digital-workspace_1     quay.io/alfresco/alfresco-digital-workspace    3.1.0                     5842196a4fb4   376.4 MB
         acs-trial_postgres_1              postgres                                       14.4                      e09e90144645   376.1 MB
         acs-trial_proxy_1                 alfresco/alfresco-acs-nginx                    3.4.2                     f9c4519b7920   23.45 MB
         acs-trial_share_1                 quay.io/alfresco/alfresco-share                7.3.0                     e77a380ab703   720.4 MB
         acs-trial_shared-file-store_1     quay.io/alfresco/alfresco-shared-file-store    2.0.0                     32d64489f2b6   607.2 MB
         acs-trial_solr6_1                 alfresco/alfresco-search-services              2.0.5                     936f6335d2e5   919.5 MB
         acs-trial_sync-service_1          quay.io/alfresco/service-sync                  3.8.0                     0418d131e179   629.2 MB
         acs-trial_transform-core-aio_1    alfresco/alfresco-transform-core-aio           3.0.0                     c97305a9232a   1.687 GB
         acs-trial_transform-router_1      quay.io/alfresco/alfresco-transform-router     2.0.0                     c084269f2c47   596.7 MB
        ```
    2.  List the running containers:

        ```
         docker-compose ps
        ```

        You should see a list of the services defined in the `docker-compose.yml` file.
    3.  View the log files for each service `<service-name>`, or container `<container-name>`:

        ```
         docker-compose logs <service-name>
         docker container logs <container-name>
        ```

        For example, to check the logs for Share, run any of the following commands:

        ```
         docker-compose logs share
         docker container logs acs-trial_share_1
        ```

        You can add an optional parameter `--tail=25` before `<container-name>` to display the last 25 lines of the logs for the selected container.

        ```
         docker-compose logs --tail=25 share
         docker container logs --tail=25 acs-trial_share_1
        ```

        Check for a success message:

        ```
         Successfully retrieved license information from Alfresco.
        ```

    Once you’ve tested the services, you can clean up the deployment by stopping the running services.
4.  Stop the session by using `CONTROL+C` in the same window as the running services:

    ```
     Gracefully stopping... (press Ctrl+C again to force)
     Stopping acs-trial_transform-router_1   ... done
     Stopping acs-trial_proxy_1              ... done
     Stopping acs-trial_transform-core-aio_1 ... done
     Stopping acs-trial_postgres_1           ... done
     Stopping acs-trial_alfresco_1           ... done
     Stopping acs-trial_solr6_1              ... done
     Stopping acs-trial_shared-file-store_1  ... done
     Stopping acs-trial_share_1              ... done
     Stopping acs-trial_sync-service_1       ... done
     Stopping acs-trial_control-center_1     ... done
     Stopping acs-trial_digital-workspace_1  ... done
     Stopping acs-trial_activemq_1           ... done
    ```
5.  Alternatively, you can open a new terminal window, change directory to the `docker-compose` folder, and run:

    ```
     docker-compose down
    ```

    This stops the running services, as shown in the previous example, and removes them from memory:

    ```
     Stopping acs-trial_transform-core-aio_1 ... done
     Stopping acs-trial_transform-router_1   ... done
     Stopping acs-trial_proxy_1              ... done
     Stopping acs-trial_shared-file-store_1  ... done
     Stopping acs-trial_solr6_1              ... done
     Stopping acs-trial_share_1              ... done
     Stopping acs-trial_alfresco_1           ... done
     Stopping acs-trial_postgres_1           ... done
     Stopping acs-trial_digital-workspace_1  ... done
     Stopping acs-trial_sync-service_1       ... done
     Stopping acs-trial_activemq_1           ... done
     Stopping acs-trial_control-center_1     ... done
     Removing acs-trial_transform-core-aio_1 ... done
     Removing acs-trial_transform-router_1   ... done
     Removing acs-trial_proxy_1              ... done
     Removing acs-trial_shared-file-store_1  ... done
     Removing acs-trial_solr6_1              ... done
     Removing acs-trial_share_1              ... done
     Removing acs-trial_alfresco_1           ... done
     Removing acs-trial_postgres_1           ... done
     Removing acs-trial_digital-workspace_1  ... done
     Removing acs-trial_sync-service_1       ... done
     Removing acs-trial_activemq_1           ... done
     Removing acs-trial_control-center_1     ... done
     Removing network acs-trial_default
    ```
6. You can use a few more commands to explore the services when they’re running. Change directory to `docker-compose` before running these:
   1.  Stop all the running containers:

       ```
        docker-compose stop
       ```
   2.  Restart the containers (after using the `stop` command):

       ```
        docker-compose restart
       ```
   3.  Starts the containers that were started with `docker-compose up`:

       ```
        docker-compose start
       ```
   4.  Stop all running containers, and remove them and the network:

       ```
        docker-compose down [--rmi all]
       ```

       The `--rmi all` option also removes the images created by `docker-compose up`, and the images used by any service. You can use this, for example, if any containers fail and you need to remove them:

       ```
        docker-compose down --rmi all
       ```

       ```
        Stopping acs-trial_transform-router_1   ... done
        Stopping acs-trial_transform-core-aio_1 ... done
        Stopping acs-trial_solr6_1              ... done
        Stopping acs-trial_sync-service_1       ... done
        Stopping acs-trial_alfresco_1           ... done
        Stopping acs-trial_shared-file-store_1  ... done
        Stopping acs-trial_postgres_1           ... done
        Stopping acs-trial_share_1              ... done
        Stopping acs-trial_control-center_1     ... done
        Stopping acs-trial_activemq_1           ... done
        Removing acs-trial_transform-router_1   ... done
        Removing acs-trial_transform-core-aio_1 ... done
        Removing acs-trial_proxy_1              ... done
        Removing acs-trial_postgres_1           ... done
        Removing acs-trial_alfresco_1           ... done
        Removing acs-trial_digital-workspace_1  ... done
        Removing acs-trial_solr6_1              ... done
        Removing acs-trial_share_1              ... done
        Removing acs-trial_control-center_1     ... done
        Removing acs-trial_sync-service_1       ... done
        Removing acs-trial_shared-file-store_1  ... done
        Removing acs-trial_activemq_1           ... done
        Removing network acs-trial_default
        Removing image quay.io/alfresco/alfresco-content-repository:7.3.0
        Removing image quay.io/alfresco/alfresco-shared-file-store:2.0.0
        Removing image quay.io/alfresco/alfresco-share:7.3.0
        Removing image postgres:14.4
        Removing image quay.io/alfresco/search-services:2.0.5
        Removing image alfresco/alfresco-activemq:5.17.1-jre11-rockylinux8
        Removing image alfresco/alfresco-transform-core-aio:3.0.0
        Removing image quay.io/alfresco/alfresco-transform-router:2.0.0
        Removing image quay.io/alfresco/alfresco-digital-workspace:3.1.0
        Removing image quay.io/alfresco/alfresco-admin-app:7.6.0
        Removing image alfresco/alfresco-acs-nginx:3.4.2
        Removing image quay.io/alfresco/service-sync:3.8.0
       ```

See the [Docker documentation](https://docs.docker.com/) for more on using Docker.

#### Deployment project in GitHub <a href="#deployment-project-in-github" id="deployment-project-in-github"></a>

See the [Alfresco/acs-deployment](https://github.com/Alfresco/acs-deployment) GitHub project for more details.

* In this project, you’ll find several Docker Compose files. The default `docker-compose.yml` file contains the latest work-in-progress deployment scripts, and installs the latest _development_ version of Content Services.
* To deploy a specific released version of Content Services, several _major.minor_ Docker Compose files are provided in the `docker-compose` folder of the project.
* To modify your development environment, for example to change or mount files in the existing images, you’ll have to create new custom Docker images (recommended approach). The same approach applies if you want to install AMP files into the repository and Share images. See the Customization guidelines for more.

Using one of the Docker Compose - Enterprise files in this project deploys the following system:

### Configure <a href="#configure" id="configure"></a>

The Docker Compose file provides some default configuration. This section lists the full set of environment variables exposed by each of the containers in the deployment.

#### Alfresco Content Repository (alfresco) <a href="#alfresco-content-repository-alfresco" id="alfresco-content-repository-alfresco"></a>

| Property            | Description                                                                                                                                                                                                          |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| JAVA\_TOOL\_OPTIONS | Adding this environment variable, allows to set sensitive values (like passwords) that are not passed as arguments to the Java Process.                                                                              |
| JAVA\_OPTS          | A set of properties that are picked up by the JVM inside the container. Any Content Services property can be passed to the container using the format `-Dproperty=value` (e.g. `-Ddb.driver=org.postgresql.Driver`). |

| Property              | Description                                                                                |
| --------------------- | ------------------------------------------------------------------------------------------ |
| JAVA\_OPTS            | A set of properties that are picked up by the JVM inside the container                     |
| REPO\_HOST            | Share needs to know how to register itself with Alfresco. The default value is `localhost` |
| REPO\_PORT            | Share needs to know how to register itself with Alfresco. The default value is `8080`      |
| CSRF\_FILTER\_REFERER | CSRF Referrer                                                                              |
| CSRF\_FILTER\_ORIGIN  | CSRF Origin                                                                                |
| USE\_SSL              | Enables ssl use if set to `true`. The default value is `false`                             |

#### Alfresco Digital Workspace (digital-workspace) <a href="#alfresco-digital-workspace-digital-workspace" id="alfresco-digital-workspace-digital-workspace"></a>

| Property                                           | Description                                                                                                              |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| BASE\_PATH                                         | The default value is `./`                                                                                                |
| APP\_CONFIG\_OAUTH2\_HOST                          | The address of the Identity Service including the realm name configured                                                  |
| APP\_CONFIG\_AUTH\_TYPE                            | The authentication type. To use Single Sign-on mode you must change this property to OAUTH. The default value is `BASIC` |
| APP\_CONFIG\_OAUTH2\_CLIENTID                      | The name of the client configured for Digital Workspace                                                                  |
| APP\_CONFIG\_OAUTH2\_REDIRECT\_SILENT\_IFRAME\_URI | The address that Digital Workspace uses to refresh authorization tokens                                                  |
| APP\_CONFIG\_OAUTH2\_REDIRECT\_LOGIN               | The URL to redirect to after a user is successfully authenticated                                                        |
| APP\_CONFIG\_OAUTH2\_REDIRECT\_LOGOUT              | The URL to redirect to after a user successfully signs out                                                               |
| APP\_BASE\_SHARE\_URL                              | Base Share URL. For example `{protocol}//{hostname}{:port}/workspace/#/preview/s`                                        |
| AUTH\_TYPE                                         | The authentication type. To use Single Sign-on mode you must change this property to OAUTH. The default value is `BASIC` |
| PROVIDER                                           | The default value is `ALL`                                                                                               |
| ENVIRONMENT\_SUFFIX                                | Only for Process Cloud instance. The default value is `_CLOUD`                                                           |
| API\_HOST                                          |                                                                                                                          |
| API\_CONTENT\_HOST                                 |                                                                                                                          |
| API\_CONTENT\_HOST\_LOCAL                          | The default value is `http://localhost:8080`                                                                             |
| API\_PROCESS\_HOST                                 |                                                                                                                          |
| OAUTH\_HOST                                        |                                                                                                                          |
| IDENTITY\_HOST                                     | The address of the Identity Service including the realm name configured.                                                 |
| E2E\_HOST                                          | The default value is `http://localhost`                                                                                  |
| E2E\_PORT                                          | The default value is `80`                                                                                                |
| API\_HOST\_CLOUD                                   |                                                                                                                          |
| API\_CONTENT\_HOST\_CLOUD                          |                                                                                                                          |
| API\_PROCESS\_HOST\_CLOUD                          |                                                                                                                          |
| OAUTH\_HOST\_CLOUD                                 |                                                                                                                          |
| IDENTITY\_HOST\_CLOUD                              |                                                                                                                          |
| E2E\_HOST\_CLOUD                                   | The default value is `http://localhost`                                                                                  |
| E2E\_PORT\_CLOUD                                   | The default value is `4200`                                                                                              |
| APP\_CONFIG\_APPS\_DEPLOYED                        | The name of the deployed application (e.g. `"[{"name": "<the name of the deployed application>"}]"`)                     |

#### Alfresco Content App (content-app) <a href="#alfresco-content-app-content-app" id="alfresco-content-app-content-app"></a>

This app is deployed by default only with the Community Compose file, `community-docker-compose.yml`.

| Property                                           | Description                                                                                                                                        |
| -------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| BASE\_PATH                                         | The default value is `./`                                                                                                                          |
| APP\_CONFIG\_PROVIDER                              | BPM/ECM/ALL. The default value is `ECM`                                                                                                            |
| APP\_CONFIG\_AUTH\_TYPE                            | The authentication type. To use Single Sign-on mode you must change this property to OAUTH. The default value is `BASIC`                           |
| APP\_CONFIG\_BPM\_HOST                             | BPM Host address. The default value is `{protocol}//{hostname}{:port}`                                                                             |
| APP\_CONFIG\_ECM\_HOST                             | ECM Host address. The default value is `{protocol}//{hostname}{:port}`                                                                             |
| APP\_CONFIG\_IDENTITY\_HOST                        |                                                                                                                                                    |
| APP\_CONFIG\_OAUTH2\_HOST                          | The address of the Identity Service including the realm name configured. The default value is `{protocol}//{hostname}{:port}/auth/realms/alfresco` |
| APP\_CONFIG\_OAUTH2\_CLIENTID                      | The name of the client configured for Content App. The default value is `alfresco`                                                                 |
| APP\_CONFIG\_OAUTH2\_IMPLICIT\_FLOW                | The default value is `true`                                                                                                                        |
| APP\_CONFIG\_OAUTH2\_SILENT\_LOGIN                 | The default value is `true`                                                                                                                        |
| APP\_CONFIG\_OAUTH2\_REDIRECT\_SILENT\_IFRAME\_URI | The address that Content App uses to refresh authorization tokens. The default value is `{protocol}//{hostname}{:port}/assets/silent-refresh.html` |
| APP\_CONFIG\_OAUTH2\_REDIRECT\_LOGIN               | The URL to redirect to after a user is successfully authenticated. The default value is `./`                                                       |
| APP\_CONFIG\_OAUTH2\_REDIRECT\_LOGOUT              | The URL to redirect to after a user successfully signs out. The default value is `./`                                                              |
| APP\_BASE\_SHARE\_URL                              | Base Share URL. The default value is `${APP_CONFIG_ECM_HOST}/#/preview/s`                                                                          |
| APP\_CONFIG\_PLUGIN\_AOS                           | Enables AOS plugin. The default value is `true`                                                                                                    |
| APP\_CONFIG\_PLUGIN\_CONTENT\_SERVICE              | Enable Content Service plugin. The default value is `true`                                                                                         |
| APP\_EXTENSIONS\_IGNORE\_REFS                      | Plugins references to exclude                                                                                                                      |

#### Alfresco Control Center (control-center) <a href="#alfresco-control-center-control-center" id="alfresco-control-center-control-center"></a>

| Property                | Description                                                                                                              |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| BASE\_PATH              | The default value is `./`                                                                                                |
| APP\_CONFIG\_AUTH\_TYPE | The authentication type. To use Single Sign-on mode you must change this property to OAUTH. The default value is `BASIC` |
| APP\_CONFIG\_PROVIDER   | Config provider. The default value is `ECM`                                                                              |

#### Alfresco Search Services (solr6) <a href="#alfresco-search-services-solr6" id="alfresco-search-services-solr6"></a>

| Property                          | Description                                                                                                                                                                                                                                                                      |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SOLR\_ALFRESCO\_HOST              | Solr needs to know how to register itself with Alfresco. The default value is `alfresco`                                                                                                                                                                                         |
| SOLR\_ALFRESCO\_PORT              | Solr needs to know how to register itself with Alfresco. The default value is `8080`                                                                                                                                                                                             |
| SOLR\_SOLR\_HOST                  | Alfresco needs to know how to call solr. The default value is `solr6`                                                                                                                                                                                                            |
| SOLR\_SOLR\_PORT                  | Alfresco needs to know how to call solr. The default value is `8983`                                                                                                                                                                                                             |
| SOLR\_CREATE\_ALFRESCO\_DEFAULTS  | Create the default alfresco and archive cores. The default value is `alfresco,archive`                                                                                                                                                                                           |
| SOLR\_OPTS                        | Options to pass when starting the Java process.                                                                                                                                                                                                                                  |
| SOLR\_HEAP                        | The Java heap assigned to Solr. The default value is `2g`                                                                                                                                                                                                                        |
| SOLR\_JAVA\_MEM                   | The exact memory settings for Solr. Note that SOLR\_HEAP takes precedence over this. The default value is `-Xms2g -Xmx2g`                                                                                                                                                        |
| MAX\_SOLR\_RAM\_PERCENTAGE        | The percentage of available memory (an integer value) to assign to Solr. Note that SOLR\_HEAP and SOLR\_JAVA\_MEM take precedence over this. The default value is `2`                                                                                                            |
| SEARCH\_LOG\_LEVEL                | The root logger level (`ERROR`, `WARN`, `INFO`, `DEBUG` or `TRACE`). The default value is `INFO`                                                                                                                                                                                 |
| ENABLE\_SPELLCHECK                | Whether spellchecking is enabled or not (`true` or `false`).                                                                                                                                                                                                                     |
| DISABLE\_CASCADE\_TRACKING        | Whether cascade tracking is enabled or not (`true` or `false`). Disabling cascade tracking will improve performance, but result in some feature loss (such as path queries).                                                                                                     |
| ALFRESCO\_SECURE\_COMMS           | Whether communication with the repository is secured (`https` or `none`). See [Alfresco Search Services implementation](https://github.com/Alfresco/InsightEngine/blob/master/search-services/README.md) for more details. The default value is `none`                           |
| SOLR\_SSL\_KEY\_STORE             | Path to SSL key store. See [Alfresco Search Services Docker Compose](https://github.com/Alfresco/InsightEngine/blob/master/search-services/README.md#use-alfresco-search-services-docker-image-with-docker-compose) steps for more details.                                      |
| SOLR\_SSL\_KEY\_STORE\_PASSWORD   | Password for key store. See [Alfresco Search Services Docker Compose](https://github.com/Alfresco/InsightEngine/blob/master/search-services/README.md#use-alfresco-search-services-docker-image-with-docker-compose) steps for more details.                                     |
| SOLR\_SSL\_KEY\_STORE\_TYPE       | Key store type. See [Alfresco Search Services Docker Compose](https://github.com/Alfresco/InsightEngine/blob/master/search-services/README.md#use-alfresco-search-services-docker-image-with-docker-compose) steps for more details. The default value is `JCEKS`                |
| SOLR\_SSL\_TRUST\_STORE           | Path to SSL trust store. See [Alfresco Search Services Docker Compose](https://github.com/Alfresco/InsightEngine/blob/master/search-services/README.md#use-alfresco-search-services-docker-image-with-docker-compose) steps for more details.                                    |
| SOLR\_SSL\_TRUST\_STORE\_PASSWORD | Password for trust store. See [Alfresco Search Services Docker Compose](https://github.com/Alfresco/InsightEngine/blob/master/search-services/README.md#use-alfresco-search-services-docker-image-with-docker-compose) steps for more details.                                   |
| SOLR\_SSL\_TRUST\_STORE\_TYPE     | Trust store type. See [Alfresco Search Services Docker Compose](https://github.com/Alfresco/InsightEngine/blob/master/search-services/README.md#use-alfresco-search-services-docker-image-with-docker-compose) steps for more details. The default value is `JCEKS`              |
| SOLR\_SSL\_NEED\_CLIENT\_AUTH     | This variable is used to configure SSL (`true` or `false`). See [Alfresco Search Services Docker Compose](https://github.com/Alfresco/InsightEngine/blob/master/search-services/README.md#use-alfresco-search-services-docker-image-with-docker-compose) steps for more details. |
| SOLR\_SSL\_WANT\_CLIENT\_AUTH     | This variable is used to configure SSL (`true` or `false`). See [Alfresco Search Services Docker Compose](https://github.com/Alfresco/InsightEngine/blob/master/search-services/README.md#use-alfresco-search-services-docker-image-with-docker-compose) steps for more details. |

#### Alfresco Transform Router (transform-router) <a href="#alfresco-transform-router-transform-router" id="alfresco-transform-router-transform-router"></a>

| Property                            | Description                                                                                                                         |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| JAVA\_OPTS                          | A set of properties that are picked up by the JVM inside the container.                                                             |
| ACTIVEMQ\_URL                       | ActiveMQ URL (in this case, the name of the container is used). The default value is `nio://activemq:61616`                         |
| ACTIVEMQ\_USER                      | ActiveMQ user. The default value is `admin`                                                                                         |
| ACTIVEMQ\_PASSWORD                  | ActiveMQ password. The default value is `admin`                                                                                     |
| TRANSFORM\_REQUEST\_QUEUE           | The default value is `org.alfresco.transform.t-request.acs`                                                                         |
| TRANSFORM\_REPLY\_QUEUE             | The default value is `org.alfresco.transform.t-reply.acs`                                                                           |
| TRANSFORM\_ENGINE\_REPLY\_QUEUE     | The default value is `org.alfresco.transform.engine.t-reply.acs`                                                                    |
| JMS\_LISTENER\_CONCURRENCY          | The default value is `1-10`                                                                                                         |
| IMAGEMAGICK\_URL                    | URL for the ImageMagick T-Engine.                                                                                                   |
| PDF\_RENDERER\_URL                  | URL for the PDF Renderer T-Engine.                                                                                                  |
| LIBREOFFICE\_URL                    | URL for the LibreOffice T-Engine.                                                                                                   |
| TIKA\_URL                           | URL for the Tika T-Engine.                                                                                                          |
| MISC\_URL                           | URL for the Miscellaneous T-Engine.                                                                                                 |
| CORE\_AIO\_URL                      | URL for the All-In-One T-Engine.                                                                                                    |
| FILE\_STORE\_URL                    | URL for the Shared File Store.                                                                                                      |
| IMAGEMAGICK\_QUEUE                  | Name of the queue used by the ImageMagick T-Engine. The default value is `org.alfresco.transform.engine.imagemagick.acs`            |
| PDF\_RENDERER\_QUEUE                | Name of the queue used by the PDF Renderer T-Engine. The default value is `org.alfresco.transform.engine.alfresco-pdf-renderer.acs` |
| LIBREOFFICE\_QUEUE                  | Name of the queue used by the LibreOffice T-Engine. The default value is `org.alfresco.transform.engine.libreoffice.acs`            |
| TIKA\_QUEUE                         | Name of the queue used by the Tika T-Engine. The default value is `org.alfresco.transform.engine.tika.acs`                          |
| MISC\_QUEUE                         | Name of the queue used by the Miscellaneous T-Engine. The default value is `org.alfresco.transform.engine.misc.acs`                 |
| CORE\_AIO\_QUEUE                    | Name of the queue used by the All-In-One Core T-Engine. The default value is `org.alfresco.transform.engine.aio.acs`                |
| TRANSFORMER\_ENGINE\_PROTOCOL       | This value can be one of the following (http, jms). The default value is `jms`                                                      |
| TRANSFORMER\_ROUTES\_FILE\_LOCATION | The default value is `transformer-pipelines.json`                                                                                   |
| MAX\_TRANSFORM\_RETRIES             | The default value is `3`                                                                                                            |
| INITIAL\_RETRY\_TIMEOUT             | The default value is `10000`                                                                                                        |
| INCREASE\_RETRY\_TIMEOUT            | The default value is `10000`                                                                                                        |
| MAX\_IN\_MEMORY\_SIZE               | Double default limit to 512KiB. The default value is `524288`                                                                       |
| HOSTNAME                            | The default value is `t-router`                                                                                                     |

#### Alfresco Transform Core AIO (transform-core-aio) <a href="#alfresco-transform-core-aio-transform-core-aio" id="alfresco-transform-core-aio-transform-core-aio"></a>

| Property                          | Description                                                                                             |
| --------------------------------- | ------------------------------------------------------------------------------------------------------- |
| JAVA\_OPTS                        | A set of properties that are picked up by the JVM inside the container.                                 |
| ACTIVEMQ\_URL                     | ActiveMQ URL (in this case, the name of the container is used).                                         |
| FILE\_STORE\_URL                  | Shared file store URL (in this case, the name of the container is used).                                |
| TRANSFORM\_ENGINE\_REQUEST\_QUEUE | Name of the queue. The default value is `org.alfresco.transform.engine.aio.acs`                         |
| PDFRENDERER\_EXE                  | Location of the PDF Renderer binary. The default value is `/usr/bin/alfresco-pdf-renderer`              |
| LIBREOFFICE\_HOME                 | Location of the LibreOffice installation. The default value is `/opt/libreoffice7.2`                    |
| IMAGEMAGICK\_ROOT                 | Location of the ImageMagick installation. The default value is `/usr/lib64/ImageMagick-7.0.10`          |
| IMAGEMAGICK\_DYN                  | Location of the ImageMagick dynamic libraries. The default value is `/usr/lib64/ImageMagick-7.0.10/lib` |
| IMAGEMAGICK\_EXE                  | Location of the ImageMagick binary. The default value is `/usr/bin/convert`                             |
| IMAGEMAGICK\_CODERS               | Location of the ImageMagick coders folder                                                               |
| IMAGEMAGICK\_CONFIG               | Location of the ImageMagick configuration folder                                                        |

#### Alfresco Shared File Store (shared-file-store) <a href="#alfresco-shared-file-store-shared-file-store" id="alfresco-shared-file-store-shared-file-store"></a>

| Property                     | Description                                                                  |
| ---------------------------- | ---------------------------------------------------------------------------- |
| JAVA\_OPTS                   | A set of properties that are picked up by the JVM inside the container.      |
| fileStorePath                | Shared File Store content storing path. The default value is `/tmp/Alfresco` |
| scheduler.contract.path      | Cleanup Scheduler contract path. The default value is `/tmp/scheduler.json`  |
| scheduler.content.age.millis | Content retention period. The default value is `86400000`                    |
| scheduler.cleanup.interval   | Cleanup Scheduler interval. The default value is `86400000`                  |

#### Alfresco Sync Service (sync-service) <a href="#alfresco-sync-service-sync-service" id="alfresco-sync-service-sync-service"></a>

| Property   | Description                                                                                                                                                                                                                                                                                                                                                                                                        |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| JAVA\_OPTS | <p>A set of properties that are picked up by the JVM inside the container. Any Sync Service property can be passed to the container using the following format <code>-Dproperty=value</code> (for example, <code>-Dsql.db.username=alfresco</code>).</p><p>For a complete list of properties that can be passed through <code>JAVA_OPTS</code> environment variable, check Alfresco Sync Service configuration</p> |

#### Alfresco Proxy (proxy) <a href="#alfresco-proxy-proxy" id="alfresco-proxy-proxy"></a>

| Property             | Description                                                                           |
| -------------------- | ------------------------------------------------------------------------------------- |
| ADW\_URL             | Digital Workspace URL inside network. The default value is `http://digital-workspace` |
| CONTROL\_CENTER\_URL | Control Center URL inside network. The default value is `http://control-center`       |
| REPO\_URL            | Repository URL inside network. The default value is `http://alfresco:8080`            |
| SHARE\_URL           | Share URL inside network. The default value is `http://share:8080`                    |
| SYNCSERVICE\_URL     | Sync service URL inside network. The default value is `http://sync-service:9090`      |
| ACCESS\_LOG          | Sets the `access_log` value. Set to `off` to switch off logging.                      |
| USE\_SSL             | Enables ssl use if set to `true`. The default value is `false`                        |
| DOMAIN               | Set domain value for ssl certificate.                                                 |

### Customize <a href="#customize" id="customize"></a>

To customize the Docker Compose deployment, for example applying AMPs, we recommend following the best practice of creating your own custom Docker image(s). The Customization guidelines walks you through this process.

### Cleanup <a href="#cleanup" id="cleanup"></a>

To bring the system down and cleanup the containers run the following command:

```
docker-compose down
```

### Troubleshooting <a href="#troubleshooting" id="troubleshooting"></a>

1.  If you have issues running `docker-compose up` after deleting a previous Docker Compose cluster, try replacing step 5 in the initial Docker Compose instructions with:

    ```
     docker-compose down && docker-compose build --no-cache && docker-compose up
    ```
2.  If you’re having issues running `docker-compose up` on Windows environments due to unavailable or reserved ports, and get errors such as: `bind: An attempt was made to access a socket in a way forbidden by its access permissions` which means that the Windows NAT (WinNAT) service has reserved the port range that Docker Compose is trying to use.

    To remedy this issue, run the following in a terminal:

    ```
     net stop winnat
     docker-compose up
     net start winnat
    ```
3. Stop the session by using `CONTROL+C`.
4.  Remove the containers (using the `--rmi all` option):

    ```
     docker-compose down --rmi all
    ```
5.  Try allocating more memory resources to Docker, as advised in `docker-compose.yml`.

    For example, in Docker, change the memory setting in **Preferences** (Mac) or **Settings** (Windows) > **Resources** > **Advanced** > **Memory** to at least 13 GB. If you make changes, click **Apply & Restart** and wait for the process to finish before continuing.

    Go back to step 5 in the initial Docker Compose instructions to start the deployment again.

When using _Linux_ as Docker host, all the memory in the computer is available to Docker Compose. So no additional actions are required.

When using [Docker with Windows Subsystem for Linux (WSL) 2 Backend](https://docs.docker.com/desktop/windows/wsl/) in _Windows_, use the `.wslconfig` file to increase the `memory` available for Docker Compose.

> **Note:** In order to deploy onto Docker Desktop you need to allocate at least 13 GB (preferably 16 GB) to the Docker Engine on the **Resources** tab in Docker Desktop’s preferences pane as shown in the screenshot below. This is required because insufficient memory will cause containers to exit without warning.

### Reference <a href="#reference" id="reference"></a>

The table below shows the location of the publicly available `Dockerfile` for the containers used in the Community deployment.

| Container          | Dockerfile location                                                                                                                                                                                                                                                                |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| alfresco           | [https://github.com/Alfresco/acs-packaging/blob/master/docker-alfresco/Dockerfile](https://github.com/Alfresco/acs-packaging/blob/master/docker-alfresco/Dockerfile)                                                                                                               |
| share              | [https://github.com/Alfresco/share/blob/master/packaging/docker/Dockerfile](https://github.com/Alfresco/share/blob/master/packaging/docker/Dockerfile)                                                                                                                             |
| content-app        | [https://github.com/Alfresco/alfresco-content-app/blob/master/Dockerfile](https://github.com/Alfresco/alfresco-content-app/blob/master/Dockerfile)                                                                                                                                 |
| solr6              | [https://github.com/Alfresco/SearchServices/blob/master/search-services/packaging/src/docker/Dockerfile](https://github.com/Alfresco/SearchServices/blob/master/search-services/packaging/src/docker/Dockerfile)                                                                   |
| transform-core-aio | [https://github.com/Alfresco/alfresco-transform-core/blob/master/alfresco-transform-core-aio/alfresco-transform-core-aio-boot/Dockerfile](https://github.com/Alfresco/alfresco-transform-core/blob/master/alfresco-transform-core-aio/alfresco-transform-core-aio-boot/Dockerfile) |
| activemq           | [https://github.com/Alfresco/alfresco-docker-activemq/blob/master/Dockerfile](https://github.com/Alfresco/alfresco-docker-activemq/blob/master/Dockerfile)                                                                                                                         |
| proxy              | [https://github.com/Alfresco/acs-ingress/blob/master/Dockerfile](https://github.com/Alfresco/acs-ingress/blob/master/Dockerfile)                                                                                                                                                   |
