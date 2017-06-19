FROM  erwin82/wordpress-base:4.8.0-r4
LABEL maintainer "Erwin Mueller <erwin.mueller@deventm.com>"

USER root

RUN set -x \
  && install_wp_theme.sh https://downloads.wordpress.org/theme/parabola.2.2.0.zip '743c773044aa235a66c1d376b11f91c63e2895fcd9a8e28907e9aa12983a75a1'

RUN set -x \
  && install_wp_plugin.sh https://downloads.wordpress.org/plugin/cryout-theme-settings.0.5.7.zip 'e66ce7456d8a96ccb6072a5a1c32fbde26e3986da496486b80c178d7874132a2'

# Colors http://paletton.com/#uid=53L0Z0kfmwe00++3yM+rishXxmC

ADD rootfs/parabolasettings-httpsinterscalarcom.txt /usr/src/wordpress/wp-content/uploads/parabolasettings-httpsinterscalarcom.txt

# Finishing up.

USER www-data

WORKDIR $WEB_ROOT

ENTRYPOINT ["docker-entrypoint.sh"]

CMD ["php-fpm"]
