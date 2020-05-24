## Install Docker CE

Guides are available at DigitalOcean:

  - [Ubuntu 16](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04)
  - [Ubuntu 18](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04)
  - [CentOS 7](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-centos-7)

"Cleaning Up" Recipes

  - delete unused images and their dependent layers
  ```
  $ X=$(docker image ls -f dangling=true -q)
  $ [ -n "$X" ] && docker image rm $X
  ```
  - delete containers which are not running
  ```
  dockers_not_running() { typeset -A x; local y; 
                          for y in `docker ps -aq`; do x[$y]=1; done; 
                          for y in `docker ps -q`;  do unset x[$y]; done; echo ${!x[*]}; }
  docker rm $(dockers_not_running)
  ```
  Of course, the following simple recipe will do the same, but will produce warnings as the running containers cannot be removed without the force (-f) option:
  ```
  docker rm $(docker ps -aq)
  ```
docker network prune


## docker-compose

Docker compose is a utility which allows several docker instances (aka nodes
or named services) to run as a cooperative unit, in effect by connecting them
on a virtual network.

Follow these [directions](https://docs.docker.com/compose/install/) to install.


