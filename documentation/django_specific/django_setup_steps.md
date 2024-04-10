# Django Steps
* Create the Django Project 
* Create the Django Apps, such as `Users`
* Setup separate environments in a `settings` directory such as `base` (imported by the rest), `prod`, `dev`, `qa`, `staging`, etc.
* Ensure the `DJANGO_SETTINGS_MODULE` is set to the correct environment as needed
* Setup `models` and `views` directories in Django Apps 
* Add `__init__.py` to `models` and `views`, and import: `from users import *`
* Ensure `AUTH_USER_MODEL` in the `settings` directory is set to the custom user model