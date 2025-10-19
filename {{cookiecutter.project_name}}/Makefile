.PHONY: all ruff mypy test

all: ruff mypy test

ruff:
    poetry run ruff check src/{{cookiecutter.module_name}} tests --fix

mypy:
    poetry run mypy src/{{cookiecutter.module_name}} tests

test:
    poetry run pytest