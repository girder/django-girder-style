# django-girder-style
[![PyPI](https://img.shields.io/pypi/v/django-girder-style)](https://pypi.org/project/django-girder-style/)

## Develop with Docker

Due to the dependency on npm and Python2, Docker development is the only supported
configuration.

### Initial Setup
1. Run `docker-compose run --rm django ./manage.py migrate`
2. Run `docker-compose run --rm django ./manage.py createsuperuser`
   and follow the prompts to create your own user

### Run Application
1. Run `docker-compose up`
2. Access the site, starting at http://localhost:8000/
   * Outgoing emails are sent to the console 
3. The Django admin interface is still available at http://localhost:8000/admin/
3. When finished, use `Ctrl+C`

### Install Javascript packages
In the event that Javascript packages need to be install, this can be done via Docker Compose:
1. Run: `docker-compose run --rm tailwind yarn add -D package-name`,
   substituting `package-name` as appropriate.

This can also be done natively by running Yarn commands from the `tailwind/` directory, but be sure
to re-build Docker afterwards (via Application Maintenance below).

### Application Maintenance
Occasionally, new package dependencies or schema changes will necessitate
maintenance. To non-destructively update your development stack at any time:
1. Run `docker-compose build --pull --no-cache`
2. Run `docker-compose run --rm django ./manage.py migrate`
