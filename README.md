# Packer-Mesos
[WIP] Packer builders to build an AMI/Docker Image with Mesos pre-installed (but not configured)

##Troubleshooting
###The Docker builder hangs at shell script provisioning (OS X)
Boot2Docker and/or Docker Machine are likely unable to reach the directory set as TMPDIR seeing as it is not mounted by default.

A possible workaround would be to set the TMPDIR environment variable to somewhere in your /Users directory:
```
mkdir /Users/username/tmp && TMPDIR=/Users/username/tmp
```
