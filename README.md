# Brandx Docker
Docker setup for Brandx

## Getting Started

* Add to your hosts file
```
sudo nano /etc/hosts
```
and append on the file
```
127.0.0.1   brandx.dev.com
```

* Pull jwilder's nginx proxy docker image
```
docker pull jwilder/nginx-proxy:latest
```

* Run the proxy image
```
docker run -d -p 80:80 -v /var/run/docker.sock:/tmp/docker.sock:ro --net=local_network_bridge --name=jwilder_nginx jwilder/nginx-proxy
```

* Spin the containers
This will up the apache, php, mysql and redis containers
```
docker-compose up -d
```
```
docker-compose down
```
if you want to take down the containers
```
docker-compose exec [web|cache|db] bash
```
if you want to get inside of the container

### Note
There should no instance running on your port 80
kill apache2 / apachectl instance if needed.

## Authors
* **John Gerwin De las Alas** - *Docker brandx* - [iamgerwin](https://github.com/iamgerwin)
