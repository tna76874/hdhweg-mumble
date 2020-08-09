# MUMBLE

> Docker Mumble-Server with letsencrypt and a HTML web client

### Requirements

You need to have a server and a domain linked to it. [Docker and Docker-compose](https://docs.docker.com/engine/install/ubuntu/) needs to be installed, but this can also be handled by the install script. This script is tested on Ubuntu 18.04.

### Installation

This repository aims to deploy a mumble-server on your machine in a containerized docker image. The certificates for the SSL encryption can either be self-generated (not recommended) or obtained by letsencrypt. 

To deploy the mumble-server, just clone the repository and run the install script. A secure admin password will be generated.

```bash
sudo ./install.sh
```
You can change the settings in the file `.env`, as described [here](https://github.com/sudoforge/docker-images/tree/master/mumble-server). When done, you can startup the docker-compose file with:

```bash
docker-compose up -d
```

Even on a restart of the host system, the mumble-server will also restart. You can shut down the server again with:

```bash
docker-compose down
```

### HTML Client

Included is a [HTML web client ](https://github.com/Johni0702/mumble-web). To deactivate the access:

```bash
sudo ./install.sh -d
```



### Syntax

```bash
Usage: ./install.sh -[p|s|r|n|d]

   -p,      Install prerequisites (docker, docker-compose)
   -s,      Setup environment
   -r,      Disable cronjob to renew certificates
   -n,      Generate nginx virtual and certificates
   -d,      Deactivate access to HTML client
   -h,      Print this help text

If the script will be called without parameters, it will run:
    ./install.sh -p -s -n
```

### References

[Mumble wiki](https://wiki.mumble.info/wiki/3rd_Party_Applications) 

[mumble server](https://github.com/sudoforge/docker-images/tree/master/mumble-server) 

[mumble web](https://github.com/Johni0702/mumble-web)