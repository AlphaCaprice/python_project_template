.PHONY: all ruff mypy test

all: ruff mypy test

ruff:
	poetry run ruff check src/{{cookiecutter.module_name}} tests --fix

mypy:
	poetry run mypy src/{{cookiecutter.module_name}}

test:
	poetry run pytest --cov=src/{{cookiecutter.module_name}} --cov-report=term-missing --cov-fail-under=95