# BP for Coding in a cloud environment

## General

* Create virtual environment for each project
    ```
    virtualenv ~/.venv     
    source ~/.venv/bin/activate    
    which python
    ```
* Make sure that your bashrc file is accessible directly from different terminal windows. Access your bashrc file
    ```
    vim ~/.bashrc
    ```
    after that you can add a source command to the file
    ```bash
    source ~/.venv/bin/activate
    ```
* Add standard files that you are always going to use
    ```bash
    touch Makefile
    touch requirements.txt
    ```

## Makefile

In a maekfile you can specify a lot of standard operations that have to be performed when creating a project. This is an example of a makefile
```bash
install:
	pip install --upgrade pip &&\
		pip install -r requirements.txt

test:
	python -m pytest -vv test_hello.py

format:
	black *.py

lint:
	pylint --disable=R,C hello.py

all: install format lint test
	@echo "All tasks completed successfully."
```