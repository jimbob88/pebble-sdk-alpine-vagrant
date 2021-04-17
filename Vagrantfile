# -*- mode: ruby -*-
# vi: set ft=ruby :
$provisioningscript = <<SCRIPT
    apk update
    apk upgrade
    apk add python2-dev sdl-dev libfdt pixman-dev musl-dev gcc g++ npm
    python -m ensurepip
    pip install --no-cache --upgrade pip setuptools
    pip install virtualenv
    mkdir /home/vagrant/pebble-dev
    cd /home/vagrant/pebble-dev
    wget --progress=bar:force 'https://developer.rebble.io/s3.amazonaws.com/assets.getpebble.com/pebble-tool/pebble-sdk-4.5-linux64.tar.bz2'
    tar -jxf pebble-sdk-4.5-linux64.tar.bz2
    cd /home/vagrant/pebble-dev/pebble-sdk-4.5-linux64
    virtualenv .env
    source .env/bin/activate
    pip install -r requirements.txt
    deactivate
    cd /home/vagrant
    wget --progress=bar:force 'https://raw.githubusercontent.com/jimbob88/pebble-sdk-alpine-vagrant/main/.profile'
    source /home/vagrant/pebble-dev/pebble-sdk-4.5-linux64/.env/bin/activate
    export PATH=/home/vagrant/pebble-dev/pebble-sdk-4.5-linux64/bin:$PATH
    pebble sdk install https://github.com/aveao/PebbleArchive/raw/master/SDKCores/sdk-core-4.3.tar.bz2
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox"
  config.vm.box = "generic/alpine313"

  VAGRANT_COMMAND = ARGV[0]
  if VAGRANT_COMMAND == "ssh"
    config.ssh.username = 'vagrant'
  end

  config.vm.provision "shell", run: "once" do |s|
    s.inline= $provisioningscript
  end
end

