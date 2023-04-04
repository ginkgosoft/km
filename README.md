# How to install and run docker containers using docker-compose

Compose is a tool used for running multi-container applications by defining the Docker parameters in a YAML file. Instead of passing different parameters through the command-line while running a Docker container, these parameters are defined in the YAML file and with a single command, you can start multiple Docker containers. This article describes the procedure for running Docker containers using docker-compose.

### Prerequisites <a href="#m_59251e72-29e5-4809-a43c-1f565c97bda4" id="m_59251e72-29e5-4809-a43c-1f565c97bda4"></a>

* A Webdock cloud Ubuntu instance (18.04 or later)
* You have shell (SSH) access to your VPS
* Docker installed on your Ubuntu instance

### Installing docker-compose <a href="#m_925645f0-9df8-47f5-a85b-29ccea73bd90" id="m_925645f0-9df8-47f5-a85b-29ccea73bd90"></a>

First, remove the old version of docker-compose if installed.

```
$ sudo apt remove docker-compose
```

Download the current stable release of docker-compose.

```
$ sudo curl -L "https://github.com/docker/compose/releases/download/v2.12.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

Note: Please check the [GitHub repo](https://github.com/docker/compose/releases/) for the latest stable docker-compose binary. Replace the **v2.12.2** in the above URL to fetch another version of docker-compose.

Apply execute permissions to the downloaded binary.

```
$ sudo chmod +x /usr/local/bin/docker-compose
```

Create a symlink to /usr/bin directory.

```
$ sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

Check the docker-compose version to verify installation.

```
$ docker-compose --version
```

### Creating docker-compose file <a href="#m_2c8080b4-f092-4ec5-b73d-1654e9757c75" id="m_2c8080b4-f092-4ec5-b73d-1654e9757c75"></a>

First create a new directory on your Webdock instance and go inside this directory.

```
$ mkdir ~/docker-compose
$ cd ~/docker-compose
```

Create a new file named docker-compose.yml.

```
$ touch docker-compose.yml
```

Open the file in your favorite editor.

```
$ nano docker-compose.yml
```

The docker-compose.yml file, as the name describes, is a file written in YAML format. The first option in this file is the compose version.

The version describes the compose file format for a specific version. It can be added in the compose file as below.

```
version: "3.8"
```

The compose file can contain configuration for multiple services (docker containers). These services are defined under the services option.

```
version: "3.8"

services:

  mysql_service:
```

Now under the **mysql\_service** option, we will add mysql container options as key value pairs. The important options are

* **image:** This describes which docker image will be used for this specific service.
* **container\_name:** Specifies the name of the docker container.
* **restart:** It specifies the container restart policy. There are four values for this option.
  * **no →** docker container will not start after it stops.
  * **unless-stopped** → docker container restarts after application crashes or process ends. But will not start after it is manually stopped.
  * **always →** docker container always restarts after docker service is restarted even if you manually stop it.
  * **on-failure** → docker container will only restart when an application crashes inside the container.
* **ports:** It is the list of port mappings from docker container to docker host.
* **environment:** It takes a list of environment variables passed inside the container.
* **volumes:** This option accepts a list of volumes mounted from docker container to docker host.
* **networks:** This option also specifies a list of different networks the docker container will be part of.

So the final compose file for mysql service will look like this.

```
version: "3.8"

services:

   mysql_service:

    image: mysql:8.0.23

    container_name: mysql

    restart: unless-stopped

    ports:

        - "3300:3306"

    environment:

        - MYSQL_ROOT_PASSWORD=super-secret-password

        - MYSQL_DATABASE=webdock

    volumes:

        - mysql-vol:/var/lib/mysql

    networks:

        - webdock


networks:

    webdock:

volumes:

   mysql-vol:
```

The volumes and networks used inside the compose file must be initialized at the end of the compose file.

The above compose file will create a docker network named webdock and a docker volume named mysql-vol.

After this, it will create a docker container named **mysql** from **mysql:8.0.23** docker image. By default the docker image is pulled from DockerHub.

The port **3306** of the created docker container will be mapped to the port **3300** of the docker host (Webdock instance).

This compose file will set the root password of the mysql database to **super-secret-password** and an initial database named **webdock** will be created.

The **/var/lib/mysql** directory inside the docker container will be mapped to the **mysql-vol** docker volume on docker host for data persistence.

This container will be part of the newly created docker network named **webdock**. If you run another container inside the same network, these two containers will be able to communicate with each other by their container names.

### Running docker-compose <a href="#m_eb1e7ebb-9637-4f0b-8dd4-5c515ab5459d" id="m_eb1e7ebb-9637-4f0b-8dd4-5c515ab5459d"></a>

Now save the file and run the following command to create the docker container using docker-compose.

```
$ docker-compose up
```

It will run the docker-compose in the foreground and you can not exit the terminal. To run the compose in background, add the -d option with the command.

```
$ docker-compose up -d
```

If the docker-compose.yml file is not present in the current working directory or the name of the file is other than docker-compose.yml, use the **-f** option to specify the compose file.

```
$ docker-compose -f ~/docker-compose/docker-compose.yml up -d
```

After running compose, check the status of the docker container.

```
$ docker-compose ps
```

OR

```
$ docker-compose -f ~/docker-compose/docker-compose.yml ps
```

Check the logs of the containers for debugging.

```
$ docker-compose logs
```

OR

```
$ docker-compose -f ~/docker-compose/docker-compose.yml logs
```

### Conclusion <a href="#m_52a9dd6b-83fe-49e7-b982-a6f014007de5" id="m_52a9dd6b-83fe-49e7-b982-a6f014007de5"></a>

Compose is a tool used to configure containerized microservices using a simple configuration file. It makes the process easier to deploy a containerized application on the server. This article described how a compose file is written to deploy containerized applications.
