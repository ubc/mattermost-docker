FROM alpine:3.5

RUN apk add --update --no-cache nginx && rm -rf /var/cache/apk/*

RUN rm /etc/nginx/conf.d/default.conf

COPY mattermost /etc/nginx/conf.d/
COPY mattermost-ssl /etc/nginx/conf.d/
ADD docker-entry.sh /

RUN chmod +x /docker-entry.sh

# You can see the logs using `docker-compose logs web`.
RUN ln -sf /dev/stdout /var/log/nginx/access.log
RUN ln -sf /dev/stderr /var/log/nginx/error.log

# Define working directory.
WORKDIR /etc/nginx

ENTRYPOINT /docker-entry.sh

EXPOSE 80 443
