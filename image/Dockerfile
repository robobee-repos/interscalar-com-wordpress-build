FROM  robobeerun/wordpress:v4.9.5-php5.6-fpm-r2
LABEL maintainer "Erwin Mueller <erwin.mueller@deventm.com>"

USER root

RUN set -x \
  && /install_wp_theme.sh https://downloads.wordpress.org/theme/parabola.2.2.2.zip 'e69b0a9e7eafb80043dfe9fe0afd3645a021376bb2d12264cfdb154b9d48b5ec'
RUN set -x \
  && /install_wp_plugin.sh https://downloads.wordpress.org/plugin/cryout-theme-settings.0.5.9.zip '2cbf7ce4ba024535e1fd980acbf6571f58839c6b57fef40979de4f9bfa0abf24'

ADD rootfs/parabolasettings-httpswwwinterscalarcom.txt /usr/src/wordpress/wp-content/uploads/parabolasettings-httpswwwinterscalarcom.txt

# Finishing up.

USER ${WEB_USER}

WORKDIR ${WEB_ROOT}

ENTRYPOINT ["/docker-entrypoint.sh"]

CMD ["php-fpm"]
