# Ansible-Docker-Registry
## Description
This is a simple playbook creating a docker-registry role to setup an independent private docker registry and configuring an upstart script on the docker host for starting up docker registry at boot time. 
Role is based upon docker registry [v0.8.0] (https://github.com/docker/docker-registry/tree/0.8.0). 

## Dependencies
This role has been tested in an environment with the following components
 * Ubuntu v14.04
 * Ansisble v1.7
 * Docker v1.1.1
 * Python v2.7

## Quick start
As this is a completely self contained playbook delivering a working private docker registry using the default configurations,
following steps are required to get running:
*  install docker according to the [following instructions](http://docs.docker.io/installation/#installation)
*  run the playbook: ` ansible-playbook -i hosts site.yml`
  
That will use the
[official image from the Docker index](https://index.docker.io/_/registry/).

## Known Issues
There are few known issues that I have observed while performing the tests. I intend to keep the contents and documentation in this repository as up to date as possible. If you find any issue(s) with this playbook, please do let me know. As this is my first attempt at contribution to GitHub, I am hoping to get comment and feedback on the work that I have done here.

 * Upstart configuration needs to be optimised to allow single thread of docker container is started. With the current configuration 8 docker registry docker containers gets started and are tied to random ports.
 * Everytime the service is restarted, the storage is not persisted. This is easily achievable using a persistent storage mechanism in Docker containers. 

"WORK IN PROGRESS"
===============
