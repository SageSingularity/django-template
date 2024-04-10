# Settings
This directory establishes environment-specific settings for Django.
* `base.py`: Contains settings common to all environments.
* `development.py`: Contains dev environment specific settings.
* `production.py`: Contains prod environment specific settings.
* `quality_assurance.py`: Contains QA environment specific settings.
* `staging.py`: Contains staging environment specific settings.

## Adding a New Environment
1. Create the `<environment_name>.py` file
2. Add `from .base import *` to import common settings
3. Override settings pertinent to your environment

## Starting Django with a Specific Environment
```bash
python manage.py runserver --settings=django_template.settings.<environment_name>
```
For example:
```bash
python manage.py runserver --settings=django_template.settings.development
```