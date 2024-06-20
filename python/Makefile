.PHONY: help

help:
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'

ROOT_DIR:=$(shell dirname $(realpath $(firstword $(MAKEFILE_LIST))))
ALLOWED_DIRS := <space separated directories>

lint:  ## code check code with pylint
	@poetry run python3 -m pylint $(shell find $(addprefix $(ROOT_DIR)/,$(ALLOWED_DIRS)) -type f -name "*.py")

format:  ## code reformat code with isort and black
	@poetry run python3 -m ruff format --preview $(ROOT_DIR)
	@poetry run python3 -m ruff check --show-fixes --fix --preview $(ROOT_DIR)
