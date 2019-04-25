FROM  robobeerun/wordpress:v5.1.1-php7.1-fpm-r.2
LABEL maintainer "Erwin Mueller <erwin.mueller@deventm.com>"

USER root

RUN set -x \
  && /install_wp_theme.sh https://downloads.wordpress.org/theme/parabola.2.3.2.1.zip 'ff0a846acfbd8ce9f3311a55aee94fe11068ab8d9d80dc22de7def7ebfc6144f'

RUN set -x \
  && /install_wp_plugin.sh https://downloads.wordpress.org/plugin/cryout-theme-settings.0.5.9.zip '2cbf7ce4ba024535e1fd980acbf6571f58839c6b57fef40979de4f9bfa0abf24'

ADD rootfs/parabolasettings-httpswwwinterscalarcom.txt /usr/src/wordpress/wp-content/uploads/parabolasettings-httpswwwinterscalarcom.txt

# Finishing up.

USER ${WEB_USER}

WORKDIR ${WEB_ROOT}

ENTRYPOINT ["/docker-entrypoint.sh"]

CMD ["php-fpm"]
