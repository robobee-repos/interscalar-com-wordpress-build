FROM  robobeerun/wordpress:v5.1.1-php7.1-fpm-r.3
LABEL maintainer "Erwin Mueller <erwin.mueller@deventm.com>"

USER root

RUN set -x \
  && /install_wp_theme.sh https://downloads.wordpress.org/theme/parabola.2.3.2.1.zip 'ff0a846acfbd8ce9f3311a55aee94fe11068ab8d9d80dc22de7def7ebfc6144f'

RUN set -x \
  && /install_wp_plugin.sh https://downloads.wordpress.org/plugin/cryout-theme-settings.0.5.10.zip '36991fa9ddec8a9f470fc316e4342d518d1b7415c58dcd358d81d9a6d496d1e9'

ADD rootfs/parabolasettings-httpswwwinterscalarcom.txt /usr/src/wordpress/wp-content/uploads/parabolasettings-httpswwwinterscalarcom.txt

# Finishing up.

USER ${WEB_USER}

WORKDIR ${WEB_ROOT}

ENTRYPOINT ["/docker-entrypoint.sh"]

CMD ["php-fpm"]
