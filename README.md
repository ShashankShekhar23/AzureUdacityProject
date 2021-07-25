# AzureUdacityProject
This is a repo for Udacity Azure DevOps Project


[![Python application test with Github Actions](https://github.com/ShashankShekhar23/AzureUdacityProject/actions/workflows/pythonapp.yml/badge.svg)](https://github.com/ShashankShekhar23/AzureUdacityProject/actions/workflows/pythonapp.yml)

Github Actions
![image](https://user-images.githubusercontent.com/86247520/126873822-4603fcf9-a08c-4946-b102-5e810c450f47.png)


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




