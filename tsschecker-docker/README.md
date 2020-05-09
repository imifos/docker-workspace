# tsschecker-docker

Compiles and runs Tihmstar's tsschecker tool in a Docker container.

tsschecker:

https://github.com/tihmstar/tsschecker

Pulls and compiles the following libraries in addition to the tool:

  * https://github.com/libimobiledevice/libirecovery
  * https://github.com/libimobiledevice/libplist
  * https://github.com/tihmstar/tsschecker
  * https://github.com/tihmstar/libgeneral 
  * https://github.com/tihmstar/libfragmentzip
  * https://github.com/tihmstar/jssy (as submodule)

Usage:

  * Install Docker
  * Checkout this repo: ```git clone https://github.com/imifos/docker-workspace```
  * Enter the container directory.
  * Run ```docker build -t tsschecker .``` (you can choose a different name).
  * Watch the show.
  
Use cases:
  
  * ```docker run --rm tsschecker -h```
  * ```docker run --rm tsschecker --list-ios --device iPad8,3```
  * ```docker run --rm tsschecker --list-devices```

Alternative, use Docker Hub:

```
docker pull imifos/tsschecker
docker run --rm imifos/tsschecker -h
```

Notes: 

  * Needs internet access to function.
  * Performs REST requests against https://api.ipsw.me
  
