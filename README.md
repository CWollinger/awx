# Ansible AWX Docker service with docker-compose 

This repo contains docker-compose files for Ansible AWX. It comes with nginx.

AWX Version of current branch: `15.0.1`

## Getting started
Clone the repo to your executing environment.
````shell
git clone https://github.com/CWollinger/awx.git
````

Edit the credentials for AWX and the Postgres database:
[credentials.py](awx-web/credentials.py) 
[environment.sh](awx-web/environment.sh)
[SECRET_KEY](awx-web/SECRET_KEY)

## Start docker containers
First create the services and volumes:
````shell
docker-compose up --no-start 
````

Change redis socket permissions:
````shell
sudo chmod 777 /var/lib/docker/volumes/awx_redis-socket/_data/
````

Copy your nginx config file. Make here changes if you want to redirect SSL/https:
````shell
sudo cp nginx/default.conf /var/lib/docker/volumes/awx_nginx_config/_data/conf.d/default.conf 
````

Copy the AWX config files into the volumes:
````shell
sudo mkdir /var/lib/docker/volumes/awx_awx-config/_data/conf.d
sudo cp awx-web/SECRET_KEY /var/lib/docker/volumes/awx_awx-config/_data/
sudo cp awx-web/environment.sh /var/lib/docker/volumes/awx_awx-config/_data/conf.d/
sudo cp awx-web/credentials.py /var/lib/docker/volumes/awx_awx-config/_data/conf.d/
sudo cp awx-web/nginx.conf /var/lib/docker/volumes/awx_awx-nginx/_data/
````

Start AWX:
````shell
docker-compose up -d
````

Login via http://localhost with user and password stored in [environment.sh](awx-web/environment.sh).

## Related projects
Related projects/used projects:

- [ansible/awx](https://github.com/ansible/awx)
- [redis/redis](https://github.com/redis/redis)
- [nginxinc/docker-nginx](https://github.com/nginxinc/docker-nginx)
- [postgres/postgres](https://github.com/postgres/postgres)
