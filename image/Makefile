REPOSITORY := erwin82
NAME := interscalar-com-wordpress
VERSION ?= v5-r1-1

build: _build ##@targets Builds the docker image.

clean: _clean ##@targets Removes the local docker image.

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
	@$(call checkfile_for_install,plugin,https://downloads.wordpress.org/plugin/cryout-theme-settings.0.5.9.zip)

check-themes:
	@$(call checkfile_for_install,theme,https://downloads.wordpress.org/theme/parabola.2.2.2.zip)

include ../utils/Makefile.help
include ../utils/Makefile.functions
include ../utils/Makefile.image

.PHONY +: build clean deploy
