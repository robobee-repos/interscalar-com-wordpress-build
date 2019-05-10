FROM  robobeerun/wordpress:v5.2.0-php7.1-fpm-r.1
LABEL maintainer "Erwin Mueller <erwin.mueller@deventm.com>"

USER root

# Install plugins.

RUN set -x \
  && /install_all_wp_plugins.sh

# Install themes.

RUN set -x \
  && /install_all_wp_themes.sh

# Adds parabola settings.

ADD rootfs/parabolasettings-httpswwwinterscalarcom.txt /usr/src/wordpress/wp-content/uploads/parabolasettings-httpswwwinterscalarcom.txt

# Finishing up.

USER ${WEB_USER}

WORKDIR ${WEB_ROOT}

ENTRYPOINT ["/docker-entrypoint.sh"]

CMD ["php-fpm"]
