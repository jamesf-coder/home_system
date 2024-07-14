# home_system
Infrastructure as Code (IaC) to setup my home system

## Prerequisites

1. Docker installed on host server
2. Docker can be used as non-root user
3. Ansible setup on PC:
    1. `$ ansible-galaxy collection install community.general`
    2. `$ ansible-galaxy collection install community.docker`

## Setup

Here are the steps to setup the server using Ansible:

1. Establish ssh key-based authentication between your PC and the server.
    1. `$ ssh-keygen -t rsa -b 4096`
    2. `$ ssh-copy-id your_username@myserver`
2. Clone this repository to your PC..
3. Run the following from inside the cloned repository.

## Environment variables

The following env vars are required to be specified:

* `SERVER_PUBLIC_IP` - Public IP of the server to be setup.
* `CLOUDFLARE_API_TOKEN` - Cloudflare API token for DNS updates
* `FTP_MOUNT` - Mount point for FTP server

## Running ansible

Example command to run ansible:

```bash
ansible-playbook -i inventory.yml --ask-become-pass -e SERVER_PUBLIC_IP=A.B.C.D -e CLOUDFLARE_API_TOKEN=YOURCLOUDFLAREAPIKEY -e FTP_MOUNT=/ftp/mount/point tasks/main.yml
```