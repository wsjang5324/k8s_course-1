FROM ubuntu:18.04
MAINTAINER wsjang <wsjang@gkn.co.kr>

RUN apt-get update
RUN apt-get install -y nginx

VOLUME ["/data", "/etc/nginx/site-enabled", "/var/log/nginx"]

EXPOSE 80

WORKDIR /etc/nginx

CMD ["nginx"]
