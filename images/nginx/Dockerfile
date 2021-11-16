FROM nginx:latest
LABEL maintainer="STAR Z <zx1625437980@gmail.com>"

ENV TZ="Asia\Shanghai"
RUN date -R

WORKDIR /etc/nginx/conf.d

RUN echo "daemon off;" >> /etc/nginx/nginx.conf

CMD [ "nginx" ]

EXPOSE 80 81 443