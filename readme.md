# Setup project folders
`mkdir djrect` in your location you prefer

`cd djreact` change directory to djreact

`mkdir frontend backend` creates two folders

# Create a virtual Environment 
`cd backend` change dir to backend

`virtualenv env` creates a virtual environment

## Activate the virtual Environment
- `cd env`, and run `Scripts\Activate` to activate the virtual environment `Scripts\Deactivate` to deactivate the virtual environment.
- Install django, run `pip install django`
- Install Django Rest Framework `pip install djangorestframework`

# Setting up Basic Django Project
- In `djreact\backend` run `django-admin startproject djreact`
## Setting up automation panda for Django vscode
- got to https://automationpanda.com/2018/02/08/django-projects-in-visual-studio-code/ and install the following 


- `pip install pep8`
- `pip install autopep8`
- `pip install pylint`

or you can also combine all of them at once like this 
`pip install pep8 autopep8 pylint`

- And then add the following settings:
    - in .vscode/ run `touch settings.json`
    - add 
    ```json 
    {
    "team.showWelcomeMessage": false,
    "editor.formatOnSave": true,
    "python.linting.pep8Enabled": true,
    "python.linting.pylintPath": "/path/to/pylint",
    "python.linting.pylintArgs": [
        "--load-plugins",
        "pylint_django"
    ],
    "python.linting.pylintEnabled": true }
    ``` 
in your settings.json file
