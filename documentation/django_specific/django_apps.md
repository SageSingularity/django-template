# Django Apps
Django apps are modules within Django that help maintain separation
of concerns. Not to be confused with the overall Django project.

Each one has:
* [urls.py](https://docs.djangoproject.com/en/5.0/topics/http/urls/): Configuring routing.

## Create Django App
```bash
python manage.py startapp <app_name>
```

## Register the App
Add your app to the `INSTALLED_APPS` list in the appropriate environment.
* All environments: `base.py`
* Production only: `production.py`
* Development only: `development.py`
* Staging only: `staging.py`
* Quality Assurance only: `quality_assurance.py`

```python
INSTALLED_APPS = [
    ...
    '<app_name>',
]
```

## Define Models & Views
Start defining your models in `models.py` and views in `views.py` within your app directory.

As complexity increases, you can separate Models & Views into separate files.

## Migrate the Database
After defining your models, prepare the database migrations:
```python
python manage.py makemigrations <app_name>
```
Apply the migrations:
```python
python manage.py migrate
```

## Create URLs
In your app directory, create a `urls.py` file to define URLs for your app.

Don’t forget to include your app’s URLs in the project’s `urls.py` file using the `include()` function.

## Best Practices
* `Single Responsibility Principle`: Each app should have a single responsibility and focus on a specific aspect of your project. For instance, an app for handling user authentication should not also manage blog posts.
* `Reusable Apps`: Design your apps to be reusable whenever possible. Ideally, you should be able to plug an app into another project with minimal configuration.
* `Naming Conventions`: Use clear and descriptive names for your apps. If an app is designed to manage blog posts, a name like blog is more appropriate than something generic like app1.
* `Modularize Your Project`: Keep your project organized by dividing it into smaller apps that represent different functionalities or features of your application.
* `Shared Functionality`: For functionality that is used across different apps, consider creating a common app that houses shared models, utilities, and templates.
* `Avoid Tight Coupling`: Apps should be as independent from each other as possible. If you find that changes in one app frequently require changes in another, it might be a sign that they are too tightly coupled.
* `App-specific Static and Template Directories`: Keep static files and templates within their respective app directories when they are specific to that app. Use the project-level templates and static directories for shared resources.