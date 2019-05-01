## Deploy django app to Azure App Service on Linux using Visual Studio Code

This django app is created following the [official django tutorial](https://docs.djangoproject.com/en/2.2/intro/tutorial01/). Added a welcome app to serve the website homepage.

### Prerequisites
1. You would need an Azure subscription to complete the tutorial. You can create a free account to start with: https://azure.microsoft.com/en-us/free/.  
2. This web app requires a MySQL Server (django.db.backends.mysql) as the backend, you can also use PostgreSQL server as the backend. You can easily create a Azure Database for MySQL using Azure portal https://ms.portal.azure.com/#create/Microsoft.MySQLServer.   
3. This tutorial uses Visual Studio Code as code editor and deployment too. You can download VSCode for free from https://code.visualstudio.com/download. 
4. Follow the [getting-started instructions](https://code.visualstudio.com/tutorials/app-service-extension/getting-started) to install VSCode App Service Extension. 

### Prep the code
Get the source code onto your dev machine:
$ git clone https://github.com/yiliaomsft/pycon19-django.git 

Load the local source code repo into VSCode:
$ cd pycon19-django
$ code .

### Update database connect string
Please update the settings.py file to include your own [database connection string](https://github.com/yiliaomsft/pycon19-django/blob/master/mydjangoproject/settings.py#L79).
~~~
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': '<database name>',
        'USER': '<database user name>',
        'PASSWORD': 'database password',
        'HOST': 'database host',
     }
}
~~~
### Deploy the django app to Linux App Service
Follow the [instructions](https://code.visualstudio.com/tutorials/app-service-extension/deploy-app) to create a new web app and deploy the django app to Linux App Service.
