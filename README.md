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

The base environmet consists of several container. These container environment is defined by the base-env.yml file.



## Reverse Proxy

As a reverse proxy the [Caddy-Proxy-Manager](https://github.com/lucaslorentz/caddy-docker-proxy) is used.

