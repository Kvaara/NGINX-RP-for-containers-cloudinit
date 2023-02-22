# NGINX-RP-for-containers-cloudinit
This repository can be used to automatically provision a cloud-based VM, which has Docker-CE already installed, and setup Jenkins, Gitlab, and SonarQube development environments into it using Docker Compose. NGINX sits as a Reverse Proxy in front of them.

This repository contains a Docker Compose manifest file, NGINX config file, and Cloud-Init user-data script file. 

We use Docker Compose as a way to orchestrate Docker containers. It installs all of the required containers (PostgreSQL, Jenkins, GitLab, Sonarqube, and NGINX) and configures them into a default Docker network. Docker has a built-in DNS resolution system, which means that all of those containers that reside in the same Docker network can use their Docker Compose service names as domain names. Docker will convert this domainto an IP address.

NGINX config file is needed to configure the NGINX docker container. This file includes reverse proxy configurations for the following upstream/backend servers: Jenkins, Gitlab, and Sonarqube. This file will also contain TSL/SSL setup so that every client connection to an upstream server will have encryption in it. 

The Cloud-Init user-data script file will be used to automate both the above Docker Compose and NGINX setups for a cloud-based VM during provisioning.
