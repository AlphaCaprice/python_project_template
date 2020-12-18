all: test

#: interpreter version (ex.: 3.8) or use all current available
PYTHON ?= __all_available__

# -- Tests --------------------------------------------------------------------

TEST_COMMAND = tox --recreate
ifeq "$(PYTHON)" "__all_available__"
   TEST_COMMAND += --skip-missing-interpreters
else
   TEST_COMMAND += -e py$(PYTHON)
endif


.PHONY: test
test:
	$(TEST_COMMAND)

# -- Builds -------------------------------------------------------------------

.PHONY: build_dist
build_dist: clean_dist
	pip wheel --wheel-dir dist/ .

# -- Installs -----------------------------------------------------------------

.PHONY: install_dev
install_dev:
	pip install --upgrade --editable .[develop,testing]

.PHONY: _check_dist
_check_dist:
	test -d dist/ || ( \
		echo -e "\n--> [!] Run 'make build_dist' [!]\n" && exit 1 \
	)

.PHONY: install_dist
install_dist: _check_dist
	pip install --no-index --no-cache-dir --find-links=dist/ \
		--upgrade --force-reinstall \
		mkt-andromeda[dist]==$(shell cat dist/__version__)

# -- Cleans ------------------------------------------------------------------

.PHONY: clean_dist
clean_dist:
	-rm -rv dist/
