---
description: >-
  This is a quick start guide for Huygens Search API, which will tell you how to
  install and config the API.
---

# Quick start guide

## Install

At a minimum, Huygens Search API requires `git`, [Docker Engine 19.03.2 ](https://docs.docker.com/engine/)\(or latest\) versión and [Docker Compose 3.1](https://docs.docker.com/compose/install/) \(or latest\) to be installed. This tools are needed for run the Huygens Search API .

{% hint style="info" %}
See this [guide](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04) for how install Docker Engine and Docker Compose in your computer or see the official Docker [documentation](https://docs.docker.com/get-docker/).
{% endhint %}

### Linux and macOS

### 1. Clone the deploy resources repository:

```
$ git clone https://github.com/jhuygens/deploy
```

{% hint style="success" %}
 or download this files: [`https://github.com/jhuygens/deploy`](https://github.com/jhuygens/deploy)\`\`
{% endhint %}

### 2. In deploy directory run the follows commands:

```bash
# This command will download the necessary docker images 
# to compile and put the API modules online
$ sudo docker-compose build
```

{% hint style="warning" %}
It will ask for the super user credentials. This may take several minutes.
{% endhint %}

Upon completion you will see something like this:

```bash
...

 ---> Using cache
 ---> ea6fbd50f6c2
Step 12/12 : CMD ["./main"]
 ---> Using cache
 ---> 8d1f437ec89f
Successfully built 8d1f437ec89f
Successfully tagged deploy_search-service:latest
$
```

### 3. Then run the following command to bring the Huygens Search API online:

```bash
# The -d flag makes the Docker daemon execute the containers in background
$ sudo docker-compose up -d
```

If everything works out, you will see:

```bash
Starting deploy_mongo_1          ... done
Creating deploy_search-service_1 ... done
Creating deploy_auth-service_1   ... done
Creating deploy_gateway_1        ... done
Creating deploy_redis_1          ... done
$
```

{% hint style="success" %}
Test the Huygens Search API following the instructions in this [document](../api-reference/endpoint-reference/) to confirm that it works correctly.
{% endhint %}

### 4. View the log write by the API modules with the following command:

```bash
$ sudo docker-compose logs
```

{% hint style="info" %}
For further information about how view logs in Docker, see this [document](https://docs.docker.com/config/containers/logging/). 
{% endhint %}

If you want to stop the API execution, run the following command:

```bash
# Stops containers and removes containers, networks, volumes, 
# and images created by up
$ sudo docker-compose down
```

Output:

```bash
Removing deploy_gateway_1        ... done
Removing deploy_redis_1          ... done
Removing deploy_auth-service_1   ... done
Removing deploy_search-service_1 ... done
Removing deploy_mongo_1          ... done
Removing network deploy_default
$
```

