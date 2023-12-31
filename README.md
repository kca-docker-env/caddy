# Set up a base docker environment

The base environment should contain: 

  * Reverse Proxy
  * Container handling


## Prepare

1. The docker service must be enabled on the device.

2. Create a docker-compose alias
  ```bash
  nano ~/.bashrc
  ```
3. Add alias to file
  ```
  alias docker-compose='docker run --rm -t \
  --privileged \
   -v $(pwd):/compose \
   -v /var/run/docker.sock:/var/run/docker.sock \
   -v /usr/bin/docker:/usr/bin/docker \
   wagoautomation/docker-compose'
  ```
4. Save file

5. Update environment to use alias within this session
  ```bash
  source ~/.bashrc
  ```


## Introduction

The base environmet consists of several container. This requires a network called caddy and must be created before the compose could be started.

```bash
docker create network caddy
```

After the network has been created, the Compose file can be executed.
To do this, the command must be executed in the folder where the *.yml file is located, or the path in the command must be adjusted.

```bash
docker-compose -f base-env.yml --detach
```

> **docker-compose**: Use defined alias to run container specified by compose file <br>
> **-f filename**: Use this file as compose-file <br>
> **--detach**: Run container in background

### Reverse Proxy

As a reverse proxy the [Caddy-Proxy-Manager](https://github.com/lucaslorentz/caddy-docker-proxy) is used.

New proxies are defiend by docker labels.

```compose
    networks:
      - caddy 
    labels: 
      caddy: example.domain
      caddy.reverse_proxy: "{{upstreams 80}}"
```

> **{{ upstream }}** is resolved to the IP address of the container. <br>
> Therefore, the container internal **port** must also be used!


### Container management

Container management is realized by [Portainer](https://docs.portainer.io/start/install-ce/server/docker/linux) in the Community Edition.
You can find more information [here](https://docs.portainer.io/).
