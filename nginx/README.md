# cog-containers/nginx
See repo: https://github.com/nginx-proxy/nginx-proxy

I've used the code in this repo modify the nginxy-proxy code to allow an API key to be passed. I'm using nginx-proxy version 1.4.0.

Inside the Terraform script I use the following to build the nginx container
docker run --detach --name nginx-proxy --publish 80:80 --publish 443:443 --volume certs:/etc/nginx/certs --volume vhost:/etc/nginx/vhost.d --volume html:/usr/share/nginx/html --volume /var/run/docker.sock:/tmp/docker.sock:ro nginxproxy/nginx-proxy:1.4.0
cd /home/ubuntu/data/cog/nginx
docker cp nginx.tmpl nginx-proxy:/app/nginx.tmpl
docker cp conf.d/proxy_timeout.conf nginx-proxy:/etc/nginx/conf.d/proxy_timeout.conf
docker cp nginx.conf nginx-proxy:/etc/nginx/nginx.conf
