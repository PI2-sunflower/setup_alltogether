# Install

## Git

Install git
```bash
sudo apt-get update && sudo apt-get install git
```

## Docker and docker-compose

This script assumes you are using Ubuntu 16.04, if you are using a different version take a look at:

* For [Docker](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04)
* For [docker-compose](https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-16-04)

### Install Docker

Making sure you have curl installed
```bash
sudo apt-get update && sudo apt-get install curl -y
```

Getting docker GPG key
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Adding docker repository
```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

Installing docker
```bash
sudo apt-get update && sudo apt-get install -y docker-ce
```

### Install docker-compose

Downloading docker compose
```bash
sudo curl -L https://github.com/docker/compose/releases/download/1.18.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```

Giving it execution permission
```bash
sudo chmod +x /usr/local/bin/docker-compose
```

# Build

Clone repositories
```bash
git clone --recurse-submodules https://github.com/PI2-sunflower/sunflower_alltogether.git
```

## Build process

The build process is the slowest part, but it **only need to be done once**.

First access the directory:
```bash
cd sunflower_alltogether
```

Then call docker-compose to do the build. The first build is the slowest of all because it will download and install everything, so be patient.

```bash
sudo docker-compose build
```

Remembering, you don't need to run the build every time you are going to use the system. The build is done **only one time** and then you kept just running it.

## Running

After the build is done now you just need run it.

```bash
sudo docker-compose up
```

With the process running you just need to open the browser at one of the following:
* 127.0.0.1
* 127.0.0.1:80
* localhost
* localhost:80
* 0.0.0.0
* 0.0.0.0:80

## Exiting

After using it to exit you just need to CTRL+C on terminal to terminate the docker-compose process and then execute:
```bash
sudo docker-compose down
```
