.PHONY: help
SHELL:=/bin/bash
PROJECT_ROOT=$(shell pwd)

help:  ## This help
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "\033[36m%-20s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST) | sort

install-tinc:  ## install tinc package
	sudo apt install tinc -y

generate-keys:  ## Generate the public/private keypair
	sudo tincd -n {{ cookiecutter.vpn_name }} -K4096

start-debugging:  ## Start tincd in debug mode to test
	sudo tincd -n {{ cookiecutter.vpn_name }} -D -d3

copy-to-host:  ## copies the configuration to the host tinc directory
	sudo mkdir -p /etc/tinc/{{ cookiecutter.vpn_name }}
	sudo cp -farv host/* /etc/tinc/{{ cookiecutter.vpn_name }}
	sudo cp -farv nets.boot /etc/tinc

copy-to-guest:  ## copies the configuration to the guest tinc directory
	sudo mkdir -p /etc/tinc/{{ cookiecutter.vpn_name }}
	sudo cp -farv guest/* /etc/tinc/{{ cookiecutter.vpn_name }}
	sudo cp -farv nets.boot /etc/tinc
