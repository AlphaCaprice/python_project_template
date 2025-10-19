.PHONY: all ruff mypy test

all: ruff mypy test

ruff:
	poetry run ruff check src/fastapi_sandbox tests --fix

mypy:
	poetry run mypy src/fastapi_sandbox tests

test:
	poetry run pytest