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


# Setting React Project 
- In djreact\frontend, run `npx create-react-app gui`, make sure you have the latest node js install in your machine.

## Running Back and Front End Servers
- In djreact\frontend, `cd gui\` and run `npm start`, here you should see react app running on  http://localhost:3000/
- In djreact\backend\djreact 
    - Run `python manage.py migrate` to apply migrations
    - Run `python manage.py runserver` here you should see python site runing on http://127.0.0.1:8000/  or  http://localhost:8000/

## Creating Python App
- In djreact\backend\djreact, create python app, run `python manage.py startapp article`
- Add `article` and `restframework` to the djreact\backend\djreact\settings.py 
    ```py
    INSTALLED_APPS = [
        ...
        'rest_framework',
        'article',
        ...
    ]

    REST_FRAMEWORK = {
        # Use Django's standard `django.contrib.auth` permissions,
        # or allow read-only access for unauthenticated users.
        'DEFAULT_PERMISSION_CLASSES': [
            'rest_framework.permissions.DjangoModelPermissionsOrAnonReadOnly'
        ]
    }
    ```
    and in ulrs.py in djreact\backend\djreact\ulrs.py

    ```py
    urlpatterns = [
        ...
        path('api-auth/', include('rest_framework.urls'))
        ...
    ]
    ```

### Creating Django Models 

- add to djreact\backend\djreact\article\models.py
    ```py
    class Article(models.Model):
    title = models.CharField(max_length=120)
    content = models.TextField()

    def __str__(self):
        return self.title
    ```
- In djreact\backend\djreact run `python manage.py makemigrations` followed by `python manage.py migrate`

### Register the Article in Django Admin,

- In djreact\backend\djreact\article\admin.py
add 
```py
from .models import Article
admin.site.register(Article)

```
- Create superuser run `python manage.py createsuperuser`

- use superuser to create some article in django admin