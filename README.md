


docker-compose create 

sudo chmod 777 /var/lib/docker/volumes/repo_redis-socket/_data/


sudo cp nginx/default.conf /var/lib/docker/volumes/repo_nginx_config/_data/conf.d/default.conf 




# AWX

sudo mkdir /var/lib/docker/volumes/repo_awx-config/_data/conf.d

sudo cp awx-web/SECRET_KEY /var/lib/docker/volumes/repo_awx-config/_data/
sudo cp awx-web/environment.sh /var/lib/docker/volumes/repo_awx-config/_data/conf.d/
sudo cp awx-web/credentials.py /var/lib/docker/volumes/repo_awx-config/_data/conf.d/


sudo cp awx-web/nginx.conf /var/lib/docker/volumes/repo_awx-nginx/_data/

