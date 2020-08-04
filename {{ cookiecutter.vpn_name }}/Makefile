.PHONY: help
SHELL:=/bin/bash
PROJECT_ROOT=$(shell pwd)

help:  ## This help
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "\033[36m%-20s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST) | sort

generate-keys:  ## Generate the public/private keypair
	sudo tincd -n {{ cookiecutter.vpn_name }} -K4096

start-debugging:  ## Start tincd in debug mode to test
	sudo tincd -n {{ cookiecutter.vpn_name }} -D -d3
