# pebble-sdk-alpine-vagrant
Easy to use pebble SDK using Vagrant and ALPINE LINUX

WARNING:
THIS IMAGE HAS MANY ISSUES DUE TO THE RELIANCE ON PYTHON (read [this article](https://pythonspeed.com/articles/alpine-docker-python/) on why python is a bad idea to use with Alpine)


Setup:
```
git clone https://github.com/jimbob88/pebble-sdk-alpine-vagrant.git
cd pebble-sdk-alpine-vagrant
vagrant plugin install vagrant-faster
vagrant up
vagrant ssh
```
Once logged in via SSH you most likely will need to reinstall the SDK:
```
pebble sdk install https://github.com/aveao/PebbleArchive/raw/master/SDKCores/sdk-core-4.3.tar.bz2
```
