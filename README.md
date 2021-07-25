# AzureUdacityProject
This is a repo for Udacity Azure DevOps Project


[![Python application test with Github Actions](https://github.com/ShashankShekhar23/AzureUdacityProject/actions/workflows/pythonapp.yml/badge.svg)](https://github.com/ShashankShekhar23/AzureUdacityProject/actions/workflows/pythonapp.yml)

# Steps to run this project #
* Create a Github Repo(if not created)
* Launch Azure Cloud Shell via Azure Portal
* Create ssh-keys in Azure Cloud Shell
* Upload ssh-keys to Github
* Clone Github repo through Azure Cloud Shell
* Create scaffolding for project (if not created)
  * Makefile
  ```
  install:
	pip install --upgrade pip &&\
		pip install -r requirements.txt
  test:
	python -m pytest -vv test_hello.py
  
  lint:
	pylint --disable=R,C hello.py
  
  all: install lint test
  ```
  * requirements.txt
  ```
  pylint
  pytest
  ```
  * Create initial `hello.py` and `test_hello.py`
  
  hello.py
  ```
  def toyou(x):
    return "hi %s" % x
  def add(x):
    return x + 1
  def subtract(x):
    return x - 1
  ```
  
  test_hello.py
  ```
  from hello import toyou, add, subtract
  
  def setup_function(function):
    print("Running Setup: %s" % function.__name__)
    function.x = 10
    
  def teardown_function(function):
    print("Running Teardown: %s" % function.__name__)
    del function.x
    
  ### Run to see failed test
  #def test_hello_add():
  #    assert add(test_hello_add.x) == 12
   
  def test_hello_subtract():
  assert subtract(test_hello_subtract.x) == 9
  ```

* Create a python virtual environment and source it if not created
```
python3 -m venv ~/.<your-repo-name>
source ~/.<your-repo-name>/bin/activate
```
* Run `make all` which will install, lint and test code.
![MakeAllCommand](https://user-images.githubusercontent.com/86247520/126906041-c0866198-e36e-421d-b06c-dffe1f2075c0.PNG)

* Go to **Actions** and click **setup a workflow yourself**
* Rename `main.yml` to `pythonapp.yml`
```
name: Python application test with Github Actions

on: [push]

jobs:
build:

runs-on: ubuntu-latest

steps:
- uses: actions/checkout@v2
- name: Set up Python 3.5
uses: actions/setup-python@v1
with:
python-version: 3.5
- name: Install dependencies
run: |
make install
- name: Lint with pylint
run: |
make lint
- name: Test with pytest
run: |
make test
```
* Commit `pythonapp.yml`
* Go back to **Actions** and click on the commit that was just made
![image](https://user-images.githubusercontent.com/86247520/126873822-4603fcf9-a08c-4946-b102-5e810c450f47.png)
* Create **status badge** to check the status of the project i.e. passing or failed
[![Python application test with Github Actions](https://github.com/ShashankShekhar23/AzureUdacityProject/actions/workflows/pythonapp.yml/badge.svg)](https://github.com/ShashankShekhar23/AzureUdacityProject/actions/workflows/pythonapp.yml)



