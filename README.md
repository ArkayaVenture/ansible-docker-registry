Ansible-Docker-Registry
===============

This is a simple playbook creating a docker-registry role to setup an independent private docker registry. Role is based upon docker registry [v0.8.0] (https://github.com/docker/docker-registry/tree/0.8.0).

About this document
===============

This role has been tested in an environment with the following components
 * Ubuntu v14.04
 * Ansisble v1.7
 * Docker v1.1.1
 * Python v2.7

Quick start
===============

As this is a completely self contained playbook delivering a working private docker registry using the default configurations,
following steps are required to get running:

 * install docker according to the [following instructions](http://docs.docker.io/installation/#installation)
 * run the playbook: ` ansible-playbook -i hosts site.yml`

That will use the
[official image from the Docker index](https://index.docker.io/_/registry/).


DOCUMENTATION IS "WORK IN PROGRESS"
