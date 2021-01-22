# AzureGithub - REST framework tutorial

This is my fork of the example code from the [Django REST Tramework tutorial][tut] code
with explanation of how to deploy with Azure for part of [Accelerate web development with Azure and GitHub](https://aka.ms/azurewebinar-azure-and-github) webinar demos.

[tut]: http://www.django-rest-framework.org/tutorial/1-serialization

### Testing with your local environment

1. [Recommended] Use your Python virtual environment with your preferred IDE such as [Visual Studio Code](https://code.visualstudio.com/) (with [Python extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python) is so great!). On command line, for example,
```
  $ python -m venv my_venv
  $ cd rest-framework-tutorial-with-azure
  $ code .
```
2. Satisfy Python library requirements by referring to [requirements.txt](./requirements.txt). Using __[pip](https://pypi.org/project/pip/)__ would be great like:
```
  $ pip install -r requirements.txt
```
3. You can test by running `manage.py`. Here are sample commands to test locally. Also, [restore.sh](./restore.sh) loads sample fixtures for `users` and `snippets`.
```
  # Run a local server with 8080 port number 
  $ python manage.py runserver 8080

  # Create an initial migration for our snippet model, and sync the database for the first time.
  $ python manage.py makemigrations snippets
  $ python manage.py migrate
```

### Deploying to Azure

This for mainly shows the first deployment method but there are other ways for web applications with Azure:

#### 1. as App Services

The current source code uses `sqlite` with local test support. It can be easily deployed on VSCode as a Web App. After installing [Azure App Service extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice), login on Azure and create your new app.

#### 2. using application settings with PostgreSQL and Azure Storage

[carltongibson's fork - *`azure/2-appservice`* branch](https://github.com/carltongibson/rest-framework-tutorial/commits/azure/2-appservice) shows how to integrate with [Azure Database for PostgreSQL](https://azure.microsoft.com/en-us/services/postgresql/) as database backend, and [Azure Storage](https://azure.microsoft.com/en-us/services/storage/) to store and load static web files. Also, see how environment and application settings are being managed through local environment variables and simple Python scripts.

#### 3. as serverless (Azure Functions)

See commits on [carltongibson's fork - *`azure/4-functions`* branch](https://github.com/carltongibson/rest-framework-tutorial/commits/azure/4-functions) to figure how to easily migrate from App Services to [Azure Functions](https://azure.microsoft.com/en-us/services/functions/) for serverless web applications.

### Related resources

- (Azure Webinar) [Accelerate web development with Azure and GitHub](https://aka.ms/azurewebinar-azure-and-github) by Sudhir and Ian
- (Azure Friday) Python on Azure - Part [1](https://channel9.msdn.com/shows/Azure-Friday/Python-on-Azure-Part-1-Building-Django-apps-with-Visual-Studio-Code?ocid=AID754288&wt.mc_id=CFID0237), [2](https://channel9.msdn.com/shows/Azure-Friday/Python-on-Azure-Part-2-Deploying-Django-services-to-Azure-Web-Apps?ocid=AID754288&wt.mc_id=CFID0238), [3](https://channel9.msdn.com/shows/Azure-Friday/Python-on-Azure-Part-3-CICD-with-Azure-Pipelines?ocid=AID754288&wt.mc_id=CFID0239), and [4](https://channel9.msdn.com/shows/Azure-Friday/Python-on-Azure-Part-4-Running-serverless-Django-apps-with-Functions?ocid=AID754288&wt.mc_id=CFID0240)
- [Visual Studio Code - snippets for use with Django REST Framework](https://gist.github.com/carltongibson/6d2870c7958dafe5002686454605d8b0)
