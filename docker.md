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


## docker-compose
