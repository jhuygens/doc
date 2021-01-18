---
description: >-
  This is a quick start guide for Huygens Search API, which will tell you how to
  install and config the API.
---

# Quick start guide

## Install

At a minimum, Huygens Search API requires curl, [Docker Engine 19.03.2 ](https://docs.docker.com/engine/)\(or latest\) versión and [Docker Compose 3.1](https://docs.docker.com/compose/install/) \(or latest\) to be installed. This tools are needed for run the Huygens Search API .

{% hint style="info" %}
See this [guide](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04) for how install Docker Engine and Docker Compose in your computer or see the official Docker [documentation](https://docs.docker.com/get-docker/).
{% endhint %}

### Linux and macOS

1. Download the installation resources:

```
$ curl -sLf https://github.com/jhuygens/deploy
```

{% hint style="success" %}
 or clone this repository: [`https://github.com/jhuygens/deploy`](https://github.com/jhuygens/deploy)\`\`
{% endhint %}

2. In deploy directory run the follows commands:

```bash
# This command will download the necessary docker images 
# to compile and put the API modules online
$ sudo docker-compose build
```

{% hint style="warning" %}
It will ask for the MIJU user credentials. This may take several minutes.
{% endhint %}

