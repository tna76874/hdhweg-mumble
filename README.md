# MUMBLE

> Docker Mumble-Server with letsencrypt and a HTML web client

### Requirements

You need to have a server and a domain linked to it. [Docker and Docker-compose](https://docs.docker.com/engine/install/ubuntu/) needs to be installed, but this can also be handled by the install script. This script is tested on Ubuntu 18.04.

### Installation

This repository aims to deploy a mumble-server on your machine in a containerized docker image. The certtificates for the SSL encryption can either be self-generated (not recommended) or obtained by letsencrypt. The generation of the letsencrypt-certificates will also be handeled by a [docker-instance of certbot](https://github.com/certbot-docker/certbot-docker). Also it is recommended to enable a cronjob for the renewal of the certificates. The method with the docker-certbot has the advantage, that it is independent of other applications running on your server. On the other hand, a system webserver, listening on port 80, has to be shut down while the letsencrypt-certificates are fetched.

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

Included is the optional [HTML web client ](https://github.com/Johni0702/mumble-web), that can be activated by generating the nginx virtual host:

```bash
sudo ./install.sh -n
```



### Syntax

```bash
Usage: ./install.sh -[p|s|c|r|e|d|n|h]

   -p,      Install prerequisites (docker, docker-compose)
   -s,      Setup environment
   -c,      (Re)generate letsencrypt certificates
   -r,      Renew certificates
   -e,      Enable cronjob to renew certificates
   -d,      Disable cronjob to renew certificates
   -n,      Generate nginx virtual host for mumble webserver
   -h,      Print this help text

If the script will be called without parameters, it will run:
    ./install.sh -p -s -c -e -n
```

### References

[Mumble wiki](https://wiki.mumble.info/wiki/3rd_Party_Applications) 

[mumble server](https://github.com/sudoforge/docker-images/tree/master/mumble-server) 

[mumble web](https://github.com/Johni0702/mumble-web)