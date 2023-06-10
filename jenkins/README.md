# Jenkins Docker Compose

This repository contains a Docker Compose configuration for deploying Jenkins using Docker.
It does container docker CLI inside it along with frequently used Blue Ocean plugins and features. 

# Prerequisites

Minimum hardware requirements:

* Docker

* 256 MB of RAM

* 1 GB of drive space (although 10 GB is a recommended minimum if running Jenkins as a Docker container)

Recommended hardware configuration for a small team:

* 4 GB+ of RAM

* 50 GB+ of drive space

# Downloading and running Jenkins in Docker

There are several Docker images of Jenkins available.

The recommended Docker image to use is the Official `jenkins/jenkins image` (from the Docker Hub repository). This image contains the current Long-Term Support (LTS) release of Jenkins (which is production-ready).

## On macOS and Linux

1. Open up a terminal window.
2. Navigate to `jenkins` directory in repo.
3. Run docker compose command 
```bash
    docker compose up -d
```
# Post-installation setup wizard

After downloading, installing and running Jenkins using one of the procedures above (except for installation with Jenkins Operator), the post-installation setup wizard begins.

This setup wizard takes you through a few quick "one-off" steps to unlock Jenkins, customize it with plugins and create the first administrator user through which you can continue accessing Jenkins.

## Unlocking Jenkins
When you first access a new Jenkins instance, you are asked to unlock it using an automatically-generated password.

1. Browse to http://localhost:8080 (or whichever port you configured for Jenkins when installing it) and wait until the Unlock Jenkins page appears.

![Unlocking](images/setup-jenkins-01-unlock-jenkins-page.jpg)

2. Using docker get the automatically-generated alphanumeric password.
```bash
    docker compose exec ${CONTAINER_NAME} cat /var/jenkins_home/secrets/initialAdminPassword
```
3. On the Unlock Jenkins page, paste this password into the Administrator password field and click Continue.
> Note:
The Jenkins console log indicates the location (in the Jenkins home directory) where this password can also be obtained. This password must be entered in the setup wizard on new Jenkins installations before you can access Jenkins’s main UI. This password also serves as the default administrator account’s password (with username "admin") if you happen to skip the subsequent user-creation step in the setup wizard.


