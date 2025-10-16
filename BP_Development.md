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

In the makefile there is a mention of the install section. This allows us to have a single file ```requirements.txt``` that contains all the packages and dependencies that are necessary to run the project. If I now run

```bash
make install
```
I can install whatever is contained in my ```requirements.txt```.

Seemingly if I have a piece of code in my file named ```hello.py```

```python
def more_hello()
    return 'hi'
```
and I want to test it I can run the test easily by writing it of course
```python
from hello import more_hello

def test_more_hello():
    assert more_hello()=='hi'
```

and just leverage what i did in the makefile, rather than writing the command test everytime

```bash
make test
```

One more note concerning how we write the ```requirements.txt``` file. It might be useful to run

```bash
pip freeze | less
```
to take a look at the specific version of the packages that we install, so that we can force installation of individual release of packages
