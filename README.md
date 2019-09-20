# Deploy Django app to Azure App Service on Linux using GitHub Actions

This app is based off the [official django tutorial](https://docs.djangoproject.com/en/2.2/intro/tutorial01/). Using GitHub Actions, we can deploy this app directly to App Service after changes are pushed to the repo.

## Prerequisites

1. You need an Azure subscription to complete the tutorial. You can create a free account to start with: https://azure.microsoft.com/en-us/free/.  

1. You need to create a Python 3.7 Linux Web App.

1. This web app requires a MySQL Server (`django.db.backends.mysql`) as the backend, you can also use PostgreSQL server as the backend. You can easily create a Azure Database for MySQL using Azure portal https://ms.portal.azure.com/#create/Microsoft.MySQLServer.

## Prep the code

1. Get the source code onto your dev machine:

    ```shell
    git clone https://github.com/yiliaomsft/pycon19-django.git 
    ```

1. Load the local source code repo into VSCode:

    ```shell
    cd pycon19-django
    code
    ```

1. Create a virtual environment

    ```shell
    # Linux/MacOS:
    python3 -m venv venv

    # Windows:
    py -m venv venv
    ```

1. Install modules

    ```shell
    pip3 install -r requirements.txt
    ```

1. Start the virtual environment

    ```shell
    # Linux/MacOS
    source env/bin/activate

    # Windows
    .\venv\Scripts\activate
    ```

1. Start the app locally

    ```shell
    py manage.py runserver
    ```

## Update database connection strings

The app currently uses a local SQLite database for local dev and test. You can deploy it with this, or wire it up to a proper MySQL database by editing [settings.py](/mydjangoproject/settings.py) to include your own database connection strings.

```python
DATABASES = {
    'default': {
            'ENGINE': 'django.db.backends.mysql',
            'NAME': '<database name>',
            'USER': '<database user name>',
            'PASSWORD': 'database password',
            'HOST': 'database host',
    }
}
```

## Deploy the django app to Linux App Service

Finally, get your Publish Profile of your webapp from the Azure Portal and add it as a secret in the GitHub web UI. The secret should be named "PUBLISH_PROFILE", to match the string in the workflow YAML.
