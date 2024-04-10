# Django Template Project

# Overview
This project encapsulates implementations of several Django 
features, so that the entire project can be duplicated for 
new backends. In addition, it provides a playground for
learning.

# Common Commands
## Starting the Test Server
Activate the [python virtual environment first](#activating-the-virtual-environment),
then use Django's `manage.py` to start the server.

```bash
python manage.py runserver
```

## Activating the Virtual Environment
```bash
source venv/bin/activate
```
## Deactivating the Virtual Environment
```bash
deactivate
```

# Docker
This project is setup to utilize [Docker](https://www.docker.com/).

## Creating a requirements.txt from venv
The `venv` module allows running a virtual environment locally
for devs to experiment with dependencies.

To build a Docker container however, we need a `requirements.txt`
that describes the python dependencies that should be installed
inside the container.

You can create one while inside of a virtual environment.

1. Activate venv.
```bash
source venv/bin/activate
```
2. Pipe the output of pip freeze to `requirements.txt`.
```bash
pip3 freeze > requirements.txt
```
3. The `requirements.txt` file will now be utilized by Docker.

## Build
```bash
docker build -f docker/Dockerfile -t django:1.0.0 .
```

# Project Organization
