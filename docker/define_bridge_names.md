# Define bridge names in docker-compose

Docker's bridge driver [has couple of options](https://docs.docker.com/engine/reference/commandline/network_create/#bridge-driver-options) that allow configuration of the created interfaces and bridge.

Among those there is `com.docker.network.bridge.name` which description states:

> Bridge name to be used when creating the Linux bridge

With this, one can name bridges that are created when starting containers to easier observability.

In order to use is in `docker-compose` files one can do:

    version: '2.1'

    networks:
      monitoring:
        driver: bridge
        driver_opts:
          com.docker.network.bridge.name: br-monitoring

Or when creating a network on the command line:

    docker network create \
      -o "com.docker.network.bridge.name=br-monitoring" \
      monitoring_net
