include ../utils/Makefile.help
include ../utils/Makefile.functions

export NAME := interscalar-com-wordpress

.PHONY: test
test: setup ##@targets Starts docker compose.
	docker-compose -p $(NAME) -f test.yaml up

.PHONY: rm
rm:
	docker-compose -p $(NAME) -f test.yaml rm -f

.PHONY: clean
clean: rm
	sudo rm -rf root

.PHONY: setup
setup:
	for file in html db; do \
	    mkdir -p root/$${file}; \
	    sudo chmod o+rwX root/$${file}; \
	done
	sudo chown 33.33 -R root/html
	sudo chmod u=rwX,g=rwX,o=rX -R root/html

.PHONY: own-files
own-files:
	sudo chown `id -u`.`id -g` -R root

.PHONY: count-php-files
count-php-files:
	docker exec test_$(NAME)_1 find /var/www/html -iname \*.php|wc -l
