FROM nginx:1.17.6

# Utilities
RUN apt-get update && apt-get -y install curl

COPY nginx.conf /etc/nginx/nginx.conf
# COPY test_nginx_config.sh /opt/test_nginx_config.sh