#####################################################################
#
# Customizing docker image broadtech/alpine-nginx
# https://github.com/sgeorge/dockerfiles/tree/master/alpine/nginx
#
######################################################################

# Base Image
FROM broadtech/alpine-nginx

# Configure Nginx to deny access to dotFiles
#COPY denydotfiles.conf /etc/nginx/conf.d/

# Do package update upgrade only during build
RUN rm -f /etc/docker-entrypoint.d/10_update_upgrade

RUN apk update && apk --no-cache upgrade

# Point Nginx to PHP-FPM
COPY conf/php7-fpm.conf /etc/nginx/conf.d/

# Test file to show PHP information
COPY www/index.php /var/www/localhost/htdocs/
RUN chmod -R +x /var/www/localhost/htdocs/

# Open port to access Nginx
EXPOSE 80

# Start the container
ENTRYPOINT ["/usr/sbin/run_parts_entrypoint.sh"]

# -------------------------END----------------------------------------#
