# Deploy Django app to Azure App Service on Linux using GitHub Actions

This app is based off the [official django tutorial](https://docs.djangoproject.com/en/2.2/intro/tutorial01/). Using GitHub Actions, we can deploy this app directly to App Service after changes are pushed to the repo.

## Prerequisites

1. You need an Azure subscription to complete the tutorial. You can create a free account to start with: https://azure.microsoft.com/en-us/free/.  

1. You need to create a Python 3.7 Linux Web App.

1. This web app requires a MySQL Server (`django.db.backends.mysql`) as the backend. You can easily create a Azure Database for MySQL using Azure portal https://ms.portal.azure.com/#create/Microsoft.MySQLServer.

## Prep the code

1. Get the source code onto your dev machine:

    ```shell
    git clone https://github.com/JasonFreeberg/Python-GitHub-Action.git
    ```

2. Load the local source code repo into VSCode:

    ```shell
    cd Python-GitHub-Action
    code .
    ```

3. Create a virtual environment

    ```shell
    # Linux/MacOS:
    python3 -m venv venv

    # Windows:
    py -m venv venv
    ```

    VSCode will ask *"We noticed a new virtual environment has been created. Do you want to select it for the workspace folder?"* Accept this prompt for better code completion.

4. Start the virtual environment

    ```shell
    # Linux/MacOS
    source env/bin/activate

    # Windows
    .\venv\Scripts\activate
    ```

5. Install modules

    ```shell
    pip install -r requirements.txt
    ```

6. Set up SQLite database

    ```shell
    python manage.py makemigrations
    python manage.py migrate
    ```

7. Start the app locally

    ```shell
    python manage.py runserver
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
