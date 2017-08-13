include ../utils/Makefile.help
include ../utils/Makefile.functions

ROOT_DIR:=$(shell realpath root)
NGINX_CONF_DIR:=$(shell realpath nginx-in)
NAME := interscalar-com-wordpress

test: setup ##@targets Starts docker compose.
	export ROOT_DIR="$(ROOT_DIR)" \
	&& export NGINX_CONF_DIR="$(NGINX_CONF_DIR)" \
	&& docker-compose -p $(NAME) -f test.yaml up > log.txt
.PHONY: test

rm:
	export ROOT_DIR="$(ROOT_DIR)" \
	&& export NGINX_CONF_DIR="$(NGINX_CONF_DIR)" \
	&& docker-compose -p $(NAME) -f test.yaml rm

setup:
	mkdir -p $(ROOT_DIR)
	sudo chown 33:33 -R $(ROOT_DIR)
.PHONY: setup
