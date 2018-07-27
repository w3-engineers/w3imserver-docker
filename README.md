# Docker based W3IM server deployment

##### This document intended for debian or ubuntu system.

### We are assuming you have installed (latest version)
- Docker
- Docker composer 
- Postgres DB (It can be on different host/machine/any cloud services)
- Nginx 
- [Nginx Cerbot (for SSL)](https://www.digitalocean.com/community/tutorials/how-to-set-up-let-s-encrypt-with-nginx-server-blocks-on-ubuntu-16-04)

After ensuring everything above are ready, do the followings from git cloned directory.
- Modify `docker-compose.yml` for postgres details
- Run from bash

    `mkdir -p ./volumes/app/mattermost/{data,logs,config} && \
     sudo chown -R 2000:2000 ./volumes/app/mattermost/ && \
     docker-compose up -d`

- If everything is okay, you'll find a docker container running for mattermost by typing `docker ps` on bash shell.
- Make a nginx virtual host config for your IM Server by modifying `im.host.conf` and copy it to `/etc/nginx/sites-enabled/` directory or, any directory where nginx can read config from.
- Run `sudo nginx -t` to check if any error. Fix if found reload if it's ok using `sudo service nginx reload`
- You can now access your IM URL from any browser and can set, a default **System admin** user for your IM.
- Generate SSL certificate for your domain using `sudo certbot --nginx -d im.host.com`
- Follow console instruction and procced. 

Good job, You're done.

N.B: W3IM is a inspiration of https://mattermost.com/. So, please visit, their [Documentation](https://docs.mattermost.com/) for further modification, customization. 

Also, you can reach us for anything by going https://w3engineers.com/contact/ url.