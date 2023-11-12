FROM nginx
RUN apt-get update -qq && apt-get -y install apache2-utils
ENV NODE_ROOT /var/www/api-gateway
WORKDIR $NODE_ROOT
RUN mkdir log
COPY app.conf /tmp/app.nginx
COPY certs/ca.crt /etc/nginx/ssl/
COPY my-safe-directory/ca.key /etc/nginx/ssl/
RUN envsubst '$NODE_ROOT' < /tmp/app.nginx > /etc/nginx/conf.d/default.conf
EXPOSE 82
CMD [ "nginx", "-g", "daemon off;" ]