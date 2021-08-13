FROM base:21.08.1
MAINTAINER Ra Daesung "daesungra@gmail.com"

### Install and Update nginx package ###
RUN apt-get update && apt-get install -y nginx

### Place reverse-proxy config file to instance ###
COPY ./custom-reverse.conf /etc/nginx/sites-available/

### Set nginx configuration ###
RUN unlink /etc/nginx/sites-enabled/default
RUN ln -s /etc/nginx/sites-available/custom-reverse.conf /etc/nginx/sites-enabled/custom-reverse.conf

### Test new config ###
RUN nginx -t

### Start nginx by background process ###
CMD ["nginx", "-g", "daemon off;"]

