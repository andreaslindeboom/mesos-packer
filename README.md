# Packer-Mesos
[WIP] Packer builders to build an AMI/Docker Image with Mesos pre-installed (but not configured)

##How to build
###Preparation
If you intend to create AMIs, copy secrets.json.dist to secrets.json, and enter your AWS credentials.

If you intend to create Docker images, spin up a [Docker Machine](https://www.docker.com/docker-machine).

###Amazon EC2 AMI
packer build -only=amazon-ebs -var-file=secrets.json -var-file=config.json mesos.json

###Docker Image
```
packer build -only=docker -var-file=config.json mesos.json
```

##Troubleshooting
###The Docker builder hangs at shell script provisioning (OS X)
Boot2Docker and/or Docker Machine are likely unable to reach the directory set as TMPDIR seeing as it is not mounted by default.

A possible workaround would be to set the TMPDIR environment variable to somewhere in your /Users directory:
```
mkdir /Users/username/tmp && TMPDIR=/Users/username/tmp
```
