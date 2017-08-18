########################################################################
#
# Customizing docker image broadtech/alpine-php7-fpm
# https://github.com/sgeorge/dockerfiles/tree/master/alpine/php7-fpm
#
########################################################################

# Base Image
FROM broadtech/alpine-php7-fpm

# Do package update upgrade only during build
RUN rm -f /etc/docker-entrypoint.d/10_update_upgrade

# Install reruired PHP7 modules and dependencies
RUN apk --no-cache add busybox \
                       php7-bz2 \
                       php7-ctype \
                       php7-gd \
                       php7-json \
                       php7-mcrypt \
                       php7-mysqli \
                       php7-zip \
                       php7-zlib

# PHP FPM Pool configuration
COPY conf/www.conf /etc/php7/php-fpm.d/

# Open port for FPM access
Expose 9000

# Start the container
ENTRYPOINT ["/usr/sbin/php-fpm7"]

##################---END---###########################################
