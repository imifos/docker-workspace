# cyberchef-docker

Compiles and runs GCHQ's CyberChef tool in a Docker container.

https://github.com/gchq/cyberchef

Usage:

  * Install Docker
  * Checkout this repo: ```git clone https://github.com/imifos/docker-workspace```
  * Enter the container directory.
  * Run ```docker build -t cyberchef .``` (you can choose a different name).
   
Use cases:
  
  * ```docker run --rm -p 6401:8080 cyberchef```
  * http://localhost:6401/
  * Exit: Ctrl+C in container window

Notes: 

  * Using UBUNTU as base image as I also use the below in combo-containers.
 
  
