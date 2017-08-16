FROM  erwin82/wordpress:v4.8.1-r2-1
LABEL maintainer "Erwin Mueller <erwin.mueller@deventm.com>"

USER root

RUN set -x \
  && install_wp_theme.sh https://downloads.wordpress.org/theme/parabola.2.2.1.zip '1f82a70e34a403f0d9a2597fcfaa9b1dd2e99679e546300263738d6ada61b923'

RUN set -x \
  && install_wp_plugin.sh https://downloads.wordpress.org/plugin/cryout-theme-settings.0.5.8.zip '40e97f9725cbc12ba130dbbba2f9a60dcddf47cec53623a0f133b3110fe31617'

ADD rootfs/parabolasettings-httpswwwinterscalarcom.txt /usr/src/wordpress/wp-content/uploads/parabolasettings-httpswwwinterscalarcom.txt

# Finishing up.

USER ${WEB_USER}

WORKDIR ${WEB_ROOT}

ENTRYPOINT ["docker-entrypoint.sh"]

CMD ["php-fpm"]
