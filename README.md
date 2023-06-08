# Deploying Django with Docker Compose

Preparing and deploying a Django project to an AWS EC2 instance using Docker Compose.



## Deploying AWS - EC2
After configuring EC2 instance (with ssh key eventually to connect from local to ec2 virtual machine) :
- connect to instance : `ssh ec2-user@{public_DNS}`
- install git : `sudo yum install git -y`
- install docker : `sudo amazon-linux-extras install docker -y`
- enable and start docker service when machine boot/reboot : `sudo systemctl enable docker.service`
- [explicitly] start docker service : `sudo systemctl start docker.service`
- give permission to user to run docker containers : `sudo usermod -aG docker ec2-user`
- install docker-compose (see documentation) :
```
DOCKER_CONFIG=${DOCKER_CONFIG:-$HOME/.docker}
mkdir -p $DOCKER_CONFIG/cli-plugins
curl -SL https://github.com/docker/compose/releases/download/v2.18.1/docker-compose-linux-x86_64 -o $DOCKER_CONFIG/cli-plugins/docker-compose
```
- make executable : `chmod +x $DOCKER_CONFIG/cli-plugins/docker-compose`
- then exit and log in again

- If public repo, generate a new ssh key (inside the ec2 machine) to use for deploying with Github Deploy key
`ssh-keygen -t ed25519 -b 4096`