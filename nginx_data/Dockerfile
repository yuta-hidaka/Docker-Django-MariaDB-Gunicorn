FROM nginx:latest
ARG APP_NAME
ARG APP_PORT
ARG LISTEN_PORT

RUN rm /etc/nginx/conf.d/default.conf
RUN touch /etc/nginx/conf.d/nginx.conf
RUN echo "                                                              \
            upstream $APP_NAME {                                        \
                server python-django:$APP_PORT;                         \
            }                                                           \
            server {                                                    \
                listen $LISTEN_PORT;                                    \
                charset utf-8;                                          \
                location / {                                            \
                    proxy_pass http://$APP_NAME;                        \
                    proxy_redirect off;                                 \
                }                                                       \
                location /static/ {                                     \
                    alias /static/;                                     \
                }                                                       \
                location /media/ {                                      \
                    alias /media/;                                      \
                }                                                       \
            }                                                           \
            server_tokens off;                                          \
        "                                                               \ 
> /etc/nginx/conf.d/nginx.conf
