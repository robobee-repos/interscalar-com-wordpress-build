FROM  robobeerun/wordpress:v5.1.1-php7.1-fpm-r.1
LABEL maintainer "Erwin Mueller <erwin.mueller@deventm.com>"

USER root

RUN set -x \
  && /install_wp_theme.sh https://downloads.wordpress.org/theme/parabola.2.3.1.zip '3a134f7d4d8a403700b5a262bf84712ca66fccedbb313858dbc45b9a4e2d884b'

RUN set -x \
  && /install_wp_plugin.sh https://downloads.wordpress.org/plugin/cryout-theme-settings.0.5.9.zip '2cbf7ce4ba024535e1fd980acbf6571f58839c6b57fef40979de4f9bfa0abf24'

ADD rootfs/parabolasettings-httpswwwinterscalarcom.txt /usr/src/wordpress/wp-content/uploads/parabolasettings-httpswwwinterscalarcom.txt

# Finishing up.

USER ${WEB_USER}

WORKDIR ${WEB_ROOT}

ENTRYPOINT ["/docker-entrypoint.sh"]

CMD ["php-fpm"]
