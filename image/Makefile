REPOSITORY := erwin82
NAME := interscalar-com-wordpress
VERSION ?= v5.1.1-php7.1-fpm-r.3

.PHONY: build
build: _build ##@targets Builds the docker image.

.PHONY: clean
clean: _clean ##@targets Removes the local docker image.

.PHONY: deploy
deploy: _deploy ##@targets Deploys the docker image to the repository.

define checkfile_for_install
   cd /tmp && \
   wget -q $2 && \
   name=$$(basename $2) && \
   sha=$$(sha256sum $${name}|cut -f1 -d' ') && \
   rm $${name} && \
   echo "RUN set -x \\" && \
   echo "  && /install_wp_$1.sh $2 '$${sha}'"
endef

check-plugins:
	@$(call checkfile_for_install,plugin,https://downloads.wordpress.org/plugin/cryout-theme-settings.0.5.10.zip)

check-themes:
	@$(call checkfile_for_install,theme,https://downloads.wordpress.org/theme/parabola.2.3.2.1.zip)

include ../utils/Makefile.help
include ../utils/Makefile.functions
include ../utils/Makefile.image
