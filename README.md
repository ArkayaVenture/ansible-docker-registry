# Ansible-Docker-Registry
[![Build Status](https://travis-ci.org/soumentrivedi/ansible-docker-registry.svg)](https://travis-ci.org/soumentrivedi/ansible-docker-registry)
## Description
This is a simple playbook creating a docker-registry role to setup an independent private docker registry and configuring an upstart script on the docker host for starting up docker registry at boot time. 
Role is based upon docker registry [v0.8.0] (https://github.com/docker/docker-registry/tree/0.8.0). 

## Dependencies
This role has been tested in an environment with the following components
 * Ubuntu v12.04 or above
 * Ansisble v1.7
 * Docker v1.1.1
 * Python v2.7

## Note
For the upstart configuration to work, the DOCKER_OPTS in /etc/default/docker should contain "-r=false"

`DOCKER_OPTS="-r=false ..."`

## Quick start
As this is a completely self contained playbook delivering a working private docker registry using the default configurations,
following steps are required to get running:
*  install docker according to the [following instructions](http://docs.docker.io/installation/#installation)
*  run the playbook: ` ansible-playbook -i hosts site.yml`
  
That will use the
[official image from the Docker index](https://index.docker.io/_/registry/).

## Known Issues
There are currently no reported issues on this version of code. 

## Under the bonnet
### Key components
#### Docker Registry Upstart Configuration
[docker-registry.conf.j2](roles/docker-registry/templates/docker-registry.conf.j2) is the templated Upstart configuration

#### Dockerfile
[Dockerfile.j2](roles/docker-registry/templates/Dockerfile.j2) is the templated Dockerfile that is replaced during the ansible runtime to build a docker container image called docker-registry/master. The playbook performs check using the docker_image tag to build an image only if there are changes in the code.

#### Tasks
Ansible tasks configuration are written in [main.yml](roles/docker-registry/tasks/main.yml)


## Ideas/Features in development
Following are few ideas/features that will be developed in due-course of time
 * Adding apache and nginx configuration samples to perform url re-write on the docker host
 * Adding support for RHEL/CentOS

"WORK IN PROGRESS"
===============
