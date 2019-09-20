# Deploy Django app to Azure App Service on Linux using Visual Studio Code

This django app is created following the [official django tutorial](https://docs.djangoproject.com/en/2.2/intro/tutorial01/). Added a welcome app to serve the website homepage.

## Prerequisites

1. You need an Azure subscription to complete the tutorial. You can create a free account to start with: https://azure.microsoft.com/en-us/free/.  

1. This web app requires a MySQL Server (`django.db.backends.mysql`) as the backend, you can also use PostgreSQL server as the backend. You can easily create a Azure Database for MySQL using Azure portal https://ms.portal.azure.com/#create/Microsoft.MySQLServer.

1. This tutorial uses Visual Studio Code as code editor and deployment too. You can download VSCode for free from https://code.visualstudio.com/download. 

1. Follow the [getting-started instructions](https://code.visualstudio.com/tutorials/app-service-extension/getting-started) to install VSCode App Service Extension.

### Prep the code

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

### Update database connect string

Please update the [settings.py](/mydjangoproject/settings.py) file to include your own database connection string.

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

### Deploy the django app to Linux App Service

Follow the [instructions](https://code.visualstudio.com/tutorials/app-service-extension/deploy-app) to create a new web app and deploy the django app to Linux App Service.
